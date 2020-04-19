---
title: コンテナー:高度な機能
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: 350431975a4335fc06e436237b7e0d3388faab64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152931"
---
# <a name="containers-advanced-features"></a>コンテナー:高度な機能

この記事では、既存のコンテナー アプリケーションに省略可能な高度な機能を組み込むために必要な手順について説明します。 これらの機能は次のとおりです。

- [コンテナーとサーバーの両方であるアプリケーション](#_core_creating_a_container_server_application)

- [埋め込みオブジェクトへのリンク](#_core_links_to_embedded_objects)

##  <a name="_core_creating_a_container_server_application"></a> コンテナー/サーバー アプリケーションを作成します。

コンテナー/サーバー アプリケーションは、コンテナーとサーバーの両方として機能するアプリケーションです。 Microsoft Word for Windows では、この例を示します。 Windows の Word ドキュメントを他のアプリケーションに埋め込むことができますし、Windows の Word ドキュメント内のアイテムを埋め込むこともします。 コンテナー アプリケーションのコンテナーと (組み合わせコンテナー/ミニサーバー アプリケーションを作成することはできません)、完全なサーバーの両方を変更するプロセスについては、完全なサーバーを作成するためのプロセスに似ています。

この記事[サーバー。サーバーを実装する](../mfc/servers-implementing-a-server.md)さまざまなサーバー アプリケーションを実装するために必要なタスクを一覧表示されます。 コンテナー/サーバー アプリケーションへのコンテナー アプリケーションを変換する場合、必要があります、同じタスクの一部を実行するコードをコンテナーに追加します。 考慮すべき重要な点を次に示します。

- 既にアプリケーション ウィザードによって作成されたコンテナーのコードでは、OLE サブシステムを初期化します。 変更または追加をサポートする、何かする必要はありません。

- ドキュメント クラスの基底クラスの任意の場所は`COleDocument`に基本クラスを変更`COleServerDoc`します。

- オーバーライド`COleClientItem::CanActivate`場で編集できる、サーバー自体を使用中は、配置内の項目を編集しないようにします。

   たとえば、MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)コンテナー/サーバー アプリケーションで作成されたアイテムが埋め込まれています。 OCLIENT アプリケーションを開くし、一括編集コンテナー/サーバー アプリケーションで作成された項目。 アプリケーションのアイテムの編集中に決定した MFC OLE サンプルで作成したアイテムを埋め込む[HIERSVR](../overview/visual-cpp-samples.md)します。 これを行うには、インプレース アクティブ化を使用することはできません。 完全には、この項目をアクティブ化する HIERSVR を開く必要があります。 Microsoft Foundation Class ライブラリがこの OLE 機能をサポートしていないためにオーバーライド`COleClientItem::CanActivate`すると、このような状況を確認し、アプリケーションで可能な実行時エラーを防ぐことができます。

新しいアプリケーションを作成し、コンテナー/サーバー アプリケーションとして機能する場合は、アプリケーション ウィザードでこのサポート OLE オプション ダイアログ ボックスのオプションが自動的に作成されることを選択します。 詳細については、この記事を参照してください。[概要。ActiveX コントロール コンテナーの作成](../mfc/reference/creating-an-mfc-activex-control-container.md)です。 MFC のサンプルについては、MFC のサンプルを参照してください。

それ自体に MDI アプリケーションを挿入することはできませんに注意してください。 SDI アプリケーションである場合を除き、コンテナー/サーバー アプリケーションを自体に挿入できません。

##  <a name="_core_links_to_embedded_objects"></a> 埋め込みオブジェクトへのリンク

埋め込みオブジェクトの機能へのリンクには、ドキュメント コンテナー アプリケーション内の埋め込みオブジェクトへのリンクを作成するユーザーができるようにします。 たとえば、スプレッドシートを埋め込む、ワード プロセッサでドキュメントを作成します。 アプリケーションでは、埋め込みオブジェクトへのリンクをサポートする場合、ワード プロセッサのドキュメントに含まれるスプレッドシートへのリンクを貼り付けることができます。 この機能により、スプレッドシート、ワード プロセッサもともと了解を知らなくても含まれる情報を使用するアプリケーション。

#### <a name="to-link-to-embedded-objects-in-your-application"></a>アプリケーション内の埋め込みオブジェクトにリンクするには

1. ドキュメントからクラスを派生`COleLinkingDoc`の代わりに`COleDocument`します。

1. OLE クラス ID の作成 (**CLSID**) OLE 開発ツールに含まれているクラス ID ジェネレーターを使用してアプリケーション用。

1. OLE アプリケーションを登録します。

1. 作成、`COleTemplateServer`アプリケーション クラスのメンバーとしてのオブジェクト。

1. アプリケーション クラス`InitInstance`メンバー関数で、次の操作を行います。

   - 接続、`COleTemplateServer`を呼び出して、オブジェクトのドキュメント テンプレートにオブジェクト`ConnectTemplate`メンバー関数。

   - 呼び出す、 `COleTemplateServer::RegisterAll` OLE システム クラスのすべてのオブジェクトに登録します。

   - `COleTemplateServer::UpdateRegistry` を呼び出す。 唯一のパラメーターを`UpdateRegistry`べき*OAT_CONTAINER* 「/埋め込みの」スイッチを使用して、アプリケーションが起動しない場合。 これは、埋め込みオブジェクトへのリンクをサポートできるコンテナーとしてアプリケーションを登録します。

         If the application is launched with the "/Embedded" switch, it should not show its main window, similar to a server application.

MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md)この機能を実装します。 これを行う方法の例は、次を参照してください。、`InitInstance`で機能、 *OCLIENT します。CPP*このサンプル アプリケーションのファイル。

## <a name="see-also"></a>関連項目

[コンテナー](../mfc/containers.md)<br/>
[サーバー](../mfc/servers.md)
