---
title: コンパイラ エラー C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756787"
---
# <a name="compiler-error-c2553"></a>コンパイラ エラー C2553

' base_function ': オーバーライドする仮想関数の戻り値の型が ' override_function ' と異なります

派生クラスの関数が基底クラスの仮想関数をオーバーライドしようとしましたが、派生クラスの関数に基底クラス関数と同じ戻り値の型がありませんでした。  オーバーライド関数のシグネチャは、オーバーライドされる関数のシグネチャと一致する必要があります。

次の例では、C2553 が生成されます。

```cpp
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```
