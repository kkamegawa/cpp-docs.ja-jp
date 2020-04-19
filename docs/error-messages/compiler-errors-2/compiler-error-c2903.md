---
title: コンパイラ エラー C2903
ms.date: 11/04/2016
f1_keywords:
- C2903
helpviewer_keywords:
- C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
ms.openlocfilehash: df097cf38fea47702b639b44fd2f2ac3341df2ba
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735906"
---
# <a name="compiler-error-c2903"></a>コンパイラ エラー C2903

'identifier' : シンボルがクラス テンプレートでも関数テンプレートでもありません

コードで、テンプレートではないものを明示的にインスタンス化しようとしています。

次の例では C2903 が生成されます。

```cpp
// C2903.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template Y y;   // C2903
   N::X<N::Y> y;   // OK
}
```

C2903 は、ジェネリックを使用しているときにも発生します。

```cpp
// C2903b.cpp
// compile with: /clr /c
namespace N {
   class Y {};
   generic<class T> ref class Z {};
}

void f() {
   N::generic Y y;   // C2903
   N:: generic Z<int>^ z;   // OK
}
```
