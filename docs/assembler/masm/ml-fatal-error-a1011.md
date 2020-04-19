---
title: ML の致命的なエラー A1011
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 5607d6d56e0b3889332dcf2624d519529819b1c9
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318080"
---
# <a name="ml-fatal-error-a1011"></a>ML の致命的なエラー A1011

**ディレクティブはコントロールブロック内になければなりません**

アセンブラーは、予期されていない上位レベルのディレクティブを検出しました。 次のいずれかのディレクティブが見つかりました。

- [.それ以外](dot-else.md)の場合は[。IF](dot-if.md)

- [.ENDIF](dot-endif.md)が[ありません。IF](dot-if.md)

- [.ENDW](dot-endw.md)なし[。しばらく](dot-while.md)

- [.UNTILCXZ](dot-untilcxz.md) without [.REPEAT](dot-repeat.md)

- [.](dot-continue.md)を指定せずに続行[します。また](dot-while.md)は[。繰り返し](dot-repeat.md)

- [.](dot-break.md)を使用せずに中断[します。また](dot-while.md)は[。繰り返し](dot-repeat.md)

- [.その他](dot-else.md)の `.ELSE`

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
