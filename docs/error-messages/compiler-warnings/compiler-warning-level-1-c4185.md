---
title: コンパイラの警告 (レベル 1) C4185
ms.date: 11/04/2016
f1_keywords:
- C4185
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
ms.openlocfilehash: 6c818f99afb4cd60f5e129f48494aee0c24ba86a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626199"
---
# <a name="compiler-warning-level-1-c4185"></a>コンパイラの警告 (レベル 1) C4185

不明な #import の属性 'attribute' を無視します

属性は、 `#import`の有効な属性ではありません。 これは無視されます。

## <a name="example"></a>例

```cpp
// C4185.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_such_attribute   // C4185
```