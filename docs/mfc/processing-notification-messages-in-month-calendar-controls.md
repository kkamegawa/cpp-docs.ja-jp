---
title: 月間予定表コントロールでの通知メッセージの処理
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908074"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>月間予定表コントロールでの通知メッセージの処理

ユーザーが月間予定表コントロールを操作する (日付を選択するか、別の月を表示する)`CMonthCalCtrl`と、コントロール () は親ウィンドウ (通常はビューまたはダイアログオブジェクト) に通知メッセージを送信します。 応答として何らかの操作を行う場合は、これらのメッセージを処理します。 たとえば、ユーザーが表示する新しい月を選択すると、強調表示する日付のセットを指定できます。

[クラスウィザード](reference/mfc-class-wizard.md)を使用して、実装するメッセージの親クラスに通知ハンドラーを追加します。

次の一覧では、月間予定表コントロールによって送信されるさまざまな通知について説明します。

- MCN_GETDAYSTATE は、どの日を太字で表示するかについての情報を要求します。 この通知を処理する方法については、「[月間予定表コントロールの日付状態の設定](../mfc/setting-the-day-state-of-a-month-calendar-control.md)」を参照してください。

- MCN_SELCHANGE は、選択した日付または日付の範囲が変更されたことを親に通知します。

- MCN_SELECT は、明示的な日付の選択が行われたことを親に通知します。

## <a name="see-also"></a>関連項目

[CMonthCalCtrl の使い方](../mfc/using-cmonthcalctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
