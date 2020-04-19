---
title: コンパイラの警告 (レベル 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 3d2372275da02a7c3bbde6c8bf044c621c5d3d09
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624923"
---
# <a name="compiler-warning-level-1-c4229"></a>コンパイラの警告 (レベル 1) C4229

旧形式の使用: データの修飾子は無視されます

データ宣言で `__cdecl` などの Microsoft 修飾子を使用することは、古い方法です。

## <a name="example"></a>例

```cpp
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```