---
title: ML の致命的なエラー A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317124"
---
# <a name="ml-fatal-error-a1007"></a>ML の致命的なエラー A1007

**入れ子レベルが深すぎます**

アセンブラーが入れ子の制限に達しました。 特に明記されていない限り、制限は20レベルです。

次のいずれかの入れ子のレベルが深すぎます。

- などの高レベルのディレクティブ[。の場合は](dot-if.md) [。](dot-repeat.md)またはを繰り返し[ます。しばらくお待ち](dot-while.md)ください。

- 構造体の定義。

- 条件付きアセンブリディレクティブ。

- プロシージャの定義。

- [Pushcontext](pushcontext.md)ディレクティブ (制限は 10)。

- セグメントの定義。

- インクルードファイル。

- マクロ。

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
