---
title: Windows ソケット:ソケット通知
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: df7bfe8a95221682d0f7f4ebb123bd15b79144d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358192"
---
# <a name="windows-sockets-socket-notifications"></a>Windows ソケット:ソケット通知

この記事では、ソケット クラス内の通知関数について説明します。 これらのメンバー関数は、重要なイベント、ソケット オブジェクトに通知するフレームワークから呼び出されるコールバック関数です。 通知関数は次のとおりです。

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive):このソケットを呼び出して取得するためのバッファーでデータがあることを通知[受信](../mfc/reference/casyncsocket-class.md#receive)します。

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend):このソケットを呼び出してデータを送信できるようになりましたことを通知[送信](../mfc/reference/casyncsocket-class.md#send)します。

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept):呼び出すことによって保留中の接続要求を受け付けられるこのリッスン ソケットに通知[Accept](../mfc/reference/casyncsocket-class.md#accept)します。

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect):その接続試行が完了しているソケットの通知: おそらく正常完了またはエラーが発生します。

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose):接続されているソケットが閉じられているこのソケットに通知します。

    > [!NOTE]
    >  追加の通知、関数は、 [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)します。 この通知は、送信側のソケットに送信する「帯域外」のデータを受信側のソケットに指示します。 帯域外のデータは、接続されているストリーム ソケットの各ペアに関連付けられている論理的に独立したチャネルです。 帯域外のチャネルは通常、「緊急」のデータ送信に使用されます。 MFC では、帯域外のデータをサポートします。 クラスを操作するユーザーを高度な[CAsyncSocket](../mfc/reference/casyncsocket-class.md)クラスのユーザーは、帯域外のチャネルを使用する必要があります[CSocket](../mfc/reference/csocket-class.md)これを使用しないでください。 簡単な方法では、このようなデータを渡すための 2 つ目のソケットを作成します。 帯域外のデータの詳細については、Windows SDK で利用できる Windows ソケット仕様を参照してください。

クラスから派生させる場合`CAsyncSocket`、ネットワーク、アプリケーションに関心のあるイベントの通知関数をオーバーライドする必要があります。 クラスからクラスを派生させる場合`CSocket`目的の通知関数をオーバーライドするかどうか、選択肢となります。 使用することも`CSocket`自体には、この場合、通知関数の既定値は、何もします。

これらの関数は、オーバーライド可能なコールバック関数です。 `CAsyncSocket` `CSocket`に通知をメッセージの変換が、それらを使用する場合に、応答に対して、通知で実行される関数を実装する必要があります。 通知関数は、ソケットが読み取られるデータの存在など、関心のあるイベントの通知時に呼び出されます。

MFC が通知される時に、ソケットの動作をカスタマイズできるように通知関数を呼び出します。 などを呼び出す`Receive`から、`OnReceive`を読み取るデータが、呼び出すことに、つまりが通知に通知関数`Receive`を読むことです。 この方法は、必要ではありませんが、有効なシナリオです。 代わりに、進行状況を追跡する通知関数を使用する場合があります印刷**トレース**メッセージ、という具合です。

ソケットの派生クラスでの通知関数をオーバーライドし、実装を提供することによって、これらの通知の利点を実行できます。

受信または送信データなどの操作中に、`CSocket`オブジェクトが同期状態になります。 同期の状態では、ソケットの他のもので、通知は、現在のソケットを待機して、通知の間にキューイングされます。 (たとえば中、`Receive`呼び出し、ソケットが読み込みの通知をします)。ソケット、同期操作を完了し、非同期が再び、他のソケットはキューに置かれた通知の受信を開始できます。

> [!NOTE]
>  `CSocket`、`OnConnect`通知関数を呼び出すことはありません。 接続は、呼び出す`Connect`、(正常にまたはエラー)、接続が完了したときに返されます。 MFC 実装の詳細は、接続の通知を処理する方法。

詳細については、通知の各関数は、クラスの下にある関数を参照してください。`CAsyncSocket`で、 *MFC リファレンス*します。 ソース コードと MFC のサンプルについては、「 [MFC サンプル](../overview/visual-cpp-samples.md)します。

詳細については次を参照してください:

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: ソケット クラスからの派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows ソケット: アーカイブ付きソケットの動作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows ソケット: ブロッキング](../mfc/windows-sockets-blocking.md)

- [Windows ソケット: バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)

- [Windows ソケット: 文字列の変換](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
