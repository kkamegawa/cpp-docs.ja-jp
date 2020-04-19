---
title: ファイルを削除する典型的な FTP クライアント アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 6d2a920d3053a920638dd20a23e1c2334745bbc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307056"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>ファイルを削除する典型的な FTP クライアント アプリケーションの作成手順

次の表では、ファイルを削除する典型的な FTP クライアント アプリケーションで手順を示します。

|目標|操作を実行します。|効果|
|---------------|----------------------|-------------|
|FTP セッションを開始します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|WinInet を初期化し、サーバーに接続します。|
|FTP サーバーに接続します。|使用[CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)します。|返します、 [CFtpConnection](../mfc/reference/cftpconnection-class.md)オブジェクト。|
|FTP サーバー上のディレクトリ位置していることを確認します。|使用[CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)または[CFtpConnection::GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl)します。|名前または現在選択されているメンバー関数によって、サーバー上に接続しているディレクトリの URL を返します。|
|サーバー上に新しい FTP ディレクトリに変更します。|使用[CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)します。|現在、サーバーに接続しているディレクトリを変更します。|
|FTP ディレクトリの最初のファイルを検索します。|使用[CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile)します。|最初のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|FTP ディレクトリの次のファイルを検索します。|使用[CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)します。|次のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|によって検出されたファイルを削除`FindFile`または`FindNextFile`します。|使用[CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove)、によって返されるファイル名を使用して`FindFile`または`FindNextFile`します。|サーバー上の読み取りまたは書き込みのファイルを削除します。|
|例外を処理する|使用して、 [CInternetException](../mfc/reference/cinternetexception-class.md)クラス。|すべての一般的なインターネット例外タイプを処理します。|
|FTP セッションを終了します。|破棄、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|開いているファイル ハンドルと接続を自動的にクリーンアップします。|

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント クラスの必要条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
