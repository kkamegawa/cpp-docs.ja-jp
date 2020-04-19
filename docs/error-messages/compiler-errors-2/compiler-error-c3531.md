---
title: コンパイラ エラー C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 7da9da2daedc79db619f82848dc864d1cb7bd1f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750092"
---
# <a name="compiler-error-c3531"></a>コンパイラ エラー C3531

' symbol ': 型に ' auto ' を含むシンボルには初期化子を指定しなければなりません

指定された変数に初期化子式がありません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 変数を宣言するときに、等号構文を使用する単純な代入などの初期化子式を指定します。

## <a name="example"></a>使用例

次の例では、変数 `x1`、`y1, y2, y3`、および `z2` が初期化されていないため、C3531 が生成されます。

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
