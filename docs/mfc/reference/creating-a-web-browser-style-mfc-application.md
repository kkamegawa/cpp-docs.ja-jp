---
title: Web ブラウザー形式の MFC アプリケーションの作成
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: 9d249c7effc2c78e319207d82c9a963d7a61a67c
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504759"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Web ブラウザー形式の MFC アプリケーションの作成

ネットワークおよびローカル ファイル システムで、Web ブラウザー スタイルのアプリケーション (HTML、アクティブなドキュメントなど)、インターネットまたはイントラネットでは、フォルダーから情報にアクセスできます。 アプリケーションのビューのクラスから派生することによって[CHtmlView](../../mfc/reference/chtmlview-class.md)、効果的に WebBrowser コントロールにビューを提供することで、Web ブラウザー アプリケーションを作成します。

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>MFC のドキュメント/ビュー アーキテクチャに基づく Web ブラウザー アプリケーションを作成するには

1. 指示に従って[MFC アプリケーションを作成する](../../mfc/reference/creating-an-mfc-application.md)します。

1. MFC アプリケーション ウィザードで[アプリケーションの種類](../../mfc/reference/application-type-mfc-application-wizard.md) ページであること、**ドキュメント/ビュー アーキテクチャ**ボックスがオンにします。 (いずれも使用できます**1 つのドキュメント**または**複数のドキュメント**、なく**ダイアログ ベース**)。

1. [生成されたクラス](../../mfc/reference/generated-classes-mfc-application-wizard.md) ページで、使用、**基本クラス**を選択するドロップダウン メニュー`CHtmlView`します。

1. その他のオプションをスケルトン アプリケーションに組み込まれているを選択します。

1. **[完了]** をクリックします。

WebBrowser コントロールでは、Web 参照のハイパーリンクと Uniform Resource Locator (URL) のナビゲーションをサポートします。 コントロールは、ユーザーが前後に参照できる履歴一覧を保持しを旧バージョンと以前に参照サイト、フォルダー、およびドキュメント。 コントロールは、ナビゲーション、ハイパーリンク、履歴リスト、お気に入り、およびセキュリティを直接処理します。 アプリケーションは、WebBrowser コントロールをホストのアクティブなドキュメントも、アクティブなドキュメントのコンテナーとして使用できます。 そのため、Microsoft Excel スプレッドシートなどの表現力豊かな書式設定されたドキュメントまたは Word 文書を開くおよび編集できますから WebBrowser コントロール内で。 WebBrowser コントロールが ActiveX コントロールをホストできる ActiveX コントロール コンテナーもできます。

> [!NOTE]
>  WebBrowser ActiveX コントロール (したがって`CHtmlView`) 以降がインストールされているか Internet Explorer 4.0 での Windows バージョンで実行されるアプリケーションにのみ使用できます。

`CHtmlView`だけ印刷が他の Microsoft の Web ブラウザー コントロールのサポートを実装[CView](../../mfc/reference/cview-class.md)-クラスを派生します。 代わりに、WebBrowser コントロールは、印刷、プリンターのユーザー インターフェイスを実装します。 その結果、`CHtmlView`はサポートされていません 印刷プレビュー、およびフレームワークはその他の印刷のサポート機能を提供しません: たとえば、[関数](../../mfc/reference/cview-class.md#onprepareprinting)、[値](../../mfc/reference/cview-class.md#onbeginprinting)、および[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)、他の MFC アプリケーションで利用可能な。

`CHtmlView` で、アプリケーション、Web または HTML ページを表示、Web ブラウザー コントロール用のラッパーとして機能します。 ウィザードの作成よりも優先、 [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)ビュー クラスは、Microsoft Visual C++ Web サイトへのナビゲーション リンクを提供することで、関数。

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

このサイトは、独自のいずれかで置き換えることができます。 または使用できます、 [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)メンバー関数は、ビューの既定の内容として、プロジェクトのリソース スクリプトに存在する HTML ページを開きます。 例:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>関連項目

[MFC サンプル MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)<br/>
[コンパイラとビルドのプロパティの設定](../../build/working-with-project-properties.md)<br/>
[プロパティ ページ](../../build/reference/property-pages-visual-cpp.md)<br/>
[コンパイラとビルドのプロパティの設定](../../build/working-with-project-properties.md)

