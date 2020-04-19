---
title: コンパイラの警告 (レベル 1) C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: b1f62b744547dc91923b397f3715c09659433a05
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052341"
---
# <a name="compiler-warning-level-1-c4810"></a>コンパイラの警告 (レベル 1) C4810

pragma の値 pack(show) == n

この警告は、 **pack** プラグマの [show](../../preprocessor/pack.md) オプションを使用すると発行されます。 *n* は pack の現在の値です。

たとえば、次のコードは、pack プラグマで C4810 警告がどのように発生するかを示しています。

```cpp
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```