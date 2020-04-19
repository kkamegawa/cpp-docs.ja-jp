---
title: ツリー コントロールのラベルの編集
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 4b53d2c8e5a26a4dc37dfd7ae0710748bcd27bf6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741234"
---
# <a name="tree-control-label-editing"></a>ツリー コントロールのラベルの編集

ユーザーは、 **TVS_EDITLABELS**スタイルを持つツリーコントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) の項目のラベルを直接編集できます。 ユーザーは、フォーカスのあるアイテムのラベルをクリックして編集を開始します。 アプリケーションは、 [Editlabel](../mfc/reference/ctreectrl-class.md#editlabel)メンバー関数を使用して編集を開始します。 編集が開始され、キャンセルまたは完了したときに、ツリーコントロールによって通知が送信されます。 編集が完了したら、必要に応じて、項目のラベルを更新する必要があります。

ラベルの編集が開始されると、ツリーコントロールは[TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit)通知メッセージを送信します。 この通知を処理することで、一部のラベルの編集を許可し、他のラベルを編集できないようにすることができます。 0を返すと編集が可能になり、0以外の場合はそれを返すことができません。

ラベルの編集が取り消された場合、または完了した場合、ツリーコントロールは[TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit)通知メッセージを送信します。 *LParam*パラメーターは[Nmtvdispinfo](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow)構造体のアドレスです。 **項目**メンバーは、項目を識別し、編集されたテキストを含む[TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw)構造体です。 必要に応じて、編集した文字列を検証した後で、項目のラベルを更新する必要があります。 編集が取り消された`TV_ITEM`場合、の*psztext*メンバーは0になります。

通常、ラベルの編集中に、 [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit)通知メッセージに応答して、 [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol)メンバー関数を使用してラベル編集に使用される編集コントロールへのポインターを取得できます。 エディットコントロールの[Setlimittext](../mfc/reference/cedit-class.md#setlimittext)メンバー関数を呼び出して、ユーザーが入力できるテキストの量を制限したり、編集コントロールをサブクラス化して、無効な文字を途中で破棄したりできます。 ただし、エディットコントロールは、 **TVN_BEGINLABELEDIT**が送信され*た後*にのみ表示されることに注意してください。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
