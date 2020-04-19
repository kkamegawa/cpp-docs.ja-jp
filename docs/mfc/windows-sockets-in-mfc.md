---
title: MFC における Windows ソケット
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510617"
---
# <a name="windows-sockets-in-mfc"></a>MFC における Windows ソケット

> [!NOTE]
>  MFC は Windows Sockets 1 をサポートしますが、 [Windows sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2)はサポートしていません。 Windows Sockets 2 は windows 98 に付属しており、windows 2000 に含まれるバージョンです。

MFC には、Windows ソケットを使用したネットワーク通信プログラムを作成するための2つのモデルが用意されています この記事では、これらのモデルについて説明し、MFC ソケットのサポートについて詳しく説明します。 "Socket" は通信のエンドポイントであり、アプリケーションがネットワーク経由で他の Windows Sockets アプリケーションと通信するために使用されるオブジェクトです。

ソケットの概念の説明など、windows ソケットの詳細については[、「windows sockets:バックグラウンド](../mfc/windows-sockets-background.md)。

##  <a name="_core_sockets_programming_models"></a>ソケットプログラミングモデル

2つの MFC Windows Sockets プログラミングモデルは、次のクラスによってサポートされています。

- `CAsyncSocket`

   このクラスは、Windows Sockets API をカプセル化します。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)は、ネットワークプログラミングについて理解していて、ソケット API に直接プログラミングする柔軟性を必要としているが、ネットワークイベントの通知にコールバック関数の利便性を必要としているプログラマを対象としています。 で使用するためにオブジェクト指向の形式でソケットをC++パッケージ化する以外に、このクラスで提供される唯一の抽象化は、特定のソケット関連の Windows メッセージをコールバックに変換することです。 詳細については[、「Windows Sockets:ソケット通知](../mfc/windows-sockets-socket-notifications.md)。

- `CSocket`

   から`CAsyncSocket`派生したこのクラスは、MFC の[CArchive](../mfc/reference/carchive-class.md)オブジェクトを介してソケットを操作するための、より高いレベルの抽象化を提供します。 アーカイブでソケットを使用することは、MFC のファイルシリアル化プロトコルを使用する場合とよく似ています。 これにより、 `CAsyncSocket`モデルよりも使いやすくなります。 [CSocket](../mfc/reference/csocket-class.md)は、Windows ソケット api `CAsyncSocket`をカプセル化するの多くのメンバー関数を継承します。これらの関数のいくつかを使用し、一般的にソケットプログラミングについて理解する必要があります。 では、未加工の API またはクラス`CAsyncSocket`を使用して自分で行う必要がある通信の多くの側面を管理します。`CSocket` 最も重要な`CSocket`のは、(Windows メッセージをバックグラウンドで処理する) ブロックを提供することです。 `CArchive`これは、の同期操作に不可欠です。

オブジェクトとオブジェクト`CSocket`の`CAsyncSocket`作成と使用に[ついては、「Windows Sockets:アーカイブ](../mfc/windows-sockets-using-sockets-with-archives.md) と[Windows ソケットでのソケットの使用:クラス CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)を使用します。

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows ソケット Dll

Microsoft Windows オペレーティングシステムには、Windows Sockets ダイナミックリンクライブラリ (DLL) が用意されています。 ビジュアルC++には、適切なヘッダーファイルとライブラリ、および Windows ソケット仕様が用意されています。

Windows ソケットの詳細については、次を参照してください。

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: 動作シーケンス](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows ソケット: アーカイブを使用するソケットの例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows ソケット: アーカイブ付きソケットの動作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: ソケット クラスからの派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows ソケット: ソケット通知](../mfc/windows-sockets-socket-notifications.md)

- [Windows ソケット: ブロッキング](../mfc/windows-sockets-blocking.md)

- [Windows ソケット: バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)

- [Windows ソケット: 文字列の変換](../mfc/windows-sockets-converting-strings.md)

- [Windows ソケット: ポートとソケット アドレス](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>関連項目

[Windows ソケット](../mfc/windows-sockets.md)
