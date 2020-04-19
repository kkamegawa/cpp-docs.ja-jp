---
title: コンパイラ エラー C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: f5a62b1c12b94735d0383697bf7a92d12d64b21f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757801"
---
# <a name="compiler-error-c2243"></a>コンパイラ エラー C2243

'type1' から 'type2' の 'conversion type' 変換は存在しますが、アクセスできません。

アクセス保護 (`protected` または `private`) によって、派生クラスへのポインターから基底クラスへのポインターに変換できませんでした。

次の例では C2243 が生成されます。

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

`protected` または `private` アクセスの基底クラスは、派生クラスのクライアントからはアクセスできません。 これらのレベルのアクセス制御は、基底クラスが、クライアントに表示される必要がない実装の詳細であることを示すために使用されます。 派生クラスのクライアントが派生クラスのポインターから基底クラスへのポインターへの暗黙的な変換にアクセスする必要がある場合は、パブリック派生を使用します。
