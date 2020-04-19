---
title: コンパイラ エラー C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: 63063ec98bbc4d42f3237fd42e42b9fdce489892
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745422"
---
# <a name="compiler-error-c2378"></a>コンパイラ エラー C2378

'identifier': 再定義されています。シンボルは typedef でオーバーロードできません

この識別子は `typedef`として定義されました。

次の例では C2378 が生成されます。

```cpp
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```
