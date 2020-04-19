---
title: Windows ソケット:ポートとソケット アドレス
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: c33ec1376c1898272cf80e8d77c5cc273e16f9de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389373"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows ソケット:ポートとソケット アドレス

この記事では、用語"port"および"address"として Windows ソケットの使用について説明します。

##  <a name="_core_port"></a> ポート

ポートは、サービスを提供する一意のプロセスを識別します。 現在のコンテキストでは、ポートは、Windows Sockets をサポートするアプリケーションに関連付けられます。 考え方は、1 つ以上の Windows ソケット アプリケーションを同時に、マシンで実行されていることもできます各 Windows ソケット アプリケーションを一意に識別するためにです。

特定のポートは、FTP などの一般的なサービスの予約されています。 この種のサービスを提供する場合を除き、これらのポートを使用してを避ける必要があります。 Windows ソケット仕様では、これらの予約ポートについて説明します。 WINSOCK ファイル。H を使用して、それらも表示されます。

使用できるポートを選択します。 Windows Sockets DLL をできるようにするには、ポートの値として 0 を渡します。 MFC では、1,024 の 10 進数より大きいポート値を選択します。 MFC を呼び出すことによって選択されているポートの値を取得することができます、[で](../mfc/reference/casyncsocket-class.md#getsockname)メンバー関数。

##  <a name="_core_socket_address"></a> ソケット アドレス

各ソケット オブジェクトは、ネットワーク上、インターネット プロトコル (IP) アドレスに関連付けられます。 通常、アドレスは、「専用」などのコンピューター名または「128.56.22.8」など、ピリオドで区切られた数字です。

ソケットを作成するとき、通常、独自のアドレスを指定する必要はありません。

> [!NOTE]
>  すると、コンピューターには複数のネットワーク カード (または、アプリケーションがこのようなマシン実行いつか)、それぞれが別のネットワークを表します。 そうである場合は、ソケットが使用するネットワーク カードを指定するアドレスを付与する必要があります。 これは、高度な使用状況と移植性にも問題を特定します。

詳細については次を参照してください:

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: アーカイブ付きソケットの動作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
