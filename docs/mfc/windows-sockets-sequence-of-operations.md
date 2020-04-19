---
title: Windows ソケット:操作の順序
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 0f9fd339fdbdfee9381ea693568f40473c2397e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296515"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows ソケット:操作の順序

この記事は並行してにサーバー ソケットと、クライアント ソケットの操作のシーケンスを説明します。 ソケットを使用しているため`CArchive`オブジェクトは必ずしも[ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)します。

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Stream のソケット通信するための操作のシーケンス

構築する時点まで、`CSocketFile`オブジェクトに、次のシーケンスが (いくつかのパラメーターの違い) の正確な両方の`CAsyncSocket`と`CSocket`します。 その時点のシーケンスは`CSocket`します。 次の表は、クライアントとサーバー間の通信の設定の操作のシーケンスを示しています。

### <a name="setting-up-communication-between-a-server-and-a-client"></a>サーバーとクライアント間の通信の設定

|サーバー|クライアント|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> - または -<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> (または両方)|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> - または -<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> (または両方)|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> - または -<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> - または -<br /><br /> `arOut << dwValue;`6|

1. 場所*に対して*ポート番号です。 参照してください[Windows ソケット。ポートとソケット アドレス](../mfc/windows-sockets-ports-and-socket-addresses.md)ポートの詳細について。

2. クライアントが接続できるように、サーバーは、ポートを常に指定する必要があります。 `Create`呼び出しもアドレスを指定します。 クライアント側で利用可能なポートを使用する MFC を求める既定のパラメーターを使用します。

3. 場所*に対して*ポート番号と*strAddr*はマシンのアドレスまたはインターネット プロトコル (IP) アドレス。

4. マシンのアドレスには、いくつかの形式:「専用」、"microsoft.com"。 IP アドレスは、「番号をドット形式」フォーム「127.54.67.32」を使用します。 `Connect`関数をアドレスがピリオドで区切られた数である (ただし、数が、ネットワーク上の有効なコンピューターであることを確認するのにはチェックされません) かどうかを確認します。 ない場合は、`Connect`他の形式のいずれかのマシン名を前提としています。

5. 呼び出すと`Accept`サーバー側では、新しいソケット オブジェクトへの参照を渡します。 最初に、このオブジェクトを構築する必要がありますが、呼び出さないでください`Create`にします。 注意このソケット オブジェクトがスコープ接続は閉じられますがなくなるとします。 MFC の新しいオブジェクトへの接続、**ソケット**を処理します。 ソケットに示すように、スタックまたはヒープを構築することができます。

6. スコープ外に出るときに、アーカイブ、ソケット ファイルは閉じられます。 ソケット オブジェクトのデストラクターを呼び出すことも、[閉じる](../mfc/reference/casyncsocket-class.md#close)ソケット オブジェクト、オブジェクトがスコープ外になるか、削除するときのメンバー関数。

## <a name="additional-notes-about-the-sequence"></a>シーケンスに関するその他のメモ

上記の表に示すように呼び出しのシーケンスは、ストリーム ソケットによってです。 コネクションレス型は、データグラム ソケットは、必要としない、[不要なため](../mfc/reference/casyncsocket-class.md#connect)、[リッスン](../mfc/reference/casyncsocket-class.md#listen)、および[Accept](../mfc/reference/casyncsocket-class.md#accept)呼び出し (を使用できますが、必要に応じて`Connect`). 代わりに、クラスを使用している場合`CAsyncSocket`、データグラム ソケットの使用、`CAsyncSocket::SendTo`と`ReceiveFrom`メンバー関数。 (を使用する場合`Connect`を使用するデータグラム ソケットで`Send`と`Receive`)。`CArchive`は機能しません、データグラムを使用しないでください`CSocket`データグラム ソケットの場合、アーカイブします。

[CSocketFile](../mfc/reference/csocketfile-class.md)すべてのサポートされない`CFile`の機能です。`CFile`などメンバー`Seek`をすることは意味ソケット通信では使用できません。 このため、一部の既定設定 MFC`Serialize`関数と互換性がない`CSocketFile`します。 これは特に、`CEditView`クラス。 シリアル化しないでください`CEditView`を使用してデータを`CArchive`オブジェクトにアタッチされて、`CSocketFile`オブジェクトを使用して`CEditView::SerializeRaw`; を使用して、`CEditView::Serialize`代わりに (文書化されていません)。 [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw)関数に必要なファイル オブジェクトなど、関数に`Seek`、その`CSocketFile`はサポートしていません。

詳細については次を参照してください:

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: ポートとソケット アドレス](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket クラス](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)
