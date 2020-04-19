---
title: コンパイラ エラー C3204
ms.date: 11/04/2016
f1_keywords:
- C3204
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
ms.openlocfilehash: 72b9f4fe926b617d7c5b3538fb9d3281e1d95a5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738701"
---
# <a name="compiler-error-c3204"></a>コンパイラ エラー C3204

catch ブロック内から '_alloca' を呼び出すことはできません。

このエラーは、catch ブロック内から [_alloca](../../c-runtime-library/reference/alloca.md) への呼び出しを使用すると発生します。

## <a name="example"></a>使用例

次の例では C3204 が生成されます。

```cpp
// C3204.cpp
// compile with: /EHsc
#include <malloc.h>

void ShowError(void)
{
   try
   {
   }
   catch(...)
   {
      _alloca(1);   // C3204
   }
}
```
