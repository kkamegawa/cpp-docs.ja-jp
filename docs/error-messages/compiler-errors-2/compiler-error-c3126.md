---
title: コンパイラエラー C3126
ms.date: 11/04/2016
f1_keywords:
- C3126
helpviewer_keywords:
- C3126
ms.assetid: e72658a3-5d85-4a31-89a4-dbc3d475973d
ms.openlocfilehash: 2b8901ce9914f35d4cd219f4d51477582fa676a8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760726"
---
# <a name="compiler-error-c3126"></a>コンパイラエラー C3126

マネージド型 ' type ' 内で共用体 ' union ' を定義することはできません

共用体はマネージド型の内部では定義できません。

次の例では、C3126 が生成されます。

```cpp
// C3126_2.cpp
// compile with: /clr /c
ref class Test
{
   union x
   {   // C3126
      int a;
      int b;
   };
};
```
