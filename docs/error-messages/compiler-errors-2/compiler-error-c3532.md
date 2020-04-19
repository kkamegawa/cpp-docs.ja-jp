---
title: コンパイラ エラー C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761934"
---
# <a name="compiler-error-c3532"></a>コンパイラ エラー C3532

' type ': ' auto ' の使用法が正しくありません

指定された型は、`auto` キーワードを使用して宣言することはできません。 たとえば、`auto` キーワードを使用して、配列またはメソッドの戻り値の型を宣言することはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 初期化式によって有効な型が生成されていることを確認します。

1. 配列またはメソッドの戻り値の型が宣言されていないことを確認してください。

## <a name="example"></a>使用例

次の例では、`auto` キーワードがメソッドの戻り値の型を宣言できないため、C3532 が生成されます。

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>使用例

次の例では、`auto` キーワードで配列を宣言できないため、C3532 が生成されます。

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
