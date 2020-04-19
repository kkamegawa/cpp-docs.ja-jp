---
title: コンパイラ エラー C3265
ms.date: 11/04/2016
f1_keywords:
- C3265
helpviewer_keywords:
- C3265
ms.assetid: 10ab3e17-4a9f-4120-bab5-21473869b70f
ms.openlocfilehash: 633089115fe7edd0bdf06cdbcda6909ae7ac656e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754161"
---
# <a name="compiler-error-c3265"></a>コンパイラ エラー C3265

マネージド ' マネージドコンストラクト ' はアンマネージドコンストラクト ' で宣言できません

マネージオブジェクトをアンマネージコンテキストに含めることはできません。

次のサンプルでは、C3265 を再現します。

```cpp
// C3265_2.cpp
// compile with: /clr /LD
#include <vcclr.h>

ref class A { };

class B
// try the following line instead
// ref class B
{
   A ^a;   // C3265
   // or embed the managed handle using gcroot
   // try the following line instead
   // gcroot<A^> a;
};
```
