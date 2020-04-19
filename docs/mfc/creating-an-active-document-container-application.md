---
title: Active ドキュメント コンテナー アプリケーションの作成
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 965778fd5d17aa416b198c101edc3a445a39580b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152944"
---
# <a name="creating-an-active-document-container-application"></a>Active ドキュメント コンテナー アプリケーションの作成

Active ドキュメント コンテナー アプリケーションを作成する最も簡単で最も推奨される方法は、MFC アプリケーション ウィザードを使用して MFC EXE コンテナー アプリケーションを作成し、active ドキュメント コンテインメントをサポートするためにアプリケーションを変更します。

#### <a name="to-create-an-active-document-container-application"></a>Active ドキュメント コンテナー アプリケーションを作成するには

1. **ファイル** メニューのをクリックして**プロジェクト**から、**新規**サブメニューで開く。

1. 左側のウィンドウから次のようにクリックします。 **Visual c**プロジェクトの種類。

1. 選択**MFC アプリケーション**右側のウィンドウ。

1. プロジェクトに名前を*MyProj*、 をクリックして**OK**します。

1. 選択、**複合ドキュメント サポート**ページ。

1. 選択、**コンテナー**または**コンテナー/フル サーバー**オプション。

1. 選択、 **Active ドキュメント コンテナー**チェック ボックスをオンします。

1. **[完了]** をクリックします。

1. MFC アプリケーション ウィザードでは、アプリケーションの生成が完了したら、ソリューション エクスプ ローラーを使用して、次のファイルを開きます。

   - *MyProjview.cpp*

1. *MyProjview.cpp*、次の変更します。

   - `CMyProjView::OnPreparePrinting`関数の内容を次のコードに置き換えます。

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` 印刷のサポートを提供します。 このコードで置き換えます`DoPreparePrinting`、これは、既定の印刷準備します。

   Active ドキュメント コンテインメントには、強化された印刷スキームが用意されています。

   - 使用してアクティブなドキュメントを最初に呼び出すことができます、`IPrint`インターフェイス自体を印刷するように指定しています。 これに対し、プリンターに含まれているアイテムの画像を表示するコンテナー必要がある、以前の OLE コンテインメント`CDC`オブジェクト。

   - 失敗した場合、通知自体を介して印刷に含まれているアイテムの`IOleCommandTarget`インターフェイス

   - 失敗した場合は、独自のアイテムの表示を確認します。

   静的メンバー関数は、`COleDocObjectItem::OnPrint`と`COleDocObjectItem::OnPreparePrinting`前のコードに実装されると、この強化された印刷スキームを処理します。

1. 独自の実装を追加し、アプリケーションをビルドします。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテインメント](../mfc/active-document-containment.md)
