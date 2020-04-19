---
title: ツリー コントロールの通知メッセージ
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 90e2e112d7862dfed7d8af31cfb72ff45633a2c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181642"
---
# <a name="tree-control-notification-messages"></a>ツリー コントロールの通知メッセージ

ツリー コントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) WM_NOTIFY メッセージとして、次の通知メッセージを送信します。

|通知メッセージ|説明|
|--------------------------|-----------------|
|TVN_BEGINDRAG|ドラッグ アンド ドロップ操作の開始を通知します。|
|TVN_BEGINLABELEDIT|ラベルのインプレース編集の開始を通知します。|
|TVN_BEGINRDRAG|マウスの右ボタンを使用して、ドラッグ アンド ドロップ操作の開始を通知します。|
|TVN_DELETEITEM|特定の項目の削除を知らせます。|
|TVN_ENDLABELEDIT|ラベルの編集の終了を通知します。|
|TVN_GETDISPINFO|ツリー コントロールが項目を表示するが必要な要求情報|
|TVN_ITEMEXPANDED|信号の子項目の親項目の一覧が展開されたかどうか、または折りたたまれていること|
|TVN_ITEMEXPANDING|子アイテムの親項目の一覧が展開または折りたたむに信号|
|TVN_KEYDOWN|キーボード イベントを通知します。|
|TVN_SELCHANGED|1 つの項目から別の選択が変更されたことを通知|
|TVN_SELCHANGING|選択範囲は 1 つの項目から別に変更することを通知|
|TVN_SETDISPINFO|項目に保持される情報を更新する通知|

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
