---
title: Rebar コントロールでの通知メッセージの処理
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 948990c8597c2ccdcec496252c6801c02a78cbf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507956"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Rebar コントロールでの通知メッセージの処理

Rebar コントロールの親クラスで、処理する rebar コントロール`OnChildNotify` (`CReBarCtrl`) 通知メッセージの switch ステートメントを含むハンドラー関数を作成します。 ユーザーが rebar コントロール上でオブジェクトをドラッグしたり、rebar バンドのレイアウトを変更したり、rebar コントロールからバンドを削除したりすると、通知が親ウィンドウに送信されます。

Rebar コントロールオブジェクトは、次の通知メッセージを送信できます。

- Rebar が自動的にサイズを変更したときに rebar コントロール (RBS_AUTOSIZE スタイルで作成) によって送信された RBN_AUTOSIZE。

- RBN_BEGINDRAG は、ユーザーがバンドのドラッグを開始したときに rebar コントロールによって送信されます。

- RBN_CHILDSIZE バンドの子ウィンドウのサイズが変更されたときに rebar コントロールによって送信されます。

- RBN_DELETEDBAND は、バンドが削除された後に rebar コントロールによって送信されます。

- バンドが削除されようとしているときに rebar コントロールによって送信された RBN_DELETINGBAND。

- RBN_ENDDRAG は、ユーザーがバンドのドラッグを停止したときに rebar コントロールによって送信されます。

- オブジェクトがコントロールのバンド上にドラッグされたときに、rebar コントロール (RBS_REGISTERDROP スタイルで作成) によって送信された RBN_GETOBJECT。

- RBN_HEIGHTCHANGE は、その高さが変更されたときに rebar コントロールによって送信されます。

- RBN_LAYOUTCHANGED は、ユーザーがコントロールのバンドのレイアウトを変更したときに rebar コントロールによって送信されます。

これらの通知の詳細については、Windows SDK の「 [Rebar コントロールリファレンス](/windows/win32/controls/rebar-control-reference)」を参照してください。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
