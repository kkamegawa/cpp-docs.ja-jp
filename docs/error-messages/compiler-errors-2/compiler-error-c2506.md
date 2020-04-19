---
title: コンパイラ エラー C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746839"
---
# <a name="compiler-error-c2506"></a>コンパイラ エラー C2506

' member ': ' __declspec (修飾子) ' はこのシンボルに適用できません

マネージクラスの静的メンバーに対して、プロセスごとまたは appdomain ごとの宣言を行うことはできません。

詳細については、「 [appdomain](../../cpp/appdomain.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、C2506 が生成されます。

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
