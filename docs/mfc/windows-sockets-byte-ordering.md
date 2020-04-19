---
title: Windows ソケット:バイトの順序付け
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: ca572ad32a9a46756cacf0221d80b2953b710723
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217572"
---
# <a name="windows-sockets-byte-ordering"></a>Windows ソケット:バイトの順序付け

この記事と関連記事では 2 つは、Windows ソケット プログラミングのいくつかの問題を説明します。 この記事では、バイトの順序付けについて説明します。 記事では、その他の問題がについて説明します。[Windows ソケット: ブロック](../mfc/windows-sockets-blocking.md)と[Windows ソケット。文字列を変換する](../mfc/windows-sockets-converting-strings.md)します。

使用するか、またはクラスから派生させる場合[CAsyncSocket](../mfc/reference/casyncsocket-class.md)、これらの問題を自分で管理する必要があります。 使用するか、またはクラスから派生させる場合[CSocket](../mfc/reference/csocket-class.md)MFC を管理します。

## <a name="byte-ordering"></a>バイトの順序付け

異なるマシン アーキテクチャは、場合によって異なるバイト順を使用してデータを格納します。 たとえば、Intel ベースのマシンは、Macintosh (Motorola) マシンの逆の順序でデータを格納します。 「リトル エンディアン、」と呼ばれる、Intel のバイト順は、ネットワークの標準的な「ビッグ エンディアン」順の逆でもです。 次の表では、これらの用語について説明します。

### <a name="big--and-little-endian-byte-ordering"></a>ビッグ エンディアンとリトル エンディアン バイト順

|バイトの順序付け|説明|
|-------------------|-------------|
|ビッグ エンディアン|単語の左の端が最上位バイトです。|
|リトル エンディアン|単語の右端の位置が最上位バイトです。|

通常、ネットワーク経由で送受信するデータの変換でバイト順について心配する必要はありませんが、バイト順を変換する必要があります状況があります。

## <a name="when-you-must-convert-byte-orders"></a>バイト オーダーを変換する際にする必要があります。

次の状況でバイト順を変換する必要があります。

- 別のコンピューターに送信するデータではなく、ネットワークによって解釈される必要がある情報を渡しています。 たとえば、渡すような場合のポートとアドレスで、ネットワークを理解する必要があります。

- 接続しているサーバー アプリケーションは、MFC アプリケーションではない (とは、ソース コードはありません)。 これは、2 つのマシンは同じバイト順序の基準を共有していない場合場合に、バイト順の変換に対して呼び出されます。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>バイト順の変換があるない場合

次の状況でバイト順を変換する作業を回避できます。

- 両方の end にあるマシンがスワップ (バイト単位) が同意でき、両方のマシンが同じバイト順を使用します。

- 通信しているサーバーは、MFC アプリケーションです。

- 使用すると、通信しているサーバーのソース コードがあるように設定できる明示的にかどうかどうか、バイト順を変換する必要があります。

- MFC にサーバーを移植することができます。 これはかなり簡単な方法と、結果が小さく、高速のコードでは、通常は。

操作[CAsyncSocket](../mfc/reference/casyncsocket-class.md)、すべてのバイト順のために必要な変換を自分で管理する必要があります。 Windows ソケットは、「ビッグ エンディアン」のバイト順のモデルを標準化し、この注文とその他のユーザー間で変換する関数を提供します。 [CArchive](../mfc/reference/carchive-class.md)、ただし、これと共に使用する[CSocket](../mfc/reference/csocket-class.md)、(「リトル エンディアン」) の逆の順序を使用して、`CArchive`バイト オーダー変換のための詳細を行います。 このアプリケーションで標準的な順序または Windows Sockets バイト順の変換関数を使用してを使用して行うことができます、コード移植性を高くします。

MFC ソケットの理想的な使用状況は、通信の両端を自分で作成し、両端で MFC を使用する場合です。 バイトのスワッピング アーカイブされたデータを渡す前に管理する必要があります、FTP サーバーなどの非 MFC アプリケーションと通信するアプリケーションを作成する場合は、Windows Sockets 変換ルーチンを使用して**ntohs**、 **ntohl**、 **htons**、および**htonl**します。 非 MFC アプリケーションとの通信で使用されるこれらの関数の例は、この記事の後半で表示されます。

> [!NOTE]
>  通信の他方の end は、MFC アプリケーションではないと、も回避しなければならないから派生した C++ オブジェクトのストリーミング`CObject`アーカイブに、受信側がそれらを処理できないためです。 注を参照してください[Windows ソケット。アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)します。

バイト オーダーに関する詳細については、Windows SDK で利用できる Windows ソケット仕様を参照してください。

## <a name="a-byte-order-conversion-example"></a>バイト順の変換例

次の例のシリアル化の関数を示しています、`CSocket`アーカイブを使用するオブジェクト。 Windows ソケット API では、バイト順の変換関数を使用しても示します。

この例は、非 MFC サーバー アプリケーションがあるないソース コードへのアクセスと通信するクライアントを作成するシナリオを紹介します。 このシナリオでは、非 MFC サーバーが標準的なネットワークのバイト順を使用すると想定する必要があります。 MFC クライアント アプリケーションを使用してこれに対し、`CArchive`オブジェクトを`CSocket`オブジェクト、および`CArchive`「リトル エンディアン」のバイト順を逆の標準のネットワークを使用します。

非 MFC サーバーと通信するが、次のようなメッセージ パケットのプロトコルが設定されているとします。

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

MFC には、これはするように表現。

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

C++ を**構造体**クラスとして基本的に同じです。 `Message`構造がなどのメンバー関数を持つことができます、`Serialize`上で宣言されたメンバー関数。 `Serialize`メンバー関数は次のようになります。

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

一方の end に非 MFC サーバー アプリケーションのバイトの順序付けの間にクリアの不一致があるため、データのバイト順の変換の例では、`CArchive`もう一方の end の MFC クライアント アプリケーションで使用します。 この例は、Windows ソケットを提供する変換関数でバイト順のいくつかを示します。 次の表では、これらの関数について説明します。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows ソケットのバイト順の変換関数

|関数|目的|
|--------------|-------------|
|**ntohs**|16 ビットの値をネットワークのバイト順からホストのバイト順 (ビッグ エンディアン リトル エンディアンに) 変換します。|
|**ntohl**|32 ビットの値をネットワークのバイト順からホストのバイト順 (ビッグ エンディアン リトル エンディアンに) 変換します。|
|**Htons**|16 ビットの値をホストのバイト順からネットワークのバイト順 (リトル エンディアン ビッグ エンディアンに) 変換します。|
|**Htonl**|32 ビットの値をホストのバイト順からネットワークのバイト順 (リトル エンディアン ビッグ エンディアンに) 変換します。|

この例の別のポイントは、通信のもう一方の端のソケット アプリケーションは、非 MFC アプリケーションが、しないことをする必要があります、次のような何かを示します。

`ar << pMsg;`

場所`pMsg`クラスから派生した C++ オブジェクトへのポインターは、`CObject`します。 MFC アプリケーションがある場合と、オブジェクトと、サーバーに関連付けられている追加の MFC 情報を理解できない送信されます。

詳細については次を参照してください:

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
