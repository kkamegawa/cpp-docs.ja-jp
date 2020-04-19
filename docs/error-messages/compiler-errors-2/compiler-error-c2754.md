---
title: コンパイラエラー C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: 179cbaf65bf6440a13da6b35c073af981b074c71
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759569"
---
# <a name="compiler-error-c2754"></a>コンパイラエラー C2754

' 特殊化 ': 部分的特殊化は、依存しない非型テンプレートパラメーターを持つことはできません

依存しない非型テンプレートパラメーターを持つテンプレートクラスを部分的に特殊化しようとしました。 これは許可されていません。

次の例では、C2754 が生成されます。

```cpp
// C2754.cpp
// compile with: /c

template<class T, T t>
struct A {};

template<class T, int N>
struct B {};

template<class T> struct A<T,5> {};   // C2754
template<> struct A<int,5> {};   // OK
template<class T> struct B<T,5> {};   // OK
```
