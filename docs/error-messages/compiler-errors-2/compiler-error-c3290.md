---
title: コンパイラ エラー C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: a7a73c13c28923761674294d8d6e601b95ffad96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760154"
---
# <a name="compiler-error-c3290"></a>コンパイラ エラー C3290

'type': trivial プロパティに参照型を含めることはできません。

プロパティが正しく宣言されませんでした。 trivial プロパティを宣言すると、コンパイラは、プロパティが更新する変数を作成します。クラスに追跡参照変数を指定することはできません。

詳細については、「[プロパティ](../../extensions/property-cpp-component-extensions.md)And [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C3290 が生成されます。

```cpp
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```
