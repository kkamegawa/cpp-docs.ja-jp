---
title: コンパイラ エラー C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740482"
---
# <a name="compiler-error-c3537"></a>コンパイラ エラー C3537

' type ': ' auto ' を含む型にキャストすることはできません

型には `auto` キーワードが含まれており、既定の[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)コンパイラオプションが有効になっているため、指定された型に変数をキャストすることはできません。

## <a name="example"></a>使用例

次のコードでは、変数が `auto` キーワードを含む型にキャストされるため、C3537 が生成されます。

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
