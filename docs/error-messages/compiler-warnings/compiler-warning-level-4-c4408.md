---
title: コンパイラの警告 (レベル 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 27d3bb7b66b3f3d5ce4e48b56c7e3ae2a71cf115
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990899"
---
# <a name="compiler-warning-level-4-c4408"></a>コンパイラの警告 (レベル 4) C4408

anonymousstruct または union はデータメンバーを宣言しませんでした

匿名構造体または匿名共用体には、少なくとも 1 つのデータ メンバーが必要です。

次の例では C4408 が生成されます。

```cpp
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```
