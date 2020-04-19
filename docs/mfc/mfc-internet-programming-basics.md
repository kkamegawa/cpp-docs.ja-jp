---
title: MFC インターネット プログラミングの基礎
ms.date: 11/19/2018
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
ms.openlocfilehash: eee045e198f61c088e302c40deb2de406adab428
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449733"
---
# <a name="mfc-internet-programming-basics"></a>MFC インターネット プログラミングの基礎

Microsoft では、クライアントとサーバーの両方のアプリケーションのプログラミングの多くの Api を提供します。 多くの新しいアプリケーションが、インターネットに書き込まれていると、テクノロジ、ブラウザーの機能、およびセキュリティ オプションの変更、新しい種類のアプリケーションが書き込まれます。 World Wide Web にアクセスするため、テキスト、グラフィックス、ActiveX コントロール、およびドキュメントを含む HTML ページを表示して、クライアント コンピューターでブラウザーを実行します。 サーバーは、FTP、HTTP、および、gopher サービスを提供し、CGI を使用してサーバー拡張機能のアプリケーションを実行します。 カスタム アプリケーションでは、情報を取得でき、インターネット上のデータを提供することができます。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

![クライアントとサーバー アプリケーション](../mfc/media/vc38bq1.gif "クライアントおよびサーバー アプリケーション")

MFC は、インターネット プログラミングをサポートするクラスを提供します。 使用することができます[COleControl](../mfc/reference/colecontrol-class.md)と[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)および関連する ActiveX コントロールとアクティブなドキュメントを記述する MFC クラス。 などの MFC クラスを使用することができます[CInternetSession](../mfc/reference/cinternetsession-class.md)、 [CFtpConnection](../mfc/reference/cftpconnection-class.md)、および[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)ファイルと、FTP などのインターネット プロトコルを使用して情報を取得するにはHTTP、および gopher します。

## <a name="in-this-section"></a>このセクションの内容

- [インターネット関連の MFC クラス](../mfc/internet-related-mfc-classes.md)

- [項目別のインターネット情報](../mfc/internet-information-by-topic.md)

- [タスク別のインターネット情報](../mfc/internet-information-by-task.md)

- [インターネット上の Active テクノロジ](../mfc/active-technology-on-the-internet.md)

- [WinInet の基礎](../mfc/wininet-basics.md)

- [HTML の基礎](../mfc/html-basics.md)

## <a name="related-sections"></a>関連項目

- [インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)

- [インターネット上の非同期モニカー](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [MFC インターネット プログラミングの作業](../mfc/mfc-internet-programming-tasks.md)

- [アプリケーションのデザイン上の検討事項](../mfc/application-design-choices.md)

- [MFC アプリケーションの作成](../mfc/writing-mfc-applications.md)

- [インターネット アプリケーションのテスト](../mfc/testing-internet-applications.md)

- [インターネット セキュリティ](../mfc/internet-security-cpp.md)

- [DHTML コントロールの ATL サポート](../atl/atl-support-for-dhtml-controls.md)

##  <a name="_core_web_sites_for_more_information"></a> 詳細については、Web サイト

マイクロソフトのインターネット テクノロジの詳細については、次を参照してください。、 [Microsoft Developer Network (MSDN)](https://go.microsoft.com/fwlink/p/?linkid=56322) Web サイト。 (リンクは、予告なく変更可能性があります)。

開発者のためには、この Web サイトには、マイクロソフトの開発ツールとテクノロジ、および直近および今後の会議のトップ記事の使用に関する情報が含まれています。 このページには、.NET、XML のデベロッパー センターをなど、多くの開発者向け関連サイトにジャンプすることができます。 ベータ版の Sdk とサンプルをダウンロードすることもできます。

[World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) HTML、HTTP、CGI、およびその他の Web テクノロジの仕様を公開します。

##  <a name="_core_more_internet_help"></a> 詳細についてはインターネット

Windows SDK の OLE セクションには、OLE プログラミングに関する追加情報が含まれています。 この情報は、MFC クラスではなく、直接、WinInet の Win32 関数の使用方法の詳細を説明します。 インターネット テクノロジに関する概要情報も含まれています。
