---
title: メッセージの送信と受信
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: bda261f4141a7ceb4e678535d9012650818fabce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384050"
---
# <a name="message-sending-and-receiving"></a>メッセージの送信と受信

プロセスおよびフレームワークの応答の送信部分を検討してください。

ほとんどのメッセージは、プログラムでのユーザー操作の結果としてください。 メニュー項目またはツール バー ボタンでマウスのクリックで、またはキーの組み合わせによっては、コマンドが生成されます。 ユーザーはなどによって、Windows メッセージを生成し、移動またはウィンドウのサイズを変更します。 その他の Windows メッセージは、windows を取得または、フォーカスが失われ、プログラムの起動や終了などのイベントが発生したときに送信されます。 コントロールの通知メッセージは、マウスのクリックやその他のユーザーによる対話、ダイアログ ボックスで、ボタンやリスト ボックス コントロールなどのコントロールによって生成されます。

`Run`クラスのメンバー関数`CWinApp`メッセージを取得し、適切なウィンドウにそれらをディスパッチします。 ほとんどのコマンドのメッセージは、アプリケーションのメイン フレーム ウィンドウに送信されます。 `WindowProc`クラス ライブラリの取得での定義済みのメッセージとメッセージを受信したカテゴリによって異なる方法でルーティングします。

これで、プロセスの受信側の一部を検討してください。

メッセージの最初の受信側は、ウィンドウ オブジェクトである必要があります。 Windows メッセージは、ウィンドウ オブジェクトで直接、通常は処理されます。 説明されているコマンド ターゲットのチェーンにルーティングされるコマンド メッセージは、通常、アプリケーションのメイン フレーム ウィンドウから発信される[コマンド ルーティング](../mfc/command-routing.md)します。

メッセージまたはコマンドを受信できる各オブジェクトには、独自のメッセージをメッセージやコマンドのハンドラーの名前のマップがあります。

コマンド ターゲット オブジェクトを受信すると、メッセージまたはコマンドの一致をメッセージ マップを検索します。 メッセージのハンドラーが見つかると、ハンドラーを呼び出します。 メッセージ マップを検索する方法の詳細については、次を参照してください。[方法、フレームワークのメッセージ マップ検索](../mfc/how-the-framework-searches-message-maps.md)します。 図をもう一度参照してください。[フレームワークにおけるコマンド](../mfc/user-interface-objects-and-command-ids.md)します。

## <a name="see-also"></a>関連項目

[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)
