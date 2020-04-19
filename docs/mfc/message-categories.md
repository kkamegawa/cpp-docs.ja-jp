---
title: メッセージの種類
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 07d9e706e8ed01a81ee580e7c4e11fa1f1a7a8df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206881"
---
# <a name="message-categories"></a>メッセージの種類

メッセージの種類は用に作成するハンドラーは次の 3 つの主なカテゴリがあります。

1. Windows メッセージ

   以降では主にそのメッセージが含まれます、 **wm _ で始まる**WM_COMMAND を除くのプレフィックス。 Windows メッセージは、windows とビューによって処理されます。 これらのメッセージは、多くの場合、メッセージを処理する方法を決定するで使用されるパラメーターを指定します。

1. コントロールの通知

   これには、親ウィンドウにコントロールとその他の子ウィンドウから WM_COMMAND 通知メッセージが含まれます。 たとえば、エディット コントロールではその親に EN_CHANGE コントロール通知コードを格納しているユーザーがエディット コントロールでテキストを変更可能性があるアクションを実行したときに WM_COMMAND メッセージが送信します。 メッセージのウィンドウのハンドラーは、コントロール内のテキストを取得するなど、いくつかの適切な方法で、通知メッセージに応答します。

   フレームワークは、他のコントロールの通知メッセージをルーティング**wm _ で始まる**メッセージ。 ただし、1 つの例外は、それらをクリックすると、ボタンによって送信された BN_CLICKED コントロール通知のメッセージです。 このメッセージは、コマンド メッセージとして特別な処理は、その他のコマンドと同様にルーティングします。

1. コマンド メッセージ

   ユーザー インターフェイス オブジェクトから WM_COMMAND 通知メッセージが含まれます: メニューのツールバーのボタン、およびアクセラレータ キー。 フレームワークは、他のメッセージを異なる方法でコマンドを処理し、で説明したように、オブジェクトの多くの種類で処理できる[コマンド ターゲット](../mfc/command-targets.md)します。

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows メッセージとコントロール通知メッセージ

メッセージ 1 と 2 のカテゴリで、Windows メッセージとコントロール通知-windows によって処理されます: クラスから派生したクラスのオブジェクトを`CWnd`します。 これが含まれています`CFrameWnd`、 `CMDIFrameWnd`、 `CMDIChildWnd`、 `CView`、 `CDialog`、およびこれらの基本クラスから派生した独自のクラス。 このようなオブジェクトをカプセル化、 `HWND`Windows のウィンドウを識別するハンドル。

##  <a name="_core_command_messages"></a> コマンド メッセージ

メッセージ カテゴリ 3-コマンド-各種のオブジェクトによって処理されることができます: ドキュメント、ドキュメント テンプレート、および windows とビューだけでなく、アプリケーション オブジェクト自体。 コマンドは特定のオブジェクトに直接影響を与える場合は、コマンドを処理するオブジェクトを指定しても意味します。 たとえば、ファイル メニューの 開く コマンドは、アプリケーションで論理的に関連付けられている: アプリケーションは、コマンドを受信すると、指定されたドキュメントを開きます。 したがって、開いているコマンドのハンドラーは、アプリケーション クラスのメンバー関数です。 詳細については、コマンドおよびオブジェクトへのルーティング方法は、次を参照してください。[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)します。

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)
