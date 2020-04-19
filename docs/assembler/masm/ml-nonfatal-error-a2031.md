---
title: ML の致命的でないエラー A2031
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 4764f7296e28e2128fc4fc80e64f39ceb2a8ed8c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317072"
---
# <a name="ml-nonfatal-error-a2031"></a>ML の致命的でないエラー A2031

**インデックスまたはベースレジスタである必要があります**

メモリ式でベースレジスタまたはインデックスレジスタではないレジスタを使用しようとしました。

たとえば、次の式では、このエラーが発生します。

```asm
[ax]
[bl]
```

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
