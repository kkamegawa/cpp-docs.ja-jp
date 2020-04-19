---
title: Windows ソケット:アーカイブ付きソケットのしくみ
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: 3af94bc881276238f1a8d2dbeeee4dca1f173a4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389456"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows ソケット:アーカイブ付きソケットのしくみ

この記事で説明する方法、 [CSocket](../mfc/reference/csocket-class.md)オブジェクト、 [CSocketFile](../mfc/reference/csocketfile-class.md)オブジェクト、および[CArchive](../mfc/reference/carchive-class.md)オブジェクトが結合され、Windows を使用してデータの送受信を簡略化ソケット。

この記事[Windows ソケット。アーカイブを使用するソケットの例](../mfc/windows-sockets-example-of-sockets-using-archives.md)提示、`PacketSerialize`関数。 アーカイブのオブジェクト、`PacketSerialize`例は、MFC に渡されるアーカイブ オブジェクトと同様、動作[Serialize](../mfc/reference/cobject-class.md#serialize)関数。 重要な違いは、ソケットのアーカイブが接続されている標準[CFile](../mfc/reference/cfile-class.md) (通常はディスク ファイルに関連付けられている) オブジェクトには、`CSocketFile`オブジェクト。 ディスク ファイルへの接続ではなく、`CSocketFile`オブジェクトの接続先を`CSocket`オブジェクト。

A`CArchive`オブジェクトは、バッファーを管理します。 格納 (送信) アーカイブのバッファーがいっぱいのとき、関連付けられている`CFile`オブジェクトは、バッファーの内容を書き込みます。 ソケットにアタッチされているアーカイブのバッファーのフラッシュは、メッセージの送信と同じです。 読み込み (受信) アーカイブのバッファーがいっぱいで、ときに、`CFile`バッファーが再び使用可能になるまで、オブジェクトが読み取りを停止します。

クラス`CSocketFile`から派生`CFile`、サポートされていませんが、 [CFile](../mfc/reference/cfile-class.md)ポジショニング関数などのメンバー関数 (`Seek`、 `GetLength`、`SetLength`など)、(を関数のロック`LockRange`、 `UnlockRange`)、または`GetPosition`関数。 すべて、 [CSocketFile](../mfc/reference/csocketfile-class.md)オブジェクトを実行する必要がありますが、書き込みまたは読み取りとの間、関連付けられているバイトのシーケンス`CSocket`オブジェクト。 ファイルが含まれていないためなどの操作`Seek`と`GetPosition`意味がありません。 `CSocketFile` 派生`CFile`ので、すべてこれらのメンバー関数の継承は通常、します。 これを防ぐため、サポートされていない`CFile`メンバー関数がでオーバーライドされる`CSocketFile`をスローする、 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)します。

`CSocketFile`オブジェクトは、メンバーの関数を呼び出してその`CSocket`データ送信または受信するオブジェクト。

次の図は、通信の両方の側でこれらのオブジェクト間の関係を示します。

![CArchive、csocketfile、CSocket](../mfc/media/vc38ia1.gif "CArchive、csocketfile、CSocket") <br/>
CArchive、CSocketFile、CSocket

この上の複雑さでは、ソケットの詳細情報を自分で管理する必要があることからも保護します。 ソケット、ファイル、およびアーカイブを作成してアーカイブへの挿入またはアーカイブからデータを抽出してデータを送信または受信を開始します。 [CArchive](../mfc/reference/carchive-class.md)、 [CSocketFile](../mfc/reference/csocketfile-class.md)、および[CSocket](../mfc/reference/csocket-class.md)バック グラウンドで詳細を管理します。

A`CSocket`オブジェクトは、実際には 2 つの状態のオブジェクト: 非同期 (通常の状態) と同期します。 非同期の状態でソケットは、framework から非同期の通知を受信できます。 ただし、受信または送信データなどの操作中に、ソケット同期状態になります。 これは、同期操作が完了するまで、ソケットの非同期通知を受信することを意味します。 モードを切り替えることので行うことができます、たとえば、次のようなもの。

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

場合`CSocket`実装されなかった、2 つの状態オブジェクトとして、前の通知を処理していたときに、同じ種類のイベントの追加の通知を受信することができる場合があります。 たとえば、取得する可能性があります、`OnReceive`通知の処理中に、`OnReceive`します。 上記のコード フラグメントで抽出`str`アーカイブからは、再帰で生じる可能性があります。 状態を切り替えることで`CSocket`追加の通知を防止することで再帰を防止します。 一般的な規則には、通知内での通知はありません。

> [!NOTE]
> A`CSocketFile`なし (制限あり) ファイルとしても使用できます、`CArchive`オブジェクト。 既定で、`CSocketFile`コンス トラクターの*で*パラメーターが**TRUE**します。 これは、アーカイブと使用のファイル オブジェクトであることを指定します。 アーカイブせず、ファイル オブジェクトを使用するには、渡す**FALSE**で、*で*パラメーター。

その「アーカイブ互換性のある」モードで、`CSocketFile`オブジェクト パフォーマンスが向上し、「デッドロック」の危険性は減少 ソケットの送信側と受信側の両方が、互いに待機または一般的なリソースを待機しているときに、デッドロックが発生します。 場合に、このような状況が発生する可能性があります、`CArchive`と協力して、オブジェクト、`CSocketFile`と同様、`CFile`オブジェクト。 `CFile`アーカイブの場合、要求したバイト数、受信ファイルの末尾に達したことを想定できます。 `CSocketFile`、ただし、データは、メッセージ ベース; バッファーは、複数のメッセージを含めることができます、要求されたバイト数よりも少ないのため受信ファイルの終わりを意味しません。 アプリケーションでは、それほどで、ここではブロックされません`CFile`バッファーが空になるまで、バッファーからメッセージの読み取りを続けます。 [時](../mfc/reference/carchive-class.md#isbufferempty)関数`CArchive`はこのような場合、アーカイブのバッファーの状態を監視するために便利です。

詳細については、次を参照してください。 [Windows ソケット。アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[Cobject::serialize](../mfc/reference/cobject-class.md#serialize)
