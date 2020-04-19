---
title: Windows ソケット:Casyncsocket クラス
ms.date: 11/04/2016
f1_keywords:
- CAsyncSocket
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 51274791393d95517bd8de5ae7248dc634018037
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399565"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows ソケット:Casyncsocket クラス

この記事では、クラスを使用する方法を説明します。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)します。 このクラスには、非常に低いレベルで Windows ソケット API がカプセル化してあります。 `CAsyncSocket` ネットワーク通信の詳細を把握するけれども、ネットワーク イベントの通知のコールバックをするプログラマが使用されます。 この前提に基づき、この記事では、基本的な命令のみです。 使用を検討する必要がありますおそらく`CAsyncSocket`Windows ソケットの MFC アプリケーションで複数のネットワーク プロトコルを扱うさが柔軟性を犠牲したくない場合。 クラスの別の一般的なモデルを使用するよりも自分で可能性が直接、複数の通信をプログラミングの効率が向上を取得することができますを感じることがあるも`CSocket`します。

`CAsyncSocket` 記載されていますが、 *MFC リファレンス*します。 Visual C では、Windows SDK には、Windows ソケット仕様も提供します。 詳細に残されます。 Visual C からのサンプル アプリケーションは提供されません`CAsyncSocket`します。

高度なネットワーク通信について知識ではなく、かつ、簡単な方法の場合は、クラスを使用して[CSocket](../mfc/reference/csocket-class.md)で、`CArchive`オブジェクト。 参照してください[Windows ソケット。アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)詳細についてはします。

この記事では次の内容について説明します。

- 作成と使用、`CAsyncSocket`オブジェクト。

- [お客様の責任で CAsyncSocket](#_core_your_responsibilities_with_casyncsocket)します。

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> CAsyncSocket オブジェクトの作成と

#### <a name="to-use-casyncsocket"></a>CAsyncSocket を使用するには

1. 構築、 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)オブジェクトおよびオブジェクトを使用して作成する、基になる**ソケット**を処理します。

   ソケットの作成では、2 段階の構築の MFC のパターンに従います。

   例:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     - または -

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上記の最初のコンス トラクターを作成、`CAsyncSocket`スタック上のオブジェクト。 2 番目のコンス トラクターを作成、`CAsyncSocket`ヒープにします。 最初の[作成](../mfc/reference/casyncsocket-class.md#create)上記の呼び出しでは、既定のパラメーターを使用して、ストリーム ソケットを作成します。 2 番目の`Create`呼び出しは、指定したポートとアドレスを持つデータグラム ソケットを作成します。 (いずれかを使用する`Create`いずれかの構築方法とバージョン)。

   パラメーターを`Create`は。

   - 「ポート」: 短整数。

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - ソケットの種類:**SOCK_STREAM** (既定値) または**SOCK_DGRAM**します。

   - ソケットの"address"「専用」や「128.56.22.8」など。

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

   用語"port"および「ソケット アドレス」で説明[Windows ソケット。ポートとソケット アドレス](../mfc/windows-sockets-ports-and-socket-addresses.md)します。

1. ソケットがクライアントの場合は、ソケット オブジェクトをサーバーに接続を使用して、ソケット[不要なため](../mfc/reference/casyncsocket-class.md#connect)します。

     - または -

   ソケットがサーバーの場合は、設定、ソケットのリッスンを開始 (で[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) のクライアントからの接続試行します。 接続要求を受信するでそのまま使用[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)します。

   接続を受け入れた後には、パスワードの検証などのタスクを実行できます。

    > [!NOTE]
    >  `Accept`メンバー関数は、新しい空への参照を受け取ります`CSocket`オブジェクトをパラメーターとして。 呼び出す前に、このオブジェクトを構築する必要があります`Accept`します。 このソケット オブジェクトがスコープ外になった場合、接続が閉じられます。 呼び出さない`Create`この新しいソケット オブジェクト。 例については、この記事を参照してください。 [Windows ソケット。操作のシーケンス](../mfc/windows-sockets-sequence-of-operations.md)します。

1. 呼び出すことによって、他のソケットとの通信を実行、 `CAsyncSocket` Windows ソケット API 関数をカプセル化するオブジェクトのメンバー関数。

   Windows ソケット仕様とクラスを参照してください[CAsyncSocket](../mfc/reference/casyncsocket-class.md)で、 *MFC リファレンス*します。

1. 破棄、`CAsyncSocket`オブジェクト。

   スタック上にソケット オブジェクトを作成する場合は、関数スコープから外れたときにデストラクターが呼び出されます。 使用して、ヒープ上のソケット オブジェクトを作成した場合、**新しい**演算子を使用して責任を負いますが、**削除**オブジェクトを破棄する演算子。

   デストラクターは、オブジェクトの[閉じる](../mfc/reference/casyncsocket-class.md#close)メンバー関数は、オブジェクトを破棄します。

コードでは、このシーケンスの例については (実際の`CSocket`オブジェクト) を参照してください[Windows ソケット。操作のシーケンス](../mfc/windows-sockets-sequence-of-operations.md)します。

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> CAsyncSocket でお客様の責任

クラスのオブジェクトを作成するときに[CAsyncSocket](../mfc/reference/casyncsocket-class.md)、オブジェクトには、Windows がカプセル化**ソケット**を処理し、そのハンドルに対する操作を提供します。 使用すると`CAsyncSocket`API を直接使用する場合に発生する可能性がありますすべての問題に対処する必要があります。 例えば:

- シナリオの「ブロック」されます。

- 送信側と受信のマシン間のバイト順序の違い

- Unicode とマルチバイト文字の間の変換 (MBCS) 文字列を設定します。

これらの条項および情報の追加の定義は、次を参照してください。 [Windows ソケット。ブロック](../mfc/windows-sockets-blocking.md)、 [Windows ソケット。バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)、 [Windows ソケット。文字列を変換する](../mfc/windows-sockets-converting-strings.md)します。

これらの問題に関係なくクラス`CAsycnSocket`場合があります、最適な選択肢をアプリケーションで必要なすべての柔軟性と制御を取得できます。 クラスの使用を検討する必要がありますそうでない場合`CSocket`代わりにします。 `CSocket` 多くのユーザーからの詳細を非表示になります: Windows がブロックされた呼び出し中にメッセージが表示され、ポンプへのアクセスを it `CArchive`、バイト順序の相違点と文字列変換を管理します。

詳細については次を参照してください:

- [Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
