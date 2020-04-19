---
title: コンパイラ エラー C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760877"
---
# <a name="compiler-error-c2893"></a>コンパイラ エラー C2893

関数テンプレート ' template name ' を特殊化できませんでした

コンパイラは関数テンプレートを特殊化できませんでした。 このエラーには多くの原因が考えられます。

一般に、C2893 エラーを解決するには、関数のシグネチャを確認し、すべての型をインスタンス化できるようにします。

## <a name="example"></a>使用例

`f`のテンプレートパラメーター `T` が `std::map<int,int>`されると推測されますが、`std::map<int,int>` にはメンバー `data_type` がありません (`T::data_type` を使用してインスタンス化することはできません)。 次の例では、C2893 が生成されます。

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
