---
title: '方法: C++ Interop を使用して COM 文字列をマーシャ リング'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: e86cf0b3e57eda9a0f4fa5fe2337d0c42de5669f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325482"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>方法: C++ Interop を使用して COM 文字列をマーシャ リング

このトピックでは、BSTR (COM プログラミングで推奨される基本的な文字列形式) をする方法を示しますマネージからアンマネージ関数では、その逆に渡されます。 他の文字列型との相互運用を次のトピックを参照してください。

- [方法: C++ Interop を使用して Unicode 文字列をマーシャリングする](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して ANSI 文字列をマーシャリングする](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)#pragma ディレクティブを実装するマネージ コードと同じファイル内の関数をアンマネージが個別のファイルに定義されている場合、これらの関数が同じ方法で相互運用。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要はありません[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。

## <a name="example"></a>例

次の例では、BSTR (COM プログラミングで使用される文字列形式) を渡す方法を示しますマネージ、アンマネージ関数にします。 呼び出し元関数の使用を管理する<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>.NET System.String の内容の BSTR 表現のアドレスを取得します。 使用して、このポインターがピン留め[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)アンマネージ関数の実行中に、物理アドレスがガベージ コレクション サイクル中に変更しないことを確認します。 ガベージ コレクターは移動されるまでメモリから、 [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)がスコープ外になります。

```
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>例

次の例では、BSTR を渡す方法を示しますからアンマネージ、アンマネージ関数にします。 マネージ関数する BSTR として内の文字列を使用するか使用して受信<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>に変換する<xref:System.String>他で使用するためのマネージ関数です。 BSTR を表すメモリが割り当てられるので、アンマネージ ヒープのピン留めの必要はなく、アンマネージ ヒープのガベージ コレクションがないためです。

```
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
