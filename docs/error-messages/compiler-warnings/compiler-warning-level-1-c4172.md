---
title: コンパイラの警告 (レベル 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7d53972dbcb2e3ab6a95b0b874cc6bb98cd66840
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624827"
---
# <a name="compiler-warning-level-1-c4172"></a>コンパイラの警告 (レベル 1) C4172

ローカル変数または一時アドレスを返す

関数は、ローカル変数または一時オブジェクトのアドレスを返します。 ローカル変数と一時オブジェクトは、関数がを返したときに破棄されるので、返されたアドレスは無効です。

関数を再設計して、ローカルオブジェクトのアドレスが返されないようにします。

次の例では、C4172 が生成されます。

```cpp
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```