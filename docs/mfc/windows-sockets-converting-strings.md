---
title: Windows ソケット:文字列の変換
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: eaf278fc2689f0afa9ab6ff30f1294c36de5d7ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217392"
---
# <a name="windows-sockets-converting-strings"></a>Windows ソケット:文字列の変換

この記事と関連記事では 2 つは、Windows ソケット プログラミングのいくつかの問題を説明します。 この記事では、文字列の変換について説明します。 その他の問題は、「 [Windows ソケット。ブロック](../mfc/windows-sockets-blocking.md)と[Windows ソケット。バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)します。

使用するか、またはクラスから派生させる場合[CAsyncSocket](../mfc/reference/casyncsocket-class.md)、これらの問題を自分で管理する必要があります。 使用するか、またはクラスから派生させる場合[CSocket](../mfc/reference/csocket-class.md)MFC を管理します。

## <a name="converting-strings"></a>文字列の変換

Unicode またはマルチバイト文字セット (MBCS) など、さまざまなワイド文字形式で格納された文字列を使用するアプリケーション間、またはこれらのいずれかと ANSI 文字の文字列を使用してアプリケーションの間を通信する場合は、変換を管理する必要があります。自分で`CAsyncSocket`します。 `CArchive`で使用されるオブジェクト、`CSocket`オブジェクト クラスの機能を使用するの変換を管理する[CString](../atl-mfc-shared/reference/cstringt-class.md)します。 詳細については、Windows SDK には、Windows ソケット仕様を参照してください。

詳細については次を参照してください:

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: 予備知識](../mfc/windows-sockets-background.md)

- [Windows ソケット: ストリーム ソケット](../mfc/windows-sockets-stream-sockets.md)

- [Windows ソケット: データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
