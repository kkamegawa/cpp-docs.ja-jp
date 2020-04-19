---
title: コンパイラ エラー C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 9f083f5c21e494d08374e72155b44ee14719881f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743147"
---
# <a name="compiler-error-c3387"></a>コンパイラ エラー C3387

' member ': __declspec (dllexport)/\__declspec (dllimport) は、マネージ型または WinRT 型のメンバーには適用できません

`dllimport` および[dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修飾子は、マネージ型または Windows ランタイム型のメンバーでは無効です。

次の例では C3387 を生成し、その修正方法を示しています。

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
