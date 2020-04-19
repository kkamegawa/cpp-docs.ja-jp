---
title: 日時指定コントロールの通知メッセージの処理
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: 500c31d494c53f34febb0f22c82f13b08a1d33cd
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908118"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>日時指定コントロールの通知メッセージの処理

ユーザーが日付と時刻の選択コントロールを操作すると、コントロール`CDateTimeCtrl`() は親ウィンドウ (通常はビューまたはダイアログオブジェクト) に通知メッセージを送信します。 応答として何らかの操作を行う場合は、これらのメッセージを処理します。 たとえば、ユーザーが日付と時刻の選択を開いて、埋め込み月間予定表コントロールを表示すると、DTN_DROPDOWN 通知が送信されます。

[クラスウィザード](reference/mfc-class-wizard.md)を使用して、実装するメッセージの親クラスに通知ハンドラーを追加します。

次に、[日付と時刻の選択] コントロールによって送信されるさまざまな通知を示します。

- DTN_DROPDOWN は、埋め込み月間予定表コントロールが表示されようとしていることを親に通知します。 この通知は、DTS_UPDOWN スタイルが設定されていない場合にのみ送信されます。 この通知の詳細については、「[埋め込み月間予定表コントロールへのアクセス](../mfc/accessing-the-embedded-month-calendar-control.md)」を参照してください。

- DTN_CLOSEUP は、埋め込み月間予定表コントロールが閉じようとしていることを親に通知します。 この通知は、DTS_UPDOWN スタイルが設定されていない場合にのみ送信されます。

- DTN_DATETIMECHANGE は、コントロールで変更が発生したことを親に通知します。

- DTN_FORMAT は、テキストがコールバックフィールドに表示される必要があることを親に通知します。 この通知およびコールバックフィールドの詳細については、「[日付と時刻の選択コントロールでのコールバックフィールドの使用](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)」を参照してください。

- DTN_FORMATQUERY は、コールバックフィールドに表示される文字列の最大許容サイズを指定するように親に要求します。 この通知を処理することにより、コントロールは常に出力を正しく表示し、コントロールの表示内のちらつきを減らすことができます。 この通知の詳細については、「[日付と時刻の選択コントロールでのコールバックフィールドの使用](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)」を参照してください。

- DTN_USERSTRING は、ユーザーが日付と時刻の選択コントロールの内容の編集を完了したことを親に通知します。 この通知は、DTS_APPCANPARSE スタイルが設定されている場合にのみ送信されます。

- DTN_WMKEYDOWN は、ユーザーがコールバックフィールドを入力したときに親に通知します。 この通知を処理して、日付と時刻の選択コントロールのコールバック以外のフィールドでサポートされる同じキーボード応答をエミュレートします。 この通知の詳細については、「Windows SDK での[DTP コントロールのコールバックフィールドのサポート](/windows/win32/Controls/date-and-time-picker-controls)」を参照してください。

## <a name="see-also"></a>関連項目

[CDateTimeCtrl の使い方](../mfc/using-cdatetimectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
