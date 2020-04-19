---
title: コンパイラ エラー C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761531"
---
# <a name="compiler-error-c3539"></a>コンパイラ エラー C3539

' type ': テンプレート引数に ' auto ' を含む型を指定することはできません

指定されたテンプレート引数の型に `auto` キーワードの使用を含めることはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. `auto` キーワードを使用して、テンプレート引数を指定しないでください。

## <a name="example"></a>使用例

次の例では、C3539 が生成されます。

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
