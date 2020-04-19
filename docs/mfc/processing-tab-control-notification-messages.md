---
title: タブ コントロールの通知メッセージの処理
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: cc322a038717d48f440df1ec571674cec80743ce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908061"
---
# <a name="processing-tab-control-notification-messages"></a>タブ コントロールの通知メッセージの処理

ユーザーがタブまたはボタンをクリックすると、タブコントロール ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) によって通知メッセージが親ウィンドウに送信されます。 応答として何らかの操作を行う場合は、これらのメッセージを処理します。 たとえば、ユーザーがタブをクリックしたときに、表示する前にページにコントロールデータを事前設定することができます。

ビューまたはダイアログクラスのタブコントロールから、WM_NOTIFY メッセージを処理します。 [クラスウィザード](reference/mfc-class-wizard.md)を使用して、処理されている通知メッセージに基づいた switch ステートメントを含む[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) handler 関数を作成します。 タブコントロールが親ウィンドウに送信できる通知の一覧については、Windows SDK の「[タブコントロールリファレンス](/windows/win32/controls/tab-control-reference)」の「**通知**」セクションを参照してください。

## <a name="see-also"></a>関連項目

[CTabCtrl の使い方](../mfc/using-ctabctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
