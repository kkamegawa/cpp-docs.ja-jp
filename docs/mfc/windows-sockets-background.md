---
title: Windows ソケット:背景
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 6ab866609d0b75aaf9d06a01c204433d80e7e3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217879"
---
# <a name="windows-sockets-background"></a>Windows ソケット:背景

この記事では、Windows ソケットの特性と目的について説明します。 以下の内容についても説明します。

- [用語「ソケット」の定義](#_core_definition_of_a_socket)します。

- [ソケットのハンドルのデータ型を示す](#_core_the_socket_data_type)します。

- [ソケットの使用について](#_core_uses_for_sockets)します。

Windows ソケット仕様は、Microsoft Windows 向けのバイナリ互換性のあるネットワーク プログラミング インターフェイスを定義します。 Windows ソケットは、カリフォルニア大学バークレー校で開発された Berkeley Software Distribution (BSD、リリース 4.3) の UNIX ソケットの実装に基づいています。 仕様には、BSD スタイルのソケット ルーチンと Windows 固有の拡張機能の両方が含まれています。 Windows ソケットを使用すると、アプリケーションが Windows ソケット API に準拠するネットワークを経由して通信できます。 Win32 では、Windows ソケットによってスレッド セーフが提供されます。

多くのネットワーク ソフトウェア ベンダーは、伝送制御プロトコル/インターネット プロトコル (TCP/IP)、Xerox ネットワーク システム (XNS)、Digital Equipment 社の DECNet プロトコル、Novell 社のインターネット パケット交換/順次編成パック交換 (IPX/SPX) などのネットワーク プロトコルの下で Windows ソケットをサポートしています。 現在の Windows ソケット仕様では TCP/IP 向けにソケットの抽象化が定義されていますが、どのネットワーク プロトコルでも、Windows ソケットを実装する独自バージョンのダイナミック リンク ライブラリ (DLL) を用意することで Windows ソケットに準拠できます。 Windows ソケットを使用して作成された商用アプリケーションの例として、X Windows サーバー、端末エミュレーター、電子メール システムがあります。

> [!NOTE]
>  Windows ソケットの目的は、基になるネットワークを抽象化して、そのネットワークについて詳しく知らなくても、ソケットをサポートするネットワークでアプリケーションを実行できるようにすることです。 そのため、このドキュメントではネットワーク プロトコルの詳細については説明しません。

Microsoft Foundation Class ライブラリ (MFC) は、Windows ソケット API を使用するプログラムをサポートするために、2 つのクラスを提供しています。 1 つは `CSocket` です。このクラスは、高レベルの抽象化を提供してネットワーク通信プログラミングを簡略化します。

Windows ソケット仕様では、Windows ソケット:ネットワーク コンピューティング Microsoft Windows、version 1.1 に今すぐに開くインターフェイスは、個人や企業は、TCP/IP コミュニティでの大規模なグループによってオープン ネットワー キング標準として開発されましたし、は自由に使用します。 現在、ソケット プログラミング モデルは、インターネット プロトコル スイートを使用して 1 つの "通信ドメイン" をサポートします。 仕様は、Windows SDK で使用できます。

> [!TIP]
>  ソケットはインターネット プロトコル スイートを使用するため、"情報ハイウェイ" でのインターネット通信をサポートするアプリケーションにとって最適な手段です。

##  <a name="_core_definition_of_a_socket"></a> ソケットの定義

ソケットは通信のエンドポイントです。つまり、Windows ソケット アプリケーションがネットワーク経由でデータ パケットを送受信するために使用するオブジェクトです。 ソケットには型があり、実行中のプロセスと関連付けられます。名前を持つ場合もあります。 現在、ソケットは同一の "通信ドメイン" 内にあり、インターネット プロトコル スイートを使用する他のソケットとのみデータを交換するのが普通です。

2 種類のソケットはどちらも双方向で、両方向に同時に通信できるデータ フローです (全二重)。

次の 2 種類のソケットを使用できます。

- ストリーム ソケット

   ストリーム ソケットは、レコード境界のないデータ フロー、つまりバイト ストリーム用です。 ストリームは必ず配信され、正しく順序付けられて重複しません。

- データグラム ソケット

   データグラム ソケットは、レコード指向のデータ フローをサポートします。このデータ フローは配信されるとは限らず、送信順になっていないことや重複していることがあります。

"順序付けられた" とは、パケットが送信順に配信されることです。 "重複しない" とは、特定のパケットが一度だけ配信されることです。

> [!NOTE]
>  XNS などの一部のネットワーク プロトコルでは、ストリームをバイトのストリームではなく、レコードのストリームにできます。 ただし、もっと一般的な TCP/IP プロトコルでは、ストリームはバイト ストリームです。 Windows ソケットは、基になるプロトコルに依存しない抽象化レベルを提供します。

これらの種類についてを参照してください、どのような状況で使用するソケットの種類および[Windows ソケット。ソケットを Stream](../mfc/windows-sockets-stream-sockets.md)と[Windows ソケット。データグラム ソケット](../mfc/windows-sockets-datagram-sockets.md)します。

##  <a name="_core_the_socket_data_type"></a> ソケットのデータ型

各 MFC ソケット オブジェクトは、Windows ソケット オブジェクトへのハンドルをカプセル化します。 このハンドルのデータ型は**ソケット**します。 A**ソケット**ハンドルに似ていますが、`HWND`ウィンドウ。 MFC ソケット クラスは、カプセル化されたハンドルでの操作を提供します。

**ソケット**データ型は、Windows SDK で詳しく説明します。 「Windows Sockets (Windows ソケット)」の「Socket Data Type and Error Values (ソケット データ型とエラー値)」を参照してください。

##  <a name="_core_uses_for_sockets"></a> ソケットの使用

ソケットは、少なくとも次の 3 つの通信コンテキストで非常に有用です。

- クライアント/サーバー モデル。

- ピアツーピア シナリオ (メッセージング アプリケーションなど)。

- リモート プロシージャ コール (RPC)。受信側アプリケーションにメッセージを関数呼び出しとして解釈させます。

> [!TIP]
>  MFC ソケットの理想的な使用状況は、通信の両端を自分で作成し、両端で MFC を使用する場合です。 非 MFC アプリケーションとの通信時に大文字と小文字を管理する方法など、このトピックの詳細については、次を参照してください。 [Windows ソケット。バイトの順序付け](../mfc/windows-sockets-byte-ordering.md)します。

詳細については、Windows ソケット仕様を参照してください: **ntohs**、 **ntohl**、 **htons**、 **htonl**します。 次のトピックも参照してください。

- [Windows ソケット: アーカイブ付きソケットの使用](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows ソケット: アーカイブを使用するソケットの例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows ソケット: CAsyncSocket クラスの使い方](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>関連項目

[MFC における Windows ソケット](../mfc/windows-sockets-in-mfc.md)
