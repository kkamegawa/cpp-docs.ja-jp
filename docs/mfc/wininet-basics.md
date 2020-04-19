---
title: WinInet の基礎
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: 79ec102aa27440c64f03c6e22b9f2fe959cac6b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399552"
---
# <a name="wininet-basics"></a>WinInet の基礎

WinInet を使用して、ダウンロードしてから、アプリケーション内のファイルをアップロードする FTP サポートを追加することができます。 オーバーライドできます[OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)を使用して、*独自*検索ファイルをダウンロードすると、ユーザーに進行状況に関する情報を提供するパラメーター。

この記事には、次のトピックが含まれています。

- [非常にシンプルなブラウザーを作成します。](#_core_create_a_very_simple_browser)

- [Web ページをダウンロードします。](#_core_download_a_web_page)

- [FTP ファイル](#_core_ftp_a_file)

- [Gopher ディレクトリを取得します。](#_core_retrieve_a_gopher_directory)

- [ファイルの転送中に進行状況に関する情報を表示します。](#_core_display_progress_information_while_transferring_files)

次のコードの抜粋では、単純なブラウザーを作成、Web ページでは、FTP、ファイルをダウンロードして gopher ファイルを検索する方法を示します。 完全な例としてはないし、例外処理が含まれていません。

WinInet の詳細については、次を参照してください。 [Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)します。

##  <a name="_core_create_a_very_simple_browser"></a> 非常にシンプルなブラウザーを作成します。

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> Web ページをダウンロードします。

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> FTP ファイル

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> Gopher ディレクトリを取得します。

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>OnStatusCallback を使用します。

WinInet クラスを使用するには、する場合は、使用、 [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)のアプリケーションのメンバー [CInternetSession](../mfc/reference/cinternetsession-class.md)ステータス情報を取得するオブジェクト。 独自を派生させる場合`CInternetSession`オブジェクト、オーバーライド`OnStatusCallback`、状態のコールバックを有効にして MFC が呼び出す、`OnStatusCallback`進行状況が、インターネット、そのセッションで、すべてのアクティビティに関する情報を持つ関数。

1 つのセッションはいくつかの接続 (、有効期間、多くの異なる個別の操作を実行可能性があります)、サポート可能性があるため`OnStatusCallback`特定の接続またはトランザクションを使用して各状態の変更を識別するためのメカニズムを必要があります。 このメカニズムは、WinInet のサポート クラスのメンバー関数の多くに指定されたコンテキストの ID パラメーターによって提供されます。 このパラメーターは常に型**DWORD**名前は常に*独自*します。

オブジェクトによって発生するアクティビティを識別するためにのみ、特定のインターネット オブジェクトに割り当てられているコンテキストが使用される、`OnStatusCallback`のメンバー、`CInternetSession`オブジェクト。 呼び出し`OnStatusCallback`いくつかのパラメーターを受け取るこれらのパラメーターが連携するトランザクションと接続はどのような進行状況をアプリケーションに指示します。

作成するときに、`CInternetSession`オブジェクトを指定できます、*独自*コンス トラクターのパラメーター。 `CInternetSession` 自体、コンテキスト ID を使用しません。代わりに、どのコンテキスト ID を渡します**インターネット**-派生した独自のコンテキスト ID を明示的に取得されないオブジェクト。 さらに、その`CInternetConnection`オブジェクトはに沿ってコンテキスト ID を渡す`CInternetFile`オブジェクトを別のコンテキスト ID を明示的に指定しない場合に作成します。 場合、独自の特定のコンテキスト ID、オブジェクト、およびその動作はコンテキスト ID に関連付けられる指定した一方で、 コンテキスト Id を使用するにはどのようなステータス情報で渡さを識別するために、`OnStatusCallback`関数。

##  <a name="_core_display_progress_information_while_transferring_files"></a> ファイルの転送中に進行状況に関する情報を表示します。

たとえば、ある場合はファイルの読み取りに FTP サーバーとの接続を作成しても Web ページを取得する HTTP サーバーに接続するアプリケーションを記述する、`CInternetSession`オブジェクト、2 つ`CInternetConnection`オブジェクト (1 つになります、`CFtpSession`あり、その他`CHttpSession`)、2 つと`CInternetFile`オブジェクト (接続ごとに 1 つ)。 既定値を使用している場合、*独自*パラメーター、しないことができますを区別する、 `OnStatusCallback` FTP 接続と呼び出しの進行状況を示す進行状況を示す呼び出し、HTTP 接続です。 指定した場合、*独自*ID で、後でのテストできる`OnStatusCallback`、どの操作には、コールバックが生成されることがわかります。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
