---
title: コンパイラ エラー C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: 38e2fd090f3a2b2222658c5fd491c84dd70fd5ea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756423"
---
# <a name="compiler-error-c2139"></a>コンパイラ エラー C2139

' type ': 未定義のクラスは、コンパイラの組み込み型の特徴である ' 特徴 ' の引数として使用することはできません

型の特徴に無効な引数が渡されました。

詳細については、「[型の特徴のコンパイラ サポート](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2139 が生成されます。

```cpp
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```
