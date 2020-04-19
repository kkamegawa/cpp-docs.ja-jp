---
title: __ptr32、__ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: 957e0deba31552777ef5e738afef13d74a640a18
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301328"
---
# <a name="__ptr32-__ptr64"></a>__ptr32、__ptr64

**Microsoft 固有の仕様**

**__ptr32**は32ビットシステムのネイティブポインターを表し、 **__ptr64**は64ビットシステムのネイティブポインターを表します。

次の例は、これらのポインター型のそれぞれを宣言する方法を示します。

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

32ビットシステムでは、 **__ptr64**で宣言されたポインターは、32ビットポインターに切り詰められます。 64ビットシステムでは、 **__ptr32**で宣言されたポインターは、64ビットポインターに強制変換されます。

> [!NOTE]
> **/Clr: pure**を使用してコンパイルする場合、 **__ptr32**または **__ptr64**を使用することはできません。 それ以外の場合は、コンパイラエラー C2472 が生成されます。 **/Clr: pure**および **/clr: safe**コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 ではサポートされていません。

以前のバージョンとの互換性を維持するために、 **_ptr32**と **_ptr64**は **__ptr32**と **__ptr64**のシノニムであり、コンパイラオプション[/za \(言語拡張を無効にする)](../build/reference/za-ze-disable-language-extensions.md)が指定されている場合を除きます。

## <a name="example"></a>使用例

次の例は、 **__ptr32**と **__ptr64**キーワードを使用してポインターを宣言して割り当てる方法を示しています。

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**END Microsoft 固有の仕様**

## <a name="see-also"></a>関連項目

[組み込みの型](../cpp/fundamental-types-cpp.md)