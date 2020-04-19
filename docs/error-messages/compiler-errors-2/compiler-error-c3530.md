---
title: コンパイラ エラー C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750144"
---
# <a name="compiler-error-c3530"></a>コンパイラ エラー C3530

' auto ' を他の型指定子と組み合わせることはできません

型指定子は、`auto` キーワードと共に使用されます。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. `auto` キーワードを使用する変数宣言では、型指定子を使用しないでください。

## <a name="example"></a>使用例

次の例では、変数 `x` が `auto` キーワードと型 `int`の両方で宣言されており、この例は **/zc: auto**を使用してコンパイルされているため、C3530 が生成されます。

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
