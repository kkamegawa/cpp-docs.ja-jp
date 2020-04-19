---
title: コンパイラ エラー C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: a8fe0802a7529551fce1c0b7242c867db52d8842
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756761"
---
# <a name="compiler-error-c3072"></a>コンパイラ エラー C3072

演算子 ' operator ' を ref クラスのインスタンスに適用することはできません

単項 '`operator` ' 演算子を使用して ref クラスのインスタンスをハンドル型に変換します

CLR 型には、ネイティブ (または標準) 演算子ではなく、CLR 演算子が必要です。  詳細については、「[参照演算子の追跡](../../extensions/tracking-reference-operator-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3072 が生成されます。

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
