---
title: コンパイラ エラー C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 94f35f9f3bf64e09087f28a11a4fb9802d9d3c0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761518"
---
# <a name="compiler-error-c3540"></a>コンパイラ エラー C3540

' type ': sizeof を ' auto ' を含む型に適用することはできません

`auto` 指定子が含まれているため、指定された型に[sizeof](../../cpp/sizeof-operator.md)演算子を適用することはできません。

## <a name="example"></a>使用例

次の例では、C3540 が生成されます。

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (変数の型の推測)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 演算子](../../cpp/sizeof-operator.md)
