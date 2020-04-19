---
title: ダイアログ データ バリデーション
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685762"
---
# <a name="dialog-data-validation"></a>ダイアログ データ バリデーション

「[ダイアログデータエクスチェンジ](../mfc/dialog-data-exchange.md)」の例に示すように、DDV 関数を呼び出すことにより、データ交換に加えて検証を指定できます。 この例の `DDV_MaxChars` 呼び出しは、テキストボックスコントロールに入力された文字列が20文字を超えていないことを検証します。 通常、DDV 関数は、検証に失敗した場合にメッセージボックスを使用してユーザーに警告し、ユーザーがデータを再入力できるように、問題のあるコントロールにフォーカスを移します。 特定のコントロールの DDV 関数は、同じコントロールの DDX 関数の直後に呼び出す必要があります。

独自のカスタム DDX ルーチンおよび DDV ルーチンを定義することもできます。 DDX および DDV のその他の側面の詳細については、「 [MFC テクニカルノート 26](../mfc/tn026-ddx-and-ddv-routines.md)」を参照してください。

[メンバー変数の追加ウィザード](../ide/add-member-variable-wizard.md)では、データマップ内のすべての DDX 呼び出しと DDV 呼び出しが書き込まれます。

## <a name="see-also"></a>関連項目

[ダイアログ データ エクスチェンジとダイアログ データ検証](../mfc/dialog-data-exchange-and-validation.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[ダイアログ データ エクスチェンジ](../mfc/dialog-data-exchange.md)
