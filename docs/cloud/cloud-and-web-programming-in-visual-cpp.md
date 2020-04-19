---
title: Visual C++ でのクラウドおよび Web プログラミング
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 4e50557733d474d68b8e503d00b28b2ae8cb7f09
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274641"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Visual C++ でのクラウドおよび Web プログラミング

C++ では、Web とクラウドに接続するためのいくつかの方法があります。

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure の SDK および REST サービス

- [C++ 用 Microsoft Azure Storage クライアント ライブラリ](https://azure.github.io/azure-storage-cpp/)

  C++ 用 Microsoft Azure Storage クライアント ライブラリでは、Azure Storage を操作するための包括的な API が提供されています。これには次の機能が含まれますが、これに限定されるわけではありません。

  - BLOB コンテナー、テーブル、キューの作成、読み取り、削除、一覧表示。
  - BLOB の作成、読み取り、削除、一覧表示と、BLOB 範囲の読み取りと書き込み。
  - Azure テーブル内のエンティティの挿入、削除、置換、結合、クエリ。
  - Azure キューでのメッセージのエンキューとデキュー。
  - コンテナー、BLOB、テーブル、キューの遅延リスト、およびエンティティの遅延クエリ

- モノのインターネットに関する ANSI C99 の [Azure IoT Hub SDK](/azure/iot-hub/iot-hub-devguide-sdks) により、IoT アプリケーションがデバイスまたはバックエンドで実行できるようになります。

- [Microsoft Graph での OneDrive および SharePoint](https://dev.onedrive.com/README.htm)

  OneDrive API では、アプリケーションを Office 365 と SharePoint Server 2016 のファイルとフォルダーに接続する一連の HTTP サービスが提供されます。

## <a name="windows-and-cross-platform-networking-apis"></a>Windows およびクロスプラットフォームのネットワーク API

- [C++ REST SDK (コードネーム "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  REST サービスと対話するための最新のクロスプラットフォームの非同期 API を提供します。

  - JSON ドキュメントの解析とシリアル化の組み込みサポートにより、任意の HTTP サーバーに対して REST 呼び出しを実行する
  - OAuth 1 と 2 (ローカル リダイレクト リスナーを含む) をサポート
  - リモート サービスに対する WebSocket 接続
  - PPL に基づく完全な非同期タスク API (組み込みのスレッド プールを含む)

  Windows デスクトップ (7 以降)、Windows Server (2012 以降)、ユニバーサル Windows プラットフォーム、Linux、OSX、Android、および iOS をサポートしています。

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  System.Web 名前空間にある同じ名前の .NET Framework クラスでモデル化された Windows ランタイムの HTTP クライアント クラスです。 `HttpClient` は、HTTP 経由の非同期アップロードとダウンロード、およびパイプラインにカスタム HTTP ハンドラーを挿入するためのパイプライン フィルターを完全にサポートします。 Windows SDK には、メーター付きネットワークや OAuth 認証用のサンプル フィルターが含まれています。 ユニバーサル Windows プラットフォームのみを対象とするアプリには、`Windows::Web:HttpClient` クラスを使用することをお勧めします。

- [IXMLHTTPRequest2 インターフェイス](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Windows ランタイム アプリまたは Windows デスクトップ アプリで、HTTP 経由でインターネットに接続し、GET、PUT などの HTTP コマンドを発行するために使用できる、ネイティブな COM インターフェイスを提供します。 詳細については、「[チュートリアル:タスクおよび XML HTTP 要求を使用した接続](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)」を参照してください。

- [Windows インターネット (WinInet)](/windows/win32/WinInet/portal)

  Windows デスクトップ アプリでインターネットに接続するために使用できる Windows API。

## <a name="see-also"></a>関連項目

[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Microsoft Azure C および C++ デベロッパー センター](https://azure.microsoft.com/develop/cpp/) <br/>
[ネットワークと Web サービス (UWP)](/windows/uwp/networking/)
