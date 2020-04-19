---
title: コンパイラ エラー C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: 6b9f94b1b17aad85aab37659565e6e0827b5a824
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755513"
---
# <a name="compiler-error-c2570"></a>コンパイラ エラー C2570

' identifier ': 共用体に基底クラスを含めることはできません

共用体は、クラス、構造体、または共用体から派生します。 これは許可されていません。 代わりに、派生型をクラスまたは構造体として宣言してください。

次の例では、C2570 が生成されます。

```cpp
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```
