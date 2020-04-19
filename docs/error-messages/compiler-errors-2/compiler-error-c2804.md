---
title: コンパイラ エラー C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: 62af8cca5131a5cb21df45f09c55ee5beb3fc718
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760648"
---
# <a name="compiler-error-c2804"></a>コンパイラ エラー C2804

二項 'operator 演算子' のパラメーターが多すぎます。

オーバーロードされた二項演算子のメンバー関数が、複数のパラメーターを指定して宣言されています。 型が演算子の外側の型になっている二項演算子メンバー関数の 1 つ目のオペランド パラメーターは、暗黙的に指定されます。

## <a name="example"></a>使用例

次の例では、C2804 を生成し、その修正方法を示しています。

```cpp
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

## <a name="example"></a>使用例

次の例では、C2804 を生成し、その修正方法を示しています。

```cpp
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```
