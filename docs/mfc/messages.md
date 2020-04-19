---
title: メッセージ
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384128"
---
# <a name="messages"></a>メッセージ

メッセージ ループで、`Run`クラスのメンバー関数`CWinApp`を取得しますがさまざまなイベントによって生成されたメッセージをキューに登録します。 たとえば、ユーザーには、マウスがクリックすると、Windows は WM_LBUTTONDOWN マウスの左ボタンが押されたときに、マウスの左ボタンが離されたとき、WM_LBUTTONUP など、いくつかのマウス関連メッセージを送信します。 アプリケーション メッセージ ループのフレームワークの実装では、適切なウィンドウにメッセージをディスパッチします。

メッセージの重要なカテゴリが記載されて[メッセージ カテゴリ](../mfc/message-categories.md)します。

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)
