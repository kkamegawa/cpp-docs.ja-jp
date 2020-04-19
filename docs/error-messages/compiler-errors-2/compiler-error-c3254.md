---
title: コンパイラ エラー C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 6b9ff41fb4f45d9570869ca90e3c6091cc03a58a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754252"
---
# <a name="compiler-error-c3254"></a>コンパイラ エラー C3254

' 明示的なオーバーライド ': クラスに明示的なオーバーライド ' override ' が含まれていますが、関数宣言を含むインターフェイスから派生していません

[明示的](../../cpp/explicit-overrides-cpp.md)にメソッドをオーバーライドする場合、オーバーライドを含むクラスは、オーバーライドする関数を含む型から直接的または間接的に派生させる必要があります。

次の例では、C3254 が生成されます。

```cpp
// C3254.cpp
__interface I
{
   void f();
};

__interface I1 : I
{
};

struct A /* : I1 */
{
   void I1::f()
   {   // C3254, uncomment : I1 to resolve this C3254
   }
};

int main()
{
}
```
