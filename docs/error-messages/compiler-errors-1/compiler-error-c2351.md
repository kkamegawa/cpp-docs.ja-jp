---
title: コンパイラ エラー C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 6839d0c44efa10ba9507389fea35964fa748d646
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759972"
---
# <a name="compiler-error-c2351"></a>コンパイラ エラー C2351

廃止C++されたコンストラクターの初期化構文

コンストラクターの新しいスタイルの初期化リストでは、基底クラスが唯一の場合でも、各直接基底クラスに明示的に名前を指定する必要があります。

次の例では、C2351 が生成されます。

```cpp
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```
