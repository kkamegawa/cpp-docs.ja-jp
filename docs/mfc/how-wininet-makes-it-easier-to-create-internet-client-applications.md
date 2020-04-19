---
title: WinInet を使ってインターネット クライアント アプリケーションを簡単に作成する方法
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 6da2ef1595e525bcfd407d67c806aa80cf90f1c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262711"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet を使ってインターネット クライアント アプリケーションを簡単に作成する方法

Win32 インターネット拡張機能または WinInet、gopher、FTP、HTTP などの一般的なインターネット プロトコルへのアクセスを提供します。 WinInet を使用して WinSock、TCP/IP、または特定のインターネット プロトコルの詳細を処理することがなく、プログラミングのより高いレベルでのインターネット クライアント アプリケーションを記述できます。 WinInet では、使い慣れた Win32 API インターフェイスで、すべての 3 つのプロトコルの一貫性のある一連の関数を提供します。 この整合性は、(たとえば、FTP HTTP から) から、基になるプロトコルが変更された場合のために必要なコードの変更を最小限に抑えます。

Visual C には、WinInet を使用するための 2 つの方法が用意されています。 Win32 インターネット関数を直接呼び出すことができます (詳細については、Windows SDK の OLE ドキュメントを参照してください) を通じて WinInet を使用することも、 [MFC WinInet クラス](../mfc/mfc-classes-for-creating-internet-client-applications.md)します。

**WinInet を使用できます。**

- HTML ページをダウンロードします。

   HTTP は、サーバーからクライアント ブラウザーに HTML ページを転送するために使用するプロトコルです。

- アップロードまたはファイルをダウンロードまたはディレクトリの一覧を取得する FTP 要求を送信します。

   一般的な要求では、ファイルをダウンロードする匿名ログオンです。

- Gopher のメニュー システムを使用して、インターネット上のリソースにアクセスするためです。

   メニュー項目には、その他のメニューのインデックス付きデータベースを検索することができます、ニュースグループ、またはファイルを含む、いくつかの種類を指定できます。

3 つのすべてのプロトコルをする、接続を確立し、サーバーに要求する接続を閉じます。

**MFC WinInet クラスは、簡単になります。**

- ハード ドライブからファイルを読み取るのと同じくらい簡単に、HTTP、FTP、および gopher サーバーから情報を読み取ります。

- WinSock または TCP/IP に直接プログラミングを行わず、HTTP、FTP、および gopher プロトコルを使用します。

   Win32 インターネット関数を使用する開発者は、TCP/IP または Windows Sockets を理解する必要はありません。 まだプログラムできるソケット レベルでは、WinSock および TCP/IP プロトコルを使用して、直接がインターネット経由でアクセス HTTP、FTP、gopher プロトコルに MFC WinInet クラスを使用するも簡単です。 多くの一般的な操作では、開発者が使用している特定のプロトコルの詳細を知る必要はありません。

多くの操作として、インターネット上の他のコンピューターにクライアント コンピューターで実行できる時間がかかることができます。 これらの操作の速度は、通常、ネットワーク接続の速度によって制限が、他のネットワーク トラフィックと、操作の複雑さによっても影響します。 リモートの FTP サーバーへの接続などが必要です、コンピューターがそのアドレスを見つけるには、そのサーバーの名前を最初になります。 アプリケーションは、そのアドレスでサーバーに接続する試みます。 接続を開くと、コンピューターとリモート サーバーがメッセージ交換を開始ファイル転送プロトコルを使用した前に、実際には、ファイルを取得する接続を使用することができます。

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[MFC を使ってインターネット クライアント アプリケーションを簡単に作成する方法](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)
