---
title: コンパイラ エラー C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761492"
---
# <a name="compiler-error-c3865"></a>コンパイラ エラー C3865

' calling_convention ': ネイティブメンバー関数でのみ使用できます

呼び出し規約が、グローバル関数またはマネージメンバー関数のいずれかであった関数で使用されました。 呼び出し規約は、ネイティブ (管理されていない) メンバー関数でのみ使用できます。

詳細については、「[呼び出し規則](../../cpp/calling-conventions.md)」を参照してください。

次の例では、C3865 が生成されます。

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
