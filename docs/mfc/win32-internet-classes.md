---
title: Win32 インターネット クラス
ms.date: 09/12/2018
f1_keywords:
- vc.classes.win32
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
ms.openlocfilehash: c067d0c0067ee13b0e6ce6d84fd97135274c88b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326730"
---
# <a name="win32-internet-classes"></a>Win32 インターネット クラス

MFC は、インターネット プログラミングを簡単には、Win32 のインターネット (WinInet) と ActiveX テクノロジをラップします。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

[CInternetSession](../mfc/reference/cinternetsession-class.md)<br/>
作成しインターネット セッションを 1 つまたは複数の同時インターネット セッションを初期化し、必要に応じて、プロキシ サーバーへの接続をについて説明します。

[CInternetConnection](../mfc/reference/cinternetconnection-class.md)<br/>
インターネット サーバーへの接続を管理します。

[CInternetFile](../mfc/reference/cinternetfile-class.md)<br/>
このクラスとその派生クラスは、インターネット プロトコルを使用するリモート システム上のファイルへのアクセスを許可します。

[CHttpConnection](../mfc/reference/chttpconnection-class.md)<br/>
HTTP サーバーへの接続を管理します。

[CHttpFile](../mfc/reference/chttpfile-class.md)<br/>
検索し、HTTP サーバー上のファイルを読み込む機能を提供します。

[CGopherFile](../mfc/reference/cgopherfile-class.md)<br/>
gopher サーバー上のファイルを検索し、読み込む機能が用意されています。

[CFtpConnection](../mfc/reference/cftpconnection-class.md)<br/>
FTP サーバーへの接続を管理します。

[CGopherConnection](../mfc/reference/cgopherconnection-class.md)<br/>
Gopher サーバーへの接続を管理します。

[CFileFind](../mfc/reference/cfilefind-class.md)<br/>
ローカルおよびインターネット ファイル検索を実行します。

[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)<br/>
FTP サーバーのインターネット ファイル検索を支援します。

[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)<br/>
gopher サーバーのインターネット ファイル検索を支援します。

[CGopherLocator](../mfc/reference/cgopherlocator-class.md)<br/>
gopher ロケーターを gopher サーバーから取得し、ロケーター種別を判断し、`CGopherFileFind` 用に準備します。

[CInternetException](../mfc/reference/cinternetexception-class.md)<br/>
インターネット操作に関する例外条件を表します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
