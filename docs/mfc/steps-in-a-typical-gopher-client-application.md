---
title: 典型的な Gopher クライアント アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: ca1a09a4a570fd705e726ac5a1124a4cf4ccb329
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307005"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>典型的な Gopher クライアント アプリケーションの作成手順

次の表に、典型的な gopher クライアント アプリケーションでの手順を示します。

|目標|操作を実行します。|効果|
|---------------|----------------------|-------------|
|Gopher セッションを開始します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|WinInet を初期化し、サーバーに接続します。|
|Gopher サーバーに接続します。|使用[代わり](../mfc/reference/cinternetsession-class.md#getgopherconnection)します。|返します、 [CGopherConnection](../mfc/reference/cgopherconnection-class.md)オブジェクト。|
|Gopher で最初のリソースを検索します。|使用[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)します。|最初のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|Gopher、次のリソースを検索します。|使用[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)します。|次のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|によって検出されたファイルを開く`FindFile`または`FindNextFile`読み取り用です。|使用して gopher ロケーターを取得[なった](../mfc/reference/cgopherfilefind-class.md#getlocator)します。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)します。|ロケーターによって指定されたファイルを開きます。 `OpenFile` 返します、 [CGopherFile](../mfc/reference/cgopherfile-class.md)オブジェクト。|
|指定した gopher ロケーターを使用してファイルを開きます。|使用して、gopher ロケーターを作成[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)します。 使用[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)します。|ロケーターによって指定されたファイルを開きます。 `OpenFile` 返します、 [CGopherFile](../mfc/reference/cgopherfile-class.md)オブジェクト。|
|ファイルから読み取ります。|使用[CGopherFile](../mfc/reference/cgopherfile-class.md)します。|指定した数の指定したバッファーを使用してバイトを読み取ります。|
|例外を処理する|使用して、 [CInternetException](../mfc/reference/cinternetexception-class.md)クラス。|すべての一般的なインターネット例外タイプを処理します。|
|Gopher セッションを終了します。|破棄、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|開いているファイル ハンドルと接続を自動的にクリーンアップします。|

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント クラスの必要条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
