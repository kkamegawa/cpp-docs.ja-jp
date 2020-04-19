---
title: コンパイラエラー C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: ea158d8dada013f6b90d0fbe1e7502665c1c24da
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757723"
---
# <a name="compiler-error-c2079"></a>コンパイラエラー C2079

' identifier ' は未定義のクラス/構造体/共用体 ' name ' を使用します

指定された識別子は、未定義のクラス、構造体、または共用体です。

このエラーは、匿名共用体を初期化することによって発生することがあります。

次の例では、C2079 が生成されます。

```cpp
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

解決方法:

```cpp
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 は、前方宣言がスコープ内にのみ存在する型のスタック上でオブジェクトを宣言しようとした場合にも発生する可能性があります。

```cpp
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

解決方法:

```cpp
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```
