---
title: MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 6e32210217321e4eb59d7d3e666a4f5494eb3642
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399474"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法

すべてのインターネット クライアント アプリケーションの基礎は、インターネット セッションです。 MFC クラスのオブジェクトとしてインターネット セッションを実装する[CInternetSession](../mfc/reference/cinternetsession-class.md)します。 このクラスを使用して、インターネット セッションを 1 つまたは複数の同時セッションを作成できます。

サーバーを通信する必要があります、 [CInternetConnection](../mfc/reference/cinternetconnection-class.md)オブジェクトと同様に、`CInternetSession`します。 作成することができます、`CInternetConnection`を使用して[CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)、[代わりに](../mfc/reference/cinternetsession-class.md#gethttpconnection)、または[代わり](../mfc/reference/cinternetsession-class.md#getgopherconnection). それらの各呼び出しは、プロトコルの種類に固有です。 これらの呼び出しは、サーバー上のファイルの読み取りまたは書き込みを開かないでください。 読み取りまたは書き込みする場合は、別のステップとして、ファイルを開く必要があります。

ほとんどのインターネット セッション、`CInternetSession`オブジェクトの機能を手は手で、 [CInternetFile](../mfc/reference/cinternetfile-class.md)オブジェクト。

- インターネット セッションのインスタンスを作成する必要があります[CInternetSession](../mfc/reference/cinternetsession-class.md)します。

- インスタンスを作成する必要がある場合は、インターネット セッションの読み取りまたは書き込みデータ、 `CInternetFile` (またはそのサブクラスでは、 [CHttpFile](../mfc/reference/chttpfile-class.md)または[CGopherFile](../mfc/reference/cgopherfile-class.md))。 データを読み取る最も簡単な方法を呼び出すことです。[できます](../mfc/reference/cinternetsession-class.md#openurl)します。 この関数は、入力された Universal Resource Locator (URL) を解析し、URL で指定されたサーバーへの接続を開きます読み取り専用を返します`CInternetFile`オブジェクト。 `CInternetSession::OpenURL` 1 つのプロトコルの種類に固有ではありません: 同じ呼び出しは、任意の FTP、HTTP、または gopher URL の動作します。 `CInternetSession::OpenURL` ローカル ファイルでも機能 (を返す、`CStdioFile`の代わりに、 `CInternetFile`)。

- セッションが読み取りまたは書き込みをしていない、インターネットが FTP ディレクトリ内のファイルを削除するなど、他のタスクを実行する場合のインスタンスを作成する必要はありませんが`CInternetFile`します。

作成する 2 つの方法がある、`CInternetFile`オブジェクト。

- 使用する場合`CInternetSession::OpenURL`への呼び出し、サーバー接続を確立する`OpenURL`を返します、`CStdioFile`します。

- 場合を使用して、 `CInternetSession::GetFtpConnection`、 `GetGopherConnection`、または`GetHttpConnection`サーバー接続を確立するために呼び出す必要がある`CFtpConnection::OpenFile`、 `CGopherConnection::OpenFile`、または`CHttpConnection::OpenRequest`、それぞれ、返される、 `CInternetFile`、 `CGopherFile`、または`CHttpFile`、それぞれします。

インターネット クライアント アプリケーションを実装する手順で汎用的なインターネット クライアントを作成するかどうかによって異なります`OpenURL`またはのいずれかを使用してプロトコル固有のクライアント、`GetConnection`関数。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [FTP、HTTP、および gopher で一般的に動作するインターネット クライアント アプリケーションを作成する方法](../mfc/steps-in-a-typical-internet-client-application.md)

- [ファイルを開き、FTP クライアント アプリケーションを作成する方法](../mfc/steps-in-a-typical-ftp-client-application.md)

- [ファイルを開くことができませんが、ファイルを削除するなどのディレクトリ操作を実行する FTP クライアント アプリケーションを作成する方法](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Gopher クライアント アプリケーションを作成する方法](../mfc/steps-in-a-typical-gopher-client-application.md)

- [HTTP クライアント アプリケーションを作成する方法](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント アプリケーションの作成用の MFC クラス](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[インターネット クライアント クラスの必要条件](../mfc/prerequisites-for-internet-client-classes.md)
