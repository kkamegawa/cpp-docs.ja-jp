---
title: Windows ソケット:アーカイブを使用するソケットの例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 4ea1e2911b156066360da09993fa7302db79f12b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305295"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows ソケット:アーカイブを使用するソケットの例

この記事では、クラスを使用する例を示します[CSocket](../mfc/reference/csocket-class.md)します。 この例では`CArchive`ソケットを使用してデータをシリアル化されるオブジェクト。 このドキュメントのシリアル化する、またはファイルからではないことに注意してください。

次の例を使用してデータを送受信する、アーカイブの使用方法を示します`CSocket`オブジェクト。 例では、アプリケーション (同じコンピューター上またはネットワーク上の異なるコンピューター上) の 2 つのインスタンスがデータを交換できるように設計されています。 1 つのインスタンスでは、データは、もう一方のインスタンスの受信と受信確認を送信します。 どちらのアプリケーション データ交換を開始でき、サーバーまたは他のアプリケーションへのクライアントとして動作いずれかのことができます。 次の関数は、アプリケーションのビュー クラスで定義されます。

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

この例に関する最も重要な点は、その構造が似て、MFC の`Serialize`関数。 `PacketSerialize`メンバー関数から成る、**場合**ステートメントを**他**句。 2 つ、関数が受け取った[CArchive](../mfc/reference/carchive-class.md)パラメーターとして参照: *arData*と*arAck*。 場合、 *arData* (送信) を格納するためにアーカイブ オブジェクトが設定されて、**場合**分岐が実行されます。 場合*arData*設定されている (受信) を読み込むため、この関数では、を受け取ります。**他**分岐します。 MFC におけるシリアル化の詳細については、次を参照してください。[シリアル化](../mfc/how-to-make-a-type-safe-collection.md)します。

> [!NOTE]
>  *ArAck*アーカイブ オブジェクトの反対と見なされます*arData*します。 場合*arData*を送信するは*arAck*を受け取ると、その逆は true です。

関数の例は、送信するための指定した回数だけ、デモンストレーション用のランダム データを生成するたびにループします。 アプリケーションは、ファイルなどのいくつかのソースから実際のデータを入手します。 *ArData*アーカイブの挿入演算子 (**<<**) 次の 3 つのデータ ストリームを送信するために使用します。

- "Header"データの性質を指定する (この例では、値で、 *bValue*変数とコピーの数が送信されます)。

   両方の項目は、この例ではランダムに生成されます。

- データのコピーの指定した数。

   内部**の**ループ送信*bValue*指定された回数。

- 文字列と呼ばれる*strText*受信側がそのユーザーに表示します。

受信、関数の動作同様に、点 (**>>**) アーカイブからデータを取得します。 受信側アプリケーションでは、表示する送信元アプリケーションのデータを受け取る、最終の「受信」メッセージを表示し、「送信済み」というメッセージを送り返しますを検証します。

「受信」という単語でこの通信モデルでは、メッセージで送信、 *strText*変数は、データのパケット数がされていることを受信側ユーザーを指定するため、通信のもう一方の端に表示が受信したとします。 受信側は、元の送信者の画面に"Sent"、表示するための質問のような文字列で応答します。 両方の文字列の確認メッセージは、正常な通信が発生したことを示します。

> [!CAUTION]
>  確立された (非 MFC) サーバーとの通信に MFC クライアント プログラムを記述する場合は、アーカイブから C++ オブジェクトを送信しません。 サーバーは、送信するオブジェクトの種類を認識する MFC アプリケーションでない限りは、受信し、オブジェクトを逆シリアル化することはできません。 この記事の例[Windows ソケット。バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)この種類の通信を示しています。

詳細については、Windows ソケット仕様を参照してください: **htonl**、 **htons**、 **ntohl**、 **ntohs**します。 また、詳細については、次のように表示します。

- [Windows ソケット: ソケット クラスからの派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows ソケット: アーカイブ付きソケットの動作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[ときは](../mfc/reference/carchive-class.md#flush)<br/>
[Cobject::serialize](../mfc/reference/cobject-class.md#serialize)
