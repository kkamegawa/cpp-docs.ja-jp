---
title: コンパイラ エラー C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758906"
---
# <a name="compiler-error-c2247"></a>コンパイラ エラー C2247

' class ' は ' class ' から継承するために ' 指定子 ' を使用するため、' identifier ' にアクセスできません

`identifier` は、private または protected アクセスで宣言されたクラスから継承されます。

次の例では、C2247 が生成されます。

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果として生成されることもあります。プロテクトメンバーによるアクセス制御。 プロテクトメンバー (n) は、(n) がメンバーであるクラス (A) から継承するクラス (B) のメンバー関数を介してのみアクセスできます。

Visual Studio .NET 2003 と visual Studio .NET の両方のバージョンの Visual C++studio で有効なコードの場合は、メンバーを型のフレンドとして宣言します。 パブリック継承を使用することもできます。

```cpp
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

C2247 は、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果として生成することもできます。プライベート基本クラスにアクセスできなくなりました。 型 (B) のプライベート基本クラスであるクラス (A) は、B を基底クラスとして使用する型 (C) にアクセスできないようにする必要があります。

Visual Studio .NET 2003 と visual Studio .NET の両方のバージョンの Visual C++studio で有効なコードについては、scope 演算子を使用します。

```cpp
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```
