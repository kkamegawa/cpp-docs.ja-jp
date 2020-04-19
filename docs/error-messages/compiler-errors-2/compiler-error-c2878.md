---
title: コンパイラ エラー C2878
ms.date: 11/04/2016
f1_keywords:
- C2878
helpviewer_keywords:
- C2878
ms.assetid: 83ee3de1-f554-49e8-a840-1f550cee7f69
ms.openlocfilehash: faf50edfcddc64a75062672175ab7fbad63081c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736310"
---
# <a name="compiler-error-c2878"></a>コンパイラ エラー C2878

' name ': この名前の名前空間またはクラスは存在しません

定義されていない名前空間またはクラスを参照しました。

次の例では、C2878 が生成されます。

```cpp
// C2878.cpp
// compile with: /c
namespace A {}
namespace B = C;   // C2878 namespace C doesn't exist
namespace B = A;
```
