---
title: 拡張コンボ ボックス コントロールでの通知メッセージの処理
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908108"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>拡張コンボ ボックス コントロールでの通知メッセージの処理

ユーザーが拡張コンボ ボックスを操作すると、コントロール (`CComboBoxEx`) から親ウィンドウ (通常はビュー オブジェクトかダイアログ オブジェクト) に通知メッセージが送信されます。 応答として何らかの操作を行う場合は、これらのメッセージを処理します。 たとえば、ユーザーがドロップダウンリストをアクティブにしたり、コントロールのエディットボックスをクリックしたりすると、CBEN_BEGINEDIT 通知が送信されます。

[クラスウィザード](reference/mfc-class-wizard.md)を使用して、実装するメッセージの親クラスに通知ハンドラーを追加します。

拡張コンボ ボックス コントロールで送信される通知を一覧で説明します。

- CBEN_BEGINEDIT は、ユーザーがドロップダウンリストをアクティブにしたとき、またはコントロールのエディットボックスをクリックしたときに送信されます。

- CBEN_DELETEITEM 項目が削除されたときに送信されます。

- CBEN_DRAGBEGIN は、コントロールの編集部分に表示される項目のイメージのドラッグをユーザーが開始したときに送信されます。

- CBEN_ENDEDIT ユーザーがエディットボックス内の操作を完了したとき、またはコントロールのドロップダウンリストから項目を選択したときに送信されます。

- CBEN_GETDISPINFO コールバック項目に関する表示情報を取得するために送信されます。

- CBEN_INSERTITEM コントロールに新しい項目が挿入されたときに送信されます。

## <a name="see-also"></a>関連項目

[CComboBoxEx の使い方](../mfc/using-ccomboboxex.md)<br/>
[コントロール](../mfc/controls-mfc.md)
