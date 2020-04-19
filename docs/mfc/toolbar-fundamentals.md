---
title: ツール バーに関する基本事項
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: 9c784db2e1a482b313147e6837d6bbbd16d0ecb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168220"
---
# <a name="toolbar-fundamentals"></a>ツール バーに関する基本事項

この記事では、アプリケーション ウィザードでオプションを選択して、アプリケーションに既定のツールバーを追加できるようにする基本的な MFC 実装について説明します。 取り上げるトピックは次のとおりです。

- [アプリケーション ウィザードの [ツールバー] オプション](#_core_the_appwizard_toolbar_option)

- [ツールバーのコード](#_core_the_toolbar_in_code)

- [ツール バー リソースの編集](#_core_editing_the_toolbar_resource)

- [複数のツールバー](#_core_multiple_toolbars)

##  <a name="_core_the_appwizard_toolbar_option"></a> アプリケーション ウィザードのツール バー オプション

既定のボタンを持つ 1 つのツールバーを取得するには、というラベルの付いたユーザー インターフェイス機能 ページの標準ドッキング ツールバー オプションを選択します。 これは、アプリケーションにコードが追加されますを。

- ツール バー オブジェクトを作成します。

- ツールバーで、その機能をドッキングまたはフローティングなどを管理します。

##  <a name="_core_the_toolbar_in_code"></a> ツールバーのコード

ツールバーは、 [CToolBar](../mfc/reference/ctoolbar-class.md)オブジェクトは、アプリケーションのデータ メンバーとして宣言されている`CMainFrame`クラス。 つまり、ツールバーのオブジェクトは、メイン フレーム ウィンドウのオブジェクトに埋め込まれます。 これは、フレーム ウィンドウを作成し、フレーム ウィンドウが破棄されると、ツールバーを破棄する場合、MFC でツールバーを作成することを意味します。 複数ドキュメント インターフェイス (MDI) アプリケーションの場合、次の部分クラス宣言には、埋め込みのツールバーと、埋め込まれたステータス バーのデータ メンバーが表示されます。 オーバーライドも表示されます、`OnCreate`メンバー関数。

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

ツールバーの作成は、`CMainFrame::OnCreate`します。 MFC 呼び出し[OnCreate](../mfc/reference/cwnd-class.md#oncreate)が可視になりますが、フレーム ウィンドウを作成した後。 既定の`OnCreate`ツールバーの次のタスクには、アプリケーション ウィザードが生成されます。

1. 呼び出し、`CToolBar`オブジェクトの[作成](../mfc/reference/ctoolbar-class.md#create)メンバー関数を作成する、基になる[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクト。

1. 呼び出し[LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)ツールバーのリソース情報を読み込めません。

1. ドッキング、フローティング、およびツール ヒントを有効にする関数を呼び出します。 詳細については、これらの呼び出しは、この記事を参照してください。[ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)します。

> [!NOTE]
>  MFC 標準サンプル[DOCKTOOL](../overview/visual-cpp-samples.md)新旧両方の MFC ツールバーの図が含まれています。 使用するツールバー`COldToolbar`に手順 2. で呼び出しを必要と`LoadBitmap`(なく`LoadToolBar`) および`SetButtons`します。 新しいツールバーへの呼び出しを必要と`LoadToolBar`します。

ドッキング、フローティング、およびツール ヒントの呼び出しは省略可能です。 これらの行を削除する`OnCreate`したい場合。 結果は、固定、フローティングやできませんし、ツール ヒントを表示できませんに残っているツールバーです。

##  <a name="_core_editing_the_toolbar_resource"></a> ツール バー リソースの編集

アプリケーション ウィザードを使用して取得した既定のツールバーがに基づいて、 **RT_TOOLBAR** MFC バージョン 4.0 で導入されたカスタムのリソース。 このリソースを編集する、[ツール バー エディター](../windows/toolbar-editor.md)します。 エディターでは、追加、削除、およびボタンを再配置を簡単にすることができます。 グラフィカル エディター非常に一般的なグラフィックス エディター Visual C では、次のようなボタンにはが含まれています。 Visual C の以前のバージョンでツールバーを編集する場合があります、タスク簡単ようになりました。

コマンドには、ツール バー ボタンを接続するに付けるボタン コマンド ID をなど`ID_MYCOMMAND`します。 ツールバー エディターで、ボタンのプロパティ ページで、コマンド ID を指定します。 コマンドのハンドラー関数を作成し (を参照してください[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md)詳細については)。

新しい[CToolBar](../mfc/reference/ctoolbar-class.md)メンバー関数は、 **RT_TOOLBAR**リソース。 [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)の場所を受け取るようになりました[LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap)ツールバー ボタンのイメージのビットマップの読み込みと[SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons)ボタンのスタイルを設定し、ビットマップ イメージにボタンを接続します。

ツール バー エディターの使用に関する詳細については、次を参照してください。[ツール バー エディター](../windows/toolbar-editor.md)します。

##  <a name="_core_multiple_toolbars"></a> 複数のツールバー

アプリケーション ウィザードは、1 つの既定のツールバーを提供します。 アプリケーションでは、複数のツールバーを必要がある場合は、既定のツールバーのウィザードで生成されたコードに基づく追加のツールバーのコードをモデル化できます。

コマンドの結果として、ツールバーを表示する場合は、する必要があります。

- ツールバー エディターを使って新しいツール バー リソースを作成し、読み込むことで`OnCreate`で、 [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar)メンバー関数。

- 新しい埋め込み[CToolBar](../mfc/reference/ctoolbar-class.md)メイン フレーム ウィンドウ クラスのオブジェクト。

- 内の適切な関数呼び出しのこと`OnCreate`ドッキングまたはフローティング ツールバーのスタイルを設定および具合にします。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [MFC ツールバーの実装 (ツールバーに概要情報)](../mfc/mfc-toolbar-implementation.md)

- [ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)

- [ツールバーのツール ヒント](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)と[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)クラス

- [ツール バー コントロールの操作](../mfc/working-with-the-toolbar-control.md)

- [古い形式のツールバーを使用します。](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>関連項目

[MFC ツール バーの実装](../mfc/mfc-toolbar-implementation.md)
