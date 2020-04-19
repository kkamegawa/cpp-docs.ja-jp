---
title: 典型的なインターネット クライアント アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9762e762680e2ac530b87baeac7afdea77ef6f14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306939"
---
# <a name="steps-in-a-typical-internet-client-application"></a>典型的なインターネット クライアント アプリケーションの作成手順

次の表では、一般的なインターネット クライアント アプリケーションを実行する場合があります、手順を示します。

|目標|操作を実行します。|効果|
|---------------|----------------------|-------------|
|インターネット セッションを開始します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|WinInet を初期化し、サーバーに接続します。|
|インターネット クエリ オプション (タイムアウトの制限または例では、再試行の回数) を設定します。|使用[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)します。|操作が成功した場合は FALSE を返します。|
|セッションの状態を監視するコールバック関数を確立します。|使用[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)します。|コールバックを確立[対応](../mfc/reference/cinternetsession-class.md#onstatuscallback)します。 オーバーライド`OnStatusCallback`独自コールバック ルーチンを作成します。|
|インターネット サーバー、イントラネット サーバー、またはローカル ファイルに接続します。|使用[できます](../mfc/reference/cinternetsession-class.md#openurl)します。|URL を解析し、指定したサーバーへの接続を開きます。 返します、 [CStdioFile](../mfc/reference/cstdiofile-class.md) (を渡す場合`OpenURL`ローカル ファイル名)。 これは、サーバーまたはファイルから取得されたデータにアクセスするオブジェクトです。|
|ファイルから読み取ります。|使用[細かい](../mfc/reference/cinternetfile-class.md#read)します。|指定した数の指定したバッファーを使用してバイトを読み取ります。|
|例外を処理する|使用して、 [CInternetException](../mfc/reference/cinternetexception-class.md)クラス。|すべての一般的なインターネット例外タイプを処理します。|
|インターネット セッションを終了します。|破棄、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|開いているファイル ハンドルと接続を自動的にクリーンアップします。|

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント クラスの必要条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
