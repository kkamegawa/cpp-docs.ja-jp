---
title: '方法: C++ Interop を使用してコールバックおよびデリゲートをマーシャ リングします。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: f8088bf90162fd2177599c252b0eee6332d61289
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344952"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>方法: C++ Interop を使用してコールバックおよびデリゲートをマーシャ リングします。

このトピックでは、コールバックのマーシャ リングする方法について説明し、Visual C を使用してマネージ コードとアンマネージ コード間のデリゲート (コールバックの管理対象のバージョン)。

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)しますが、#pragma ディレクティブを実装するマネージし、アンマネージ関数を同じファイルで、関数は、個別のファイルにも定義できます。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要はありません、 [/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。

## <a name="example"></a>例

次の例では、マネージ デリゲートをトリガーするアンマネージ API を構成する方法を示します。 マネージ デリゲートを作成し、相互運用機能のいずれかの<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>デリゲートの基になるエントリ ポイントを取得するために使用します。 このアドレスはマネージ関数として実装されていることを認識していなくても呼び出すアンマネージ関数に渡されます。

注意可能であれば、必ずしもそうとは限りません、ピン留めするには、デリゲートを使用して[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)から再配置したり、ガベージ コレクターによって破棄されるようにします。 ピン留めは、必要に応じて、コレクションをできないようにも再配置を防ぎますを以上に保護を提供しますが、途中のガベージ コレクションからの保護を必要とします。

デリゲートはガベージ コレクションによって再配置されている場合に影響しません、管理されている基本コールバックのため<xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>デリゲートの再配置を許可するが、破棄を防止、デリゲートへの参照を追加するために使用します。 Pin_ptr ではなく GCHandle を使用すると、マネージ ヒープの断片化の可能性が減少します。

```
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example"></a>例

次の例は、前の例に似ていますが、指定された関数ポインターが非管理対象の API によって格納されているため、呼び出すことができます、いつでも任意の長さの時間のガベージ コレクションを中止することを必要とするここで。 次の例のグローバル インスタンスを使用してその結果、<xref:System.Runtime.InteropServices.GCHandle>デリゲートが関数スコープに依存しない、再配置されたをされていることを防ぐためにします。 前述の最初の例は pin_ptr を使用してこれらの例については、必要はありませんが、ここでは、いずれにしてもうまくいきません、pin_ptr のスコープは 1 つの関数に制限されています。

```
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
