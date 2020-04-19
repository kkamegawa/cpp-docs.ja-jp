---
title: コンパイラの警告 (レベル 4) C4701
ms.date: 11/04/2016
f1_keywords:
- C4701
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
ms.openlocfilehash: b83ad810da06de1f9d640477f73d4393c932054a
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518388"
---
# <a name="compiler-warning-level-4-c4701"></a>コンパイラの警告 (レベル 4) C4701

初期化されていない可能性があるローカル変数 ' name ' を使用します

ローカル変数*名*は、値を割り当てずに使用されている可能性があります。 これにより、予測できない結果が生じる可能性があります。

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

[コンパイラの警告 (レベル 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)<br/>
[警告、/sdl、および初期化されていない変数の検出の向上](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
