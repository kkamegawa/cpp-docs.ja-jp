---
title: ML の致命的でないエラー A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316981"
---
# <a name="ml-nonfatal-error-a2050"></a>ML の致命的でないエラー A2050

**実数または BCD の数値は使用できません**

データ初期化子としてではなく、浮動小数点 (実数) またはバイナリのコード化された decimal (BCD) 定数が使用されました。

次のいずれかが発生しました。

- 式で実数または BCD が使用されました。

- [DWORD](dword.md)、 [QWORD](qword.md)、または[t](tbyte.md)以外のディレクティブを初期化するために実数が使用されました。

- BCD は、`TBYTE`以外のディレクティブを初期化するために使用されました。

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
