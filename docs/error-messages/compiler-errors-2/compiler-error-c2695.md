---
title: コンパイラエラー C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 6d46699a2036c4f45daf3c34802ddb6b44e554ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755214"
---
# <a name="compiler-error-c2695"></a>コンパイラエラー C2695

' function1 ': オーバーライドする仮想関数は、呼び出し規約によってのみ ' function2 ' と異なります

派生クラスの関数のシグネチャは、基底クラスの関数をオーバーライドし、呼び出し規約を変更することはできません。

次の例では、C2695 が生成されます。

```cpp
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```
