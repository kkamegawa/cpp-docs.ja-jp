---
title: Windows ソケット:ブロック
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 26a361bc63da5f6e75144cc91fe837498a7f656b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371965"
---
# <a name="windows-sockets-blocking"></a>Windows ソケット:ブロック

この記事と関連記事では 2 つは、Windows ソケット プログラミングのいくつかの問題を説明します。 この記事では、ブロックについて説明します。 記事では、その他の問題がについて説明します。[Windows ソケット: バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)と[Windows ソケット。文字列を変換する](../mfc/windows-sockets-converting-strings.md)します。

使用するか、またはクラスから派生させる場合[CAsyncSocket](../mfc/reference/casyncsocket-class.md)、これらの問題を自分で管理する必要があります。 使用するか、またはクラスから派生させる場合[CSocket](../mfc/reference/csocket-class.md)MFC を管理します。

## <a name="blocking"></a>ブロック

ソケットが「ブロッキング モード」または「非ブロッキング モード」であることができます。 それらのアクションを完了するまで、ブロックしている (または同期) モードで、ソケットの関数は返されません。 関数が呼び出されたソケットは何もできないため、ブロックと呼ばれますがブロックされている: 呼び出しが戻るまで。 呼び出し、`Receive`メンバー関数はなどを送信する送信元アプリケーションの待機中に完了する任意の長さの時間をかかる場合があります (これを使用するかどうかは、 `CSocket`、またはを使用して`CAsyncSocket`ブロックと)。 場合、`CAsyncSocket`オブジェクトが (オペレーティング非同期的に) 非ブロッキング モードで、呼び出しは直ちに返りますおよび使用して取得できます現在エラー コード、 [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror)メンバー関数は**WSAEWOULDBLOCK**、モードのためすぐに返されませんが、呼び出しがブロックがあることを示す必要があります。 (`CSocket`値が戻りません。 **WSAEWOULDBLOCK**します。 クラスは、管理するをブロックします。)

ソケットの動作は 32 ビットおよび 64 ビット オペレーティング システム (Windows 95、Windows 98 など) と 16 ビットのオペレーティング システム (Windows 3.1) などで異なります。 16 ビットのオペレーティング システムとは異なり、32 ビットおよび 64 ビット オペレーティング システムがプリエンプティブなマルチタスクを使用し、マルチ スレッドを提供します。 32 ビットおよび 64 ビットのオペレーティング システムでは、個別のワーカー スレッドで、ソケットを収容できます。 アプリケーションの他のアクティビティを妨げることがなく、ブロッキングをコンピューティング時間をかけることがなくスレッドのソケットをブロックできます。 マルチ スレッド プログラミングについては、この記事を参照してください。[マルチ スレッド](../parallel/multithreading-support-for-older-code-visual-cpp.md)します。

> [!NOTE]
>  ブロックの性質を使用するマルチ スレッド アプリケーションで`CSocket`をユーザー インターフェイスの応答性に影響を与えずに、プログラムの設計を簡略化します。 メイン スレッドでのユーザー操作を処理することによって、`CSocket`別のスレッドで処理して、これらの論理操作を分離できます。 アプリケーションがマルチ スレッドでは、これら 2 つのアクティビティを結合して、通常は意味を使用して 1 つのスレッドとして処理する必要があります`CAsyncSocket`オンデマンド、またはオーバーライドする通信要求を処理できるように`CSocket::OnMessagePending`ユーザーの操作を処理するには時間のかかる同期アクティビティです。

この説明の残りの部分は、16 ビットのオペレーティング システムを対象とするプログラマにとっては。

通常、使用する場合`CAsyncSocket`、ブロック操作を使用しないようにし、代わりに非同期的に動作する必要があります。 受信するポイントからの非同期操作で、 **WSAEWOULDBLOCK**呼び出した後のエラー コード`Receive`、まで待機するなど、`OnReceive`に読み取ることができますを通知するメンバー関数が呼び出されますもう一度です。 非同期呼び出しがソケットの適切なコールバック通知関数をなど、呼び出すことで行われた[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)します。

Windows では、下のブロッキング呼び出しが不適切な手法と見なされます。 既定では、 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)非同期呼び出しをサポートしていますとするコールバック通知を使用して自分でブロックを管理する必要があります。 クラス[CSocket](../mfc/reference/csocket-class.md)、一方では同期されます。 Windows メッセージをポンプし、管理するをブロックします。

ブロッキングの詳細については、Windows ソケット仕様を参照してください。 "On"関数の詳細については、次を参照してください。 [Windows ソケット。通知のソケット](../mfc/windows-sockets-socket-notifications.md)と[Windows ソケット。ソケット クラスから派生する](../mfc/windows-sockets-deriving-from-socket-classes.md)します。

詳細については次を参照してください:

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
