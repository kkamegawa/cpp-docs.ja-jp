---
title: コンパイラエラー C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: ca378c3e0ce88b454cb89fc08470a277a7be6f47
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755227"
---
# <a name="compiler-error-c2694"></a>コンパイラエラー C2694

' override ': オーバーライドする仮想関数は、基底クラスの仮想メンバー関数 ' base ' よりも制限の緩い例外指定を含んでいます

仮想関数がオーバーライドされましたが、 [/za](../../build/reference/za-ze-disable-language-extensions.md)では、オーバーライドする関数には制限の緩い[例外指定](../../cpp/exception-specifications-throw-cpp.md)がありました。

次の例では、C2694 が生成されます。

```cpp
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```
