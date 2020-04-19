---
title: 月間予定表コントロールの日付状態の設定
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907524"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>月間予定表コントロールの日付状態の設定

月間予定表コントロールの属性の1つは、その月の各日に、コントロールの日付状態と呼ばれる情報を格納する機能です。 この情報は、現在表示されている月の特定の日付を強調するために使用されます。

> [!NOTE]
>  日付`CMonthCalCtrl`状態情報を表示するには、オブジェクトに MCS_DAYSTATE スタイルが設定されている必要があります。

日状態情報は、32ビットのデータ型**MONTHDAYSTATE**として表現されます。 **MONTHDAYSTATE**ビットフィールドの各ビット (1 ~ 31) は、月の1日の状態を表します。 ビットがオンの場合は、対応する日が太字で表示されます。それ以外の場合は、何も強調表示されません。

月間予定表コントロールの日の状態を設定する方法には、 [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate)を明示的に呼び出す方法と、MCN_GETDAYSTATE 通知メッセージを処理する方法の2つがあります。

## <a name="handling-the-mcn_getdaystate-notification-message"></a>MCN_GETDAYSTATE 通知メッセージの処理

MCN_GETDAYSTATE メッセージは、表示される月内の日数を表示する方法を決定するために、コントロールによって送信されます。

> [!NOTE]
>  このコントロールは、表示されている月に対して前月と翌月をキャッシュするので、新しい月を選択するたびにこの通知を受け取ります。

このメッセージを適切に処理するには、要求されている月の状態情報の数を確認し、適切な値を使用して**MONTHDAYSTATE**構造体の配列を初期化し、新しいを使用して関連する構造体のメンバーを初期化します。参照. 次の手順では、必要な手順について説明し`CMonthCalCtrl`ます。ここでは、 *m_monthcal*という名前のオブジェクトと**MONTHDAYSTATE** objects の配列*mdstate*を使用していることを前提としています。

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>MCN_GETDAYSTATE 通知メッセージを処理するには

1. [クラスウィザード](reference/mfc-class-wizard.md)を使用して、MCN_GETDAYSTATE メッセージの通知ハンドラーを*m_monthcal*オブジェクトに追加します (「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください)。

1. ハンドラーの本体に次のコードを追加します。

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   この例では、 *Pnmhdr*ポインターを適切な型に変換し、情報が要求される月数 (`pDayState->cDayState`) を決定します。 月ごとに、現在のビットフィールド (`pDayState->prgDayState[i]`) が0に初期化され、必要な日付が設定されます (この場合は毎月15日)。

## <a name="see-also"></a>関連項目

[CMonthCalCtrl の使い方](../mfc/using-cmonthcalctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
