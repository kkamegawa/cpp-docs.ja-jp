---
title: '方法: C++ Interop を使用して Unicode 文字列をマーシャ リング'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 37b56834e000cff686557730252f3d425f642772
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400553"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>方法: C++ Interop を使用して Unicode 文字列をマーシャ リング

このトピックでは、Visual C の相互運用性の 1 つのファセットを示します。 詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)#pragma ディレクティブを実装するマネージ コードと同じファイル内の関数をアンマネージが個別のファイルに定義されている場合、これらの関数が同じ方法で相互運用。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要はありません[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。

このトピックでは、Unicode 文字列をする方法を示しますマネージからアンマネージ関数では、その逆に渡されます。 他の文字列型との相互運用を次のトピックを参照してください。

- [方法: C++ Interop を使用して ANSI 文字列をマーシャリングする](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [方法: C++ Interop を使用して COM 文字列をマーシャリングする](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>例

Unicode 文字列をマネージからアンマネージ関数に渡す、(Vcclr.h で宣言) PtrToStringChars 関数を使用するマネージ文字列が格納されているメモリにアクセスします。 このアドレスはネイティブ関数に渡される、ために、メモリを固定することが重要です[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)を文字列データの再配置されることを防ぐためにガベージ コレクション サイクルを実行中に、アンマネージ関数を実行します。

```
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>例

次の例では、アンマネージ関数によって呼び出されるマネージ関数で Unicode 文字列にアクセスするために必要なデータのマーシャ リングを示します。 ネイティブの Unicode 文字列を受け取ると、マネージ関数を使用して管理対象の文字列に変換、<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>メソッド。

```
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
