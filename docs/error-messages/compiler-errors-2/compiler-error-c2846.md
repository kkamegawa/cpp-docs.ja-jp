---
title: コンパイラ エラー C2846
ms.date: 11/04/2016
f1_keywords:
- C2846
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
ms.openlocfilehash: eef558301ce2d623ef78aab40a7a054cd73037df
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750612"
---
# <a name="compiler-error-c2846"></a>コンパイラ エラー C2846

' constructor ': インターフェイスにコンストラクターを含めることはできません

ビジュアルC++ [インターフェイス](../../cpp/interface.md)にコンストラクターを含めることはできません。

次の例では、C2846 が生成されます。

```cpp
// C2846.cpp
// compile with: /c
__interface C {
   C();   // C2846 constructor not allowed in an interface
};
```
