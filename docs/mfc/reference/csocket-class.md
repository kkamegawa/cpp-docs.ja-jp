---
title: CSocket クラス
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323961"
---
# <a name="csocket-class"></a>CSocket クラス

派生した`CAsyncSocket`、Windows ソケット API のカプセル化を継承しより高い抽象化レベルを表す、`CAsyncSocket`オブジェクト。

## <a name="syntax"></a>構文

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|`CSocket` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Csocket::attach](#attach)|ソケットのハンドルをアタッチ、`CSocket`オブジェクト。|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|現在進行中というブロッキング呼び出しをキャンセルします。|
|[CSocket::Create](#create)|ソケットが作成されます。|
|[CSocket::FromHandle](#fromhandle)|ポインターを返します、`CSocket`オブジェクト、ソケット ハンドルを指定します。|
|[CSocket::IsBlocking](#isblocking)|ブロック呼び出しが進行中かどうかを判断します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|ブロッキング呼び出しが完了するを待機中には、保留中のメッセージの処理と呼ばれます。|

## <a name="remarks"></a>Remarks

`CSocket` クラスと連携`CSocketFile`と`CArchive`データの送受信を管理します。

A`CSocket`オブジェクトも用意されています、ブロックの同期操作に不可欠である`CArchive`します。 など、機能をブロックしている`Receive`、 `Send`、 `ReceiveFrom`、 `SendTo`、および`Accept`(から継承されたすべて`CAsyncSocket`)、返されない、`WSAEWOULDBLOCK`でエラー`CSocket`します。 代わりに、これらの関数は、操作が完了するまで待機します。 場合に、元の呼び出しが WSAEINTR エラーで終了するさらに、`CancelBlockingCall`がブロックしてこれらの関数のいずれかの中に呼び出されます。

使用する、 `CSocket` 、コンス トラクターを呼び出すオブジェクトを呼び出して`Create`基になるソケット ハンドル (ソケットの種類) を作成します。 既定のパラメーターの`Create`ストリーム ソケットを作成、ソケットを使用していない場合は、`CArchive`オブジェクト、データグラム ソケットを作成する代わりに、またはサーバー ソケットを作成するのには特定のポートにバインドするパラメーターを指定することができます。 使用して、クライアント ソケット接続`Connect`クライアント側と`Accept`サーバー側でします。 作成し、`CSocketFile`オブジェクトし、関連付けることを`CSocket`オブジェクト、`CSocketFile`コンス トラクター。 次に、作成、`CArchive`を送信するためのオブジェクトと (必要に応じて) データを受信するための 1 つ関連付けるし、使用して、`CSocketFile`オブジェクト、`CArchive`コンス トラクター。 通信が完了したら、破棄、 `CArchive`、 `CSocketFile`、および`CSocket`オブジェクト。 ソケットのデータ型が、情報の記事で説明されている[Windows ソケット。バック グラウンド](../../mfc/windows-sockets-background.md)します。

使用すると`CArchive`で`CSocketFile`と`CSocket`、状況が発生する可能性があります、`CSocket::Receive`ループに入る (によって`PumpMessages(FD_READ)`) バイトの要求された時間待機しています。 これは Windows sockets FD_READ 通知ごとに 1 つだけ受信呼び出しを許可するためですが、`CSocketFile`と`CSocket`FD_READ ごとの複数の受信呼び出しを許可します。 読み取るデータがない場合に、FD_READ が発生した場合、アプリケーションがハングします。 別の FD_READ 取得しない場合、アプリケーションはソケット通信を停止します。

次のように、この問題を解決できます。 `OnReceive`メソッドを呼び出し、socket クラスの`CAsyncSocket::IOCtl(FIONREAD, ...)`を呼び出す前に、`Serialize`ソケットから読み取ることが予想されるデータが 1 つの TCP パケットのネットワークのメディア (最大転送単位のサイズを超えるとメッセージ クラスのメソッド、通常は、少なくとも 1096 バイト)。 使用可能なデータのサイズが小さいと、必要以上の場合は、すべてのデータを受信して、読み取り操作を開始してから、待機します。

次の例では、`m_dwExpected`は、ユーザーが受信するバイトのおおよその数です。 宣言している他の場所で、コードと見なされます。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  静的にリンクされた MFC アプリケーションでセカンダリ スレッドで MFC ソケットを使用する場合を呼び出す必要があります`AfxSocketInit`ソケット ライブラリを初期化するためにソケットを使用する各スレッドにします。 既定では、`AfxSocketInit`は、プライマリ スレッドでのみ呼び出されます。

詳細については、次を参照してください。 [MFC における Windows ソケット](../../mfc/windows-sockets-in-mfc.md)、 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)、 [Windows ソケット。ソケットのアーカイブ動作](../../mfc/windows-sockets-how-sockets-with-archives-work.md)、 [Windows ソケット。操作のシーケンス](../../mfc/windows-sockets-sequence-of-operations.md)、 [Windows ソケット。アーカイブを使用するソケットの例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

アタッチするには、このメンバー関数を呼び出す、`hSocket`へのハンドルを`CSocket`オブジェクト。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>パラメーター

*hSocket*<br/>
ソケットへのハンドルが含まれています。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。

### <a name="remarks"></a>Remarks

ソケットのハンドルがオブジェクトに格納されている[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)データ メンバー。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

現在進行中のブロッキング呼び出しをキャンセルするには、このメンバー関数を呼び出します。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Remarks

この関数は、このソケットに対する未処理のブロッキング操作をキャンセルします。 元のブロックの呼び出しは、できるだけ早く WSAEINTR エラーで終了します。

ブロッキング`Connect`操作、Windows ソケットの実装が終了ブロック呼び出しが、不可能になるソケット リソースは、接続が完了した (および、リセットされました) までにリリースされるとすぐに、またはタイムアウトしました。これは、アプリケーションは、新しいソケット (使用可能なソケットがない場合) を開くか、同じピアに接続するためにすぐにしようとする場合にのみある可能性があります。

以外のすべての操作をキャンセル`Accept`不定状態で、ソケットのままにできます。 アプリケーションが確実に実行できることに依存できる唯一の操作への呼び出しは、アプリケーションでは、ソケットでのブロッキング操作をキャンセルした場合`Close`、一部の Windows Sockets 実装でその他の操作に使用することがあります。 最大の移植性を必要に応じて、アプリケーションの場合は、キャンセル後の操作の実行に依存しないように注意する必要があります。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

##  <a name="create"></a>  CSocket::Create

呼び出す、**作成**Windows ソケットを作成し、アタッチするソケット オブジェクトを構築した後、メンバー関数。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>パラメーター

*nSocketPort*<br/>
Mfc でポートを選択する場合、ソケットまたは 0 で使用する特定のポート。

*nSocketType*<br/>
SOCK_STREAM または SOCK_DGRAM します。

*lpszSocketAddress*<br/>
接続のソケットでは、「128.56.22.8」などのピリオドで区切られた数のネットワーク アドレスを含む文字列へのポインター。 このパラメーターに文字列、NULL が渡される、`CSocket`インスタンスがすべてのネットワーク インターフェイス上のクライアント アクティビティを待機する必要があります。

### <a name="return-value"></a>戻り値

関数が成功した場合、0 以外の場合0、および特定のエラー コードを呼び出すことによって取得されるそれ以外の場合`GetLastError`します。

### <a name="remarks"></a>Remarks

`Create` 呼び出して`Bind`指定のアドレスにソケットをバインドします。 次の種類のソケットがサポートされています。

- SOCK_STREAM に、シーケンス処理、信頼性の高い双方向の接続ベースのバイト ストリームを提供します。 インターネット アドレス ファミリの伝送制御プロトコル (TCP) を使用します。

- SOCK_DGRAM サポート データグラムには、固定 (通常は短い) 最大長のコネクションレスで信頼性の低いのバッファーします。 インターネット アドレス ファミリには、ユーザー データグラム プロトコル (UDP) を使用します。 このオプションを使用する、ソケットを使用する必要がありますいないを`CArchive`オブジェクト。

    > [!NOTE]
    >  `Accept`メンバー関数は、新しい空への参照を受け取ります`CSocket`オブジェクトをパラメーターとして。 呼び出す前に、このオブジェクトを構築する必要があります`Accept`します。 注意このソケット オブジェクトがスコープ接続は閉じられますがなくなるとします。 呼び出さない`Create`この新しいソケット オブジェクト。

ストリームとデータグラム ソケットの詳細については、記事をご覧ください。 [Windows ソケット。バック グラウンド](../../mfc/windows-sockets-background.md)、 [Windows ソケット。ポートとソケット アドレス](../../mfc/windows-sockets-ports-and-socket-addresses.md)、および[Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

##  <a name="csocket"></a>  CSocket::CSocket

`CSocket` オブジェクトを構築します。

```
CSocket();
```

### <a name="remarks"></a>Remarks

呼び出す必要があります、作成した後、`Create`メンバー関数。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

##  <a name="fromhandle"></a>  CSocket::FromHandle

ポインターを返します、`CSocket`オブジェクト。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>パラメーター

*hSocket*<br/>
ソケットへのハンドルが含まれています。

### <a name="return-value"></a>戻り値

ポインター、`CSocket`がある場合は NULL またはありません`CSocket`オブジェクトに関連付けられて*hSocket*。

### <a name="remarks"></a>Remarks

場合、ソケット ハンドルが指定されると、`CSocket`オブジェクトがハンドルに関連付けられていない場合、メンバー関数は、NULL が返され、一時オブジェクトは作成されません。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

##  <a name="isblocking"></a>  CSocket::IsBlocking

ブロック呼び出しが進行中かを判断するには、このメンバー関数を呼び出します。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>戻り値

ソケットがブロッキングされている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

Windows から特定のメッセージを検索し、ソケットで対処するには、このメンバー関数をオーバーライドします。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>戻り値

メッセージが処理された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

これは、高度なオーバーライド可能な。

Framework 呼び出し`OnMessagePending`ソケットは、アプリケーションに関心のあるメッセージを処理する機会を提供する Windows メッセージをポンプが中にします。 使用する方法の例については`OnMessagePending`、記事をご覧ください[Windows ソケット。ソケット クラスから派生する](../../mfc/windows-sockets-deriving-from-socket-classes.md)します。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../../mfc/windows-sockets-using-sockets-with-archives.md)します。

## <a name="see-also"></a>関連項目

[CAsyncSocket クラス](../../mfc/reference/casyncsocket-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket クラス](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile クラス](../../mfc/reference/csocketfile-class.md)
