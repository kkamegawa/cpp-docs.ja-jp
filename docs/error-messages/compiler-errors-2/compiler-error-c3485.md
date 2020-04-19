---
title: コンパイラ エラー C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0eacb6ce6426674d23fc78596ead3730f46ae370
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743043"
---
# <a name="compiler-error-c3485"></a>コンパイラ エラー C3485

ラムダ定義に cv 修飾子は使用できません

ラムダ式の定義の一部として `const` 修飾子または `volatile` 修飾子を使用することはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- ラムダ式の定義から `const` 修飾子または `volatile` 修飾子を削除します。

## <a name="example"></a>使用例

次の例では、ラムダ式の定義の一部として `const` 修飾子を使用しているため、C3485 が生成されます。

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
