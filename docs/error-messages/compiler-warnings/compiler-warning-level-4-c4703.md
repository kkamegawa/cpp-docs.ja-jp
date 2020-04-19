---
title: コンパイラの警告 (レベル 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 5033490550f318cab65f984cab81b08102641c9d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518362"
---
# <a name="compiler-warning-level-4-c4703"></a>コンパイラの警告 (レベル 4) C4703

初期化されていない可能性のあるローカルポインター変数 ' name ' が使用されています

ローカルポインターの変数*名*が、値を割り当てずに使用されている可能性があります。 これにより、予測できない結果が生じる可能性があります。

## <a name="example"></a>使用例

次のコードでは、C4701 と C4703 が生成されます。

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

この警告を解決するには、次の例に示すように変数を初期化します。

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

int main()
{
    func(9);
}
```

## <a name="see-also"></a>関連項目

[コンパイラの警告 (レベル 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[警告、/sdl、および初期化されていない変数の検出の向上](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
