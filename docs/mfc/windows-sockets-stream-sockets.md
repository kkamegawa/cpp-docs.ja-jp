---
title: Windows ソケット:Stream ソケット
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: 91f06c4a36e76638708edf085987e51418913fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337831"
---
# <a name="windows-sockets-stream-sockets"></a>Windows ソケット:Stream ソケット

この記事では、ストリーム ソケットの場合、使用できる 2 つの Windows ソケット型のいずれかについて説明します。 (その他の型は、[データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md))。

Stream ソケットは、レコード境界のないデータ フローの提供: ことができる双方向のバイトのストリーム (アプリケーションが全二重: 送信し、ソケット経由で受信ができます)。 ストリームは、シーケンスを重複なしのデータを配布に依存できます。 (「順序付けられた」パケットが送信された順序で配信されたことを意味します。 「重複なし」を意味、特定のパケットを 1 回だけ取得します。)ストリーム メッセージの受信が保証され、ストリームは大量のデータの処理に適してします。

ネットワーク トランスポート層は、分割または妥当なサイズのパケット データをグループ化可能性があります。 `CSocket`梱包し、アンパックするクラスを処理します。

ストリームは明示的な接続に基づきますソケット、ソケット B; への接続を要求する。ソケット B を受け入れるか、接続要求を拒否します。

電話の呼び出しでは、ストリームの例えるを提供します。 通常の状況では、受信側パーティがって、重複または損失なく順序が話した内容聞こえます。 Stream のソケットは、必要に応じて、たとえば、実装など、ファイル転送プロトコル (FTP)、転送 ASCII または任意のサイズのバイナリ ファイルを容易にします。

Stream ソケットは、データの到着することが保証する必要があり、データのサイズが大きい場合、データグラム ソケットに適しています。 ストリーム ソケットの詳細については、Windows ソケット仕様を参照してください。 仕様は、Windows SDK で使用できます。

ストリーム ソケットを使用するよりもアプリケーションのため、ネットワーク上のすべての受信ソケットへのブロードキャストのデータグラム ソケットを使用するように設計

- ブロードキャスト モデルは、ネットワークのフラッド (または"storm") の問題です。

- その後に採用されたクライアント/サーバー モデルより効率的です。

- ストリーム モデルでは、データグラムのモデルはありません、信頼性の高いデータの転送を提供します。

- 最終的なモデルは、Unicode と ANSI 間のソケット アプリケーションで通信する機能の利用は CArchive CSocket クラスに適していると、そのクラスがします。

    > [!NOTE]
    >  クラスを使用する場合`CSocket`ストリームを使用する必要があります。 ソケット タイプを指定する場合、MFC アサーションが失敗した**SOCK_DGRAM**します。

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)
