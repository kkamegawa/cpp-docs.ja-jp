---
title: コンパイラ エラー C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 1308ff91bcebabc5495b015321494f3457cf2d1e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761505"
---
# <a name="compiler-error-c3541"></a>コンパイラ エラー C3541

' type ': typeid を ' auto ' を含む型に適用することはできません

`auto` 指定子を含んでいるため、 [typeid](../../extensions/typeid-cpp-component-extensions.md)演算子を指定された型に適用できません。

## <a name="example"></a>使用例

次の例では、C3541 が生成されます。

```cpp
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (変数の型の推測)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)
