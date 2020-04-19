---
title: コンパイラ エラー C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: 1d0ed5ec717efecb9fbea4a9451836c0471522b6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738714"
---
# <a name="compiler-error-c3203"></a>コンパイラ エラー C3203

'type': 非特殊クラス テンプレートまたはジェネリックは、テンプレートまたはジェネリック引数としてテンプレートまたはジェネリック パラメーター 'param' に使用できません。実際の型を指定してください

無効な引数をクラス テンプレートまたはジェネリックに渡しました。 クラス テンプレートまたはジェネリックには、パラメーターとして型を渡す必要があります。

このエラーは、Visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成される場合があります。非特殊クラステンプレートは、基底クラスリストのテンプレート引数として使用することはできません。 C3203 を解決するには、基底クラス リストでテンプレート パラメーターとしてテンプレート型パラメーターを使用するときに、明示的にテンプレート型パラメーターをテンプレート クラス名に追加します。

```cpp
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

次の例は C3203 を生成し、その修正方法を示しています。

```cpp
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

C3203 は、ジェネリックを使用しているときも発生します。

```cpp
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```
