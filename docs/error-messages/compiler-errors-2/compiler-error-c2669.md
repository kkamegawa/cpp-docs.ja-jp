---
title: コンパイラ エラー C2669
ms.date: 11/04/2016
f1_keywords:
- C2669
helpviewer_keywords:
- C2669
ms.assetid: f9cb8111-bcdc-484b-a863-2c42e15a0496
ms.openlocfilehash: 7944ced947ba1d7c8b10172560ce6237a554e236
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300792"
---
# <a name="compiler-error-c2669"></a>コンパイラ エラー C2669

メンバー関数は無名共用体では使用できません。

[無名共用体](../../cpp/unions.md#anonymous_unions)メンバー関数を含めることはできません。

## <a name="example"></a>例

次の例では、C2669 が生成されます。

```cpp
// C2669.cpp
struct X {
   union {
      int i;
      void f() {   // C2669, remove function
         i = 0;
      }
   };
};
```
