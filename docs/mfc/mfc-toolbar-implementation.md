---
title: MFC ツール バーの実装
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 55c43c47b93cd21d86293706fc7c3eb5145c39fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238560"
---
# <a name="mfc-toolbar-implementation"></a>MFC ツール バーの実装

ツールバーは、[コントロール バー](../mfc/control-bars.md)コントロールのビットマップ イメージを格納しています。 これらのイメージはプッシュ ボタン、チェック ボックス、オプション ボタンに似た動作をすることができます。 MFC クラスを提供する[CToolbar](../mfc/reference/ctoolbar-class.md)ツールバーを管理します。

これを有効にすると、MFC ツール バーのユーザーは、ツール バーをウィンドウの端にドッキングするか、アプリケーション ウィンドウ内の任意の場所にツール バーを "フローティング" させることができます。 MFC では、開発環境のようなカスタマイズ可能なツール バーをサポートしていません。

MFC では、ツール ヒントもサポートしています。これは、マウス ポインターをボタンの上に移動したときに、ツール バー ボタンの目的を説明する小さなポップアップ ウィンドウです。 既定では、ユーザーがツール バー ボタンをクリックすると、ステータス バー (表示されている場合) の中に、ステータス文字列が表示されます。 ボタンをクリックせずに、マウス ポインターをツール バー ボタンの上に移動したときに、ステータス文字列の表示を更新する、"フライ バイ" (リアルタイム更新) ステータス バーを有効にすることもできます。

> [!NOTE]
>  MFC バージョン 4.0 の時点で、ツール バーとツール ヒントは、MFC 固有の以前の実装ではなく、Windows 95 以降の機能を使用して実装されています。

旧バージョンと互換性のため、MFC では古いツールバーの実装クラスで`COldToolBar`します。 以前のバージョンの MFC のドキュメントについては説明`COldToolBar``CToolBar`します。

アプリケーション ウィザードの [ツール バー] オプションをクリックし、プログラムの最初のツール バーを作成します。 追加のツール バーを作成することもできます。

この記事では、次の項目を紹介します。

- [ツール バー ボタン](#_core_toolbar_buttons)

- [ドッキングとフローティング ツールバー](#_core_docking_and_floating_toolbars)

- [ツールバーとツール ヒント](#_core_toolbars_and_tool_tips)

- [CToolBar クラスと CToolBarCtrl クラス](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [ツールバーのビットマップ](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> ツール バー ボタン

ツール バー内のボタンは、メニュー内の項目に似ています。 どちらの種類のユーザー インターフェイス オブジェクトも、コマンドを生成します。プログラムはハンドラー関数を提供して、これらのコマンドを処理します。 多くの場合、ツール バー ボタンはメニュー コマンドの機能を複製したものであり、同じ機能に対する別のユーザー インターフェイスを提供します。 このような重複は、単純にボタンとメニュー項目に対して同じ ID を付与する方法で実現できます。

ツール バー内で、プッシュ ボタン、チェック ボックス、またはオプション ボタンと同じ外観でボタンを作成し、同じ動作をさせることができます。 詳細については、クラスを参照してください。 [CToolBar](../mfc/reference/ctoolbar-class.md)します。

##  <a name="_core_docking_and_floating_toolbars"></a> ドッキングとフローティング ツールバー

MFC ツール バーでは、次のことを実行できます。

- 親ウィンドウの 1 つの辺に固定したままにします。

- ドラッグして、親ウィンドウの任意の辺に "ドッキング" させます (取り付けます)。

- フレーム ウィンドウから切り離し、ミニフレーム ウィンドウの形でツール バーとして使用します。このツール バーは、ユーザーが任意の場所に移動できます。

- フローティング中にサイズを変更します。

詳細については、この記事を参照してください。[ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)します。

##  <a name="_core_toolbars_and_tool_tips"></a> ツールバーとツール ヒント

MFC ツール バーには "ツール ヒント" を表示させることもできます。ツール ヒントとは、ツール バー ボタンの用途を説明する短いテキストを表示する小さなポップアップ ウィンドウのことです。 ユーザーがツール バー ボタンの上にマウス ポインタを置くと、ヒントを示すツール ヒントのウィンドウがポップアップ表示されます。 詳細については、この記事を参照してください。[ツールバーのツール ヒント](../mfc/toolbar-tool-tips.md)します。

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar クラスと CToolBarCtrl クラス

クラスを使用して、アプリケーションのツールバーを管理する[CToolBar](../mfc/reference/ctoolbar-class.md)します。 MFC Version 4.0 では、Windows 95 以降、および Windows NT Version 3.51 以降のバージョンで使用されているツール バー コモン コントロールを使用できるように、`CToolBar` が再実装されています。

この再実装により、それらのオペレーティング システムでサポートされているコントロールを MFC で利用できるため、ツール バー関連の MFC コードは少なくなりました。 また、この再実装によって性能も向上しています。 使用することができます`CToolBar`ツールバー、またはを操作するメンバー関数は、基になるへの参照を取得できる[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクトし、ツールバーのカスタマイズなどの追加機能のメンバー関数を呼び出します。

> [!TIP]
>  以前の形式の `CToolBar` を実装するために多大な労力を費やしてきた場合は、そのまま以前の形式のツール バーを使用できます。 記事をご覧ください[を使用して、古いツールバー](../mfc/using-your-old-toolbars.md)します。

また、MFC 標準サンプルを参照してください[DOCKTOOL](../overview/visual-cpp-samples.md)します。

##  <a name="_core_the_toolbar_bitmap"></a> ツールバーのビットマップ

`CToolBar` オブジェクトは、いったん生成された後は、各ボタンのイメージを含む 1 つのビットマップを読み込んでツール バー イメージを作成します。 アプリケーション ウィザードでは、カスタマイズ可能な標準ツールバーのビットマップを作成、Visual C で[ツール バー エディター](../windows/toolbar-editor.md)します。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ツールバーに関する基本事項](../mfc/toolbar-fundamentals.md)

- [ドッキングとフローティング ツールバー](../mfc/docking-and-floating-toolbars.md)

- [ツールバーのツール ヒント](../mfc/toolbar-tool-tips.md)

- [ToolBar コントロールの操作](../mfc/working-with-the-toolbar-control.md)

- [古い形式のツール バーの使用方法](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)と[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)クラス

## <a name="see-also"></a>関連項目

[ツールバー](../mfc/toolbars.md)<br/>
[ツール バー エディター](../windows/toolbar-editor.md)
