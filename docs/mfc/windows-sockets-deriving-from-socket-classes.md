---
title: Windows ソケット:ソケット クラスから派生します。
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: 12ab66cfd9212cd79752e2f6359b857194c6428c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385259"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows ソケット:ソケット クラスから派生します。

この記事では、socket クラスのいずれかから、独自のクラスを派生させることで利用できる機能について説明します。

ソケット クラスは、いずれかから派生できます[CAsyncSocket](../mfc/reference/casyncsocket-class.md)または[CSocket](../mfc/reference/csocket-class.md)独自の機能を追加します。 具体的には、これらのクラスは、オーバーライドできる仮想メンバー関数の番号を指定します。 これらの関数を含める[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)、 [OnSend](../mfc/reference/casyncsocket-class.md#onsend)、 [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)、 [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)、および[OnClose](../mfc/reference/casyncsocket-class.md#onclose)します。 関数は、ネットワーク イベントが発生したときに、通知を活用するために、ソケットの派生クラスでオーバーライドできます。 フレームワークは、これらの読み取りを開始できることを通知するデータの受信などの重要なソケットのイベントの通知のコールバック関数を呼び出します。 通知関数の詳細については、次を参照してください。 [Windows ソケット。通知のソケット](../mfc/windows-sockets-socket-notifications.md)します。

さらに、クラス`CSocket`提供、 [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending)メンバー関数 (高度なオーバーライド可能な)。 MFC は、ソケットは、Windows ベースのメッセージをポンプが中に、この関数を呼び出します。 オーバーライドできます`OnMessagePending`を Windows からの特定のメッセージを探し、それらに応答します。

既定のバージョン`OnMessagePending`クラスで提供される`CSocket`ブロッキング呼び出しが完了するを待機中に WM_PAINT メッセージのメッセージ キューを調べます。 これは、表示品質を向上させるために描画メッセージをディスパッチします。 別に何を行うと、これを示しています、関数の方が優先する方法の 1 つ自分で。 別の例としては、使用を検討して`OnMessagePending`次のタスクの。 ネットワーク トランザクションの完了を待っている間にモードレス ダイアログ ボックスを表示するとします。 ダイアログ ボックスには、ユーザーは、時間がかかりすぎるブロックしているトランザクションのキャンセルに使用できる [キャンセル] ボタンが含まれています。 `OnMessagePending`オーバーライドは、このモードレス ダイアログ ボックスに関連するメッセージをポンプ可能性があります。

`OnMessagePending`オーバーライド、いずれかを返す**TRUE**の基本クラスのバージョンへの呼び出しからの戻り値または`OnMessagePending`します。 完了する必要のある作業を実行する場合は、基本クラスのバージョンを呼び出します。

詳細については次を参照してください:

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: ブロッキング](../mfc/windows-sockets-blocking.md)

- [Windows ソケット: バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)

- [Windows ソケット: 文字列の変換](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
