---
title: __sptr、__uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: 957f744ca6c5a7be807c1dc68fcd2b602b72300e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330960"
---
# <a name="sptr-uptr"></a>__sptr、__uptr

**Microsoft 固有の仕様**

使用して、 **_ _sptr**または **_ _uptr**コンパイラが 32 ビット ポインターを 64 ビット ポインターに変換する方法を指定する 32 ビット ポインターの宣言に修飾子。 たとえば、32 ビット ポインターが 64 ビット ポインター変数に割り当てられたときや、64 ビット プラットフォーム上で 32 ビット ポインターが逆参照される場合などに変換が必要になります。

64 ビット プラットフォームをサポートする Microsoft のドキュメントでは、32 ビット ポインターの最上位ビットを符号ビットと呼んでいる場合があります。 既定では、コンパイラは符号拡張を使用して 32 ビット ポインターを 64 ビット ポインターに変換します。 つまり、64 ビット ポインターの下位 32 ビットに 32 ビット ポインターの値が設定され、上位 32 ビットに 32 ビット ポインターの符号ビットの値が設定されます。 符号ビットが 0 の場合はこの変換で正しい結果が得られますが、符号ビットが 1 の場合は正しい結果が得られません。 たとえば、32 ビット アドレス 0x7FFFFFFF はこれと同等の 64 ビットアドレス 0x000000007FFFFFFF になりますが、32 ビット アドレス 0x80000000 は誤って 0xFFFFFFFF80000000 に変換されます。

**_ _Sptr**、符号付きポインター、または修飾子はポインター変換が 32 ビット ポインターの符号ビットに 64 ビット ポインターの最上位ビットを設定することを指定します。 **_ _Uptr**、または符号なしポインターは、修飾子を指定の変換に最上位ビットが 0 に設定されています。 次の宣言に示す、 **_ _sptr**と **_ _uptr**修飾されていない 2 つのポインターと共に使用する修飾子で修飾を 2 つのポインター、 [_ _ptr32](../cpp/ptr32-ptr64.md)型、および関数パラメーター。

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

使用して、 **_ _sptr**と **_ _uptr**ポインター宣言での修飾子。 位置で、修飾子を使用して、[ポインター型修飾子](../c-language/pointer-declarations.md)、つまり、修飾子は、アスタリスクが従う必要があります。 これらの修飾子を使用することはできません[メンバーへのポインター](../cpp/pointers-to-members.md)します。 これらの修飾子は、ポインター以外の宣言には影響を与えません。

以前のバージョンとの互換性のため **_sptr**と **_uptr**のシノニムで **_ _sptr**と **_ _uptr**コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../build/reference/za-ze-disable-language-extensions.md)を指定します。

## <a name="example"></a>例

次の例を使用して、32 ビット ポインターの宣言、 **_ _sptr**と **_ _uptr**修飾子、各 32 ビット ポインターを 64 ビット ポインター変数に代入し、各 64 - の 16 進数の値が表示されますビットのポインター。 この例はネイティブの 64 ビット コンパイラでコンパイルされ、64 ビット プラットフォームで実行されます。

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)