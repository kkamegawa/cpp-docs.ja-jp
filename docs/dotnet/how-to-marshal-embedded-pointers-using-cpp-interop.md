---
title: '方法: C++ Interop を使用して埋め込みポインターをマーシャ リングします。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: c6d622060aaf700b6ea1a3bfe797ab3190eee797
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345738"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>方法: C++ Interop を使用して埋め込みポインターをマーシャ リングします。

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)#pragma ディレクティブを実装するマネージ コードと同じファイル内の関数をアンマネージが個別のファイルに定義されている場合、これらの関数が同じ方法で相互運用。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要はありません[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。

## <a name="example"></a>例

次の例では、マネージ関数からポインターを含む構造体を受け取るアンマネージ関数を呼び出す方法を示します。 マネージ関数は、構造体のインスタンスを作成し、新しいキーワードを使用して埋め込みポインターを初期化します (の代わりに、 [ref new、gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)キーワード)。 ネイティブ ヒープにメモリを割り当ててこのため、ガベージ コレクションを抑制する配列を固定する必要はありません。 ただし、メモリ リークを回避するために、メモリを明示的に削除する必要があります。

```
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
