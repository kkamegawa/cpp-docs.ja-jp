---
title: コンパイラ エラー C2206
ms.date: 11/04/2016
f1_keywords:
- C2206
helpviewer_keywords:
- C2206
ms.assetid: d7fba68b-aa28-4885-a9a0-27107358f066
ms.openlocfilehash: dbdc86330423ff83be1f188a67684a41cc55aac8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758945"
---
# <a name="compiler-error-c2206"></a>コンパイラ エラー C2206

'function': typedef は関数の型を定義するためには使えません。

関数型を定義するには、 `typedef` を使用します。

次の例では C2206 が生成されます。

```cpp
// C2206.cpp
typedef int functyp();
typedef int MyInt;
functyp func1 {};   // C2206
int main() {
   MyInt i = 0;   // OK
}
```
