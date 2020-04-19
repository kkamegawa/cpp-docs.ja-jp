---
title: ML の致命的でないエラー A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311950"
---
# <a name="ml-nonfatal-error-a2219"></a>ML の致命的でないエラー A2219

> アンワインドコードのオフセットのアラインメントが正しくありません

## <a name="remarks"></a>コメント

[&period;ALLOCSTACK](dot-allocstack.md)および[&period;SAVEREG](dot-savereg.md)のオペランドは8の倍数である必要があります。  [&period;SAVEXMM128](dot-savexmm128.md)と[&period;setframe](dot-setframe.md)のオペランドは16の倍数である必要があります。

## <a name="see-also"></a>関連項目

[ML エラーメッセージ](ml-error-messages.md)
