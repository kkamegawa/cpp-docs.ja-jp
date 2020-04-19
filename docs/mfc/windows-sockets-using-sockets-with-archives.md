---
title: Windows ソケット:アーカイブ付きソケットの使用
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 71a7ed1f1b67bed157805328679a18ceabf201d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358288"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows ソケット:アーカイブ付きソケットの使用

この記事で説明します、 [CSocket プログラミング モデル](#_core_the_csocket_programming_model)します。 クラス[CSocket](../mfc/reference/csocket-class.md)クラスよりも高いレベルの抽象化のソケットのサポートを提供[CAsyncSocket](../mfc/reference/casyncsocket-class.md)します。 `CSocket` を通じて、MFC ソケット オブジェクトとの間のデータを渡すため、MFC のシリアル化プロトコルのバージョンを使用して[CArchive](../mfc/reference/carchive-class.md)オブジェクト。 `CSocket` (Windows メッセージのバック グラウンド処理の管理) 中にブロックを提供し、へのアクセスを提供`CArchive`、生 API またはクラスのいずれかを使用して自分で行う必要がありますの通信の多くの側面を管理`CAsyncSocket`します。

> [!TIP]
>  クラスを使用して`CSocket`自体より便利なバージョンのとして`CAsyncSocket`は、最もシンプルなプログラミング モデルを使用する`CSocket`で、`CArchive`オブジェクト。

アーカイブ付きソケットの実装の動作方法の詳細については、次を参照してください。 [Windows ソケット。ソケットのアーカイブ動作](../mfc/windows-sockets-how-sockets-with-archives-work.md)します。 コード例は、「 [Windows ソケット。操作のシーケンス](../mfc/windows-sockets-sequence-of-operations.md)と[Windows ソケット。アーカイブを使用するソケットの例](../mfc/windows-sockets-example-of-sockets-using-archives.md)します。 ソケット クラスから独自のクラスを派生することで利用できる一部の機能については、次を参照してください。 [Windows ソケット。ソケット クラスから派生する](../mfc/windows-sockets-deriving-from-socket-classes.md)します。

> [!NOTE]
>  確立された (非 MFC) サーバーとの通信に MFC クライアント プログラムを記述する場合は、アーカイブから C++ オブジェクトを送信しません。 サーバーは、送信するオブジェクトの種類を認識する MFC アプリケーションでない限りが、受信し、オブジェクトを逆シリアル化することはできません。 非 MFC アプリケーションとの通信にあるサブジェクトに関連する素材の資料を参照も[Windows ソケット。バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)します。

##  <a name="_core_the_csocket_programming_model"></a> CSocket のプログラミング モデル

使用して、`CSocket`オブジェクトが作成およびいくつかの MFC クラス オブジェクトの関連付けを行います。 次の一般的な手順では、各ステップがサーバー ソケットと、クライアント ソケット、手順 3. を除く各ソケットの種類が、別のアクションを必要との両方で取得されます。

> [!TIP]
>  実行時に、サーバー アプリケーション通常最初を開始する準備をして、クライアント アプリケーションの接続をシークするときに「リッスン」します。 クライアントが接続を試みると、サーバーが準備されていない場合は、通常は後でもう一度接続を試みるユーザー アプリケーションが必要です。

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>サーバー ソケットと、クライアント ソケットの間の通信を設定するには

1. 構築、 [CSocket](../mfc/reference/csocket-class.md)オブジェクト。

1. オブジェクトを使用して作成する、基になる**ソケット**を処理します。

   `CSocket`クライアント オブジェクト、通常、既定のパラメーターを使用する必要があります[作成](../mfc/reference/casyncsocket-class.md#create)データグラム ソケットを作成する必要がある場合を除き、します。 `CSocket`サーバー オブジェクト内のポートを指定する必要があります、`Create`呼び出します。

    > [!NOTE]
    >  `CArchive` データグラム ソケットでは機能しません。 使用する場合`CSocket`使用する場合と、データグラム ソケットに対してクラスを使用する必要があります`CAsyncSocket`、つまり、アーカイブせずにします。 データグラムの信頼性がないため、(必ず到着して、繰り返される可能性がありますいない、または誤った順序)、アーカイブをシリアル化と互換性がありません。 シリアル化操作が確実、かつシーケンス内に完了するはずです。 使用しようとする場合`CSocket`で、 `CArchive` MFC アサーションが失敗するのデータグラムのオブジェクトします。

1. ソケットがクライアントの場合は、呼び出す[不要なため](../mfc/reference/casyncsocket-class.md#connect)サーバー ソケットにソケット オブジェクトを接続します。

     - または -

   ソケットがサーバーの場合は、呼び出す[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)を開始する試行をクライアントから接続をリッスンします。 接続要求を受信すると呼び出すことで同意[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)します。

    > [!NOTE]
    >  `Accept`メンバー関数は、新しい空への参照を受け取ります`CSocket`オブジェクトをパラメーターとして。 呼び出す前に、このオブジェクトを構築する必要があります`Accept`します。 このソケット オブジェクトがスコープ外になった場合、接続が閉じられます。 呼び出さない`Create`この新しいソケット オブジェクト。

1. 作成、 [CSocketFile](../mfc/reference/csocketfile-class.md)オブジェクト、関連付け、`CSocket`られてオブジェクト。

1. 作成、 [CArchive](../mfc/reference/carchive-class.md)読み込み (受信) または (送信) データを格納するオブジェクト。 アーカイブが関連付けられている、`CSocketFile`オブジェクト。

   注意`CArchive`データグラム ソケットでは機能しません。

1. 使用して、`CArchive`クライアントとサーバー ソケットの間でデータを渡すオブジェクト。

   注意を指定した`CArchive`オブジェクトでは、一方向のみのデータを移動: 読み込み (受信) または格納 (送信) のいずれか。 場合によっては、2 つの使用は`CArchive`オブジェクト: 受信確認を受信するため、その他のデータを送信するための 1 つ。

   接続を受け入れると、archive の設定、パスワードの検証などのタスクを実行できます。

1. アーカイブ、ソケット ファイル、およびソケット オブジェクトを破棄します。

    > [!NOTE]
    >  クラス`CArchive`提供、`IsBufferEmpty`クラスを使用して専用のメンバー関数`CSocket`します。 バッファーにデータの複数のメッセージが含まれている場合は、それらのすべてが読み取られ、バッファーをクリアするまでループする必要があります。 それ以外の場合、次の通知を受信するデータが含まれる遅れる可能性があります無期限にします。 使用`IsBufferEmpty`すべてのデータを取得することを保証するためにします。

この記事[Windows ソケット。操作のシーケンス](../mfc/windows-sockets-sequence-of-operations.md)両方の側のコード例では、このプロセスを示しています。

詳細については次を参照してください:

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Create](../mfc/reference/csocket-class.md#create)
