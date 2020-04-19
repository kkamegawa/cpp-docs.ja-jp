---
title: '方法: C++ Interop を使用して ANSI 文字列をマーシャ リング'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: b73d8ed403ab0bbad7703f66f0d8d4ac23bb7766
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345750"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>方法: C++ Interop を使用して ANSI 文字列をマーシャ リング

このトピックでは、ANSI 文字列をする方法を示しますが、C++ 相互運用の場合、.NET Framework を使用して渡す<xref:System.String>ANSI への変換は、追加の手順は、Unicode 形式で文字列を表します。 その他の文字列型との相互運用を次のトピックを参照してください。

- [方法: C++ Interop を使用して Unicode 文字列をマーシャリングする](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して COM 文字列をマーシャリングする](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)#pragma ディレクティブを実装するマネージ コードと同じファイル内の関数をアンマネージが個別のファイルに定義されている場合、これらの関数が同じ方法で相互運用。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要がないため[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)、それぞれのパフォーマンス特性を保持できます。

## <a name="example"></a>例

例では、マネージからアンマネージ関数を使用して ANSI 文字列を渡す<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>します。 このメソッドは、アンマネージ ヒープにメモリを割り当てます、変換を実行した後は、アドレスが返されます。 つまり、ピン留めは必要ありません (GC ヒープ上のメモリは、アンマネージ関数に渡されてはいない) ためから、IntPtr が返される<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>明示的に解放する必要がありますまたはメモリ リークが発生する結果。

```
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example"></a>例

次の例では、アンマネージ関数によって呼び出されるマネージ関数内の ANSI 文字列にアクセスするために必要なデータのマーシャ リングを示します。 ネイティブの文字列を受け取ると、マネージ関数はそれを直接使用またはを使用して管理対象の文字列に変換する、<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>メソッドを表示します。

```
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
