---
title: コントロール バー
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: 4b75d9a96f091d0424592f34bdb1ed7ce76c2372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152777"
---
# <a name="control-bars"></a>コントロール バー

「コントロール バー」は、ツールバー、ステータス バー、およびダイアログ バーの [全般] の名前です。 MFC クラス`CToolBar`、 `CStatusBar`、 `CDialogBar`、 `COleResizeBar`、および`CReBar`クラスから派生[CControlBar](../mfc/reference/ccontrolbar-class.md)、一般的な機能を実装します。

コントロール バーは、コントロールがユーザーことができますオプションを選択、コマンドを実行またはプログラム情報の取得の行を表示するウィンドウです。 コントロール バーの種類には、ツールバー、ダイアログ バー、およびステータス バーが含まれます。

- クラスで、ツールバー、 [CToolBar](../mfc/reference/ctoolbar-class.md)

- クラスでのステータス バー、 [CStatusBar](../mfc/reference/cstatusbar-class.md)

- クラスでのダイアログ バー [CDialogBar](../mfc/reference/cdialogbar-class.md)

- クラスで、rebars [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
>  MFC バージョン 4.0、ツールバー、ステータス バー、およびツールの時点でヒントを実装に実装されているシステム機能を使用して、 *comctl32.dll* MFC 固有の以前の実装ではなく。 Mfc バージョン 6.0、 `CReBar`comctl32.dll の機能をラップすることも追加されました。

簡単な概要については、コントロール バーの種類に従ってください。 詳細については、以下のリンクを参照してください。

## <a name="control-bars"></a>コントロール バー

コントロール バーでは、クイック、ワンステップ コマンド操作を提供することで、プログラムの使いやすさが大幅に向上します。 クラス`CControlBar`すべてのツールバー、ステータス バー、およびダイアログ バーの一般的な機能を提供します。 `CControlBar` 親フレーム ウィンドウにコントロール バーを配置する機能を提供します。 コントロール バーは、親フレーム ウィンドウの子ウィンドウでは、通常であるため、クライアント ビューまたはフレーム ウィンドウの MDI クライアントに「兄弟」になります。 コントロール バー オブジェクトは、それ自体を配置については、親ウィンドウのクライアントの四角形を使用します。 クライアント ビューまたは MDI クライアント ウィンドウが、クライアント ウィンドウの残りの部分を入力できるように、親の残りのクライアント ウィンドウ四角形を変更します。

> [!NOTE]
>  コントロール バーのボタンを持っていない場合、**コマンド**または**UPDATE_COMMAND_UI**ハンドラー、フレームワークが自動的に、ボタンを無効にします。

## <a name="toolbars"></a>ツールバー

ツールバーは、コマンドを実行するビットマップのボタンの行を表示するコントロール バーです。 ツール バー ボタンを押しては等価です。 メニュー項目を選択します。メニュー項目がツール バー ボタンと同じ ID を持つ場合、メニュー項目にマップする同じハンドラーを呼び出します。 ボタンは、プッシュ ボタン、オプション ボタン、またはチェック ボックスとして表示して機能を構成できます。 ツールバーは通常、フレーム ウィンドウの上部に配置されますが、MFC ツールバーできます「ドッキング」の親ウィンドウまたはミニフレーム ウィンドウに float 型の任意の辺にします。 ツールバーをできますも"float"とそのサイズを変更し、マウスでドラッグします。 ユーザーがツールバーのボタンにマウスを移動すると、ツールバーもツール ヒントを表示できます。 ツール ヒントは、ボタンの目的を簡単に説明する小さなポップアップ ウィンドウです。

> [!NOTE]
>  MFC バージョン 4.0 の時点でクラス[CToolBar](../mfc/reference/ctoolbar-class.md) Windows ツール バー コモン コントロールを使用します。 A`CToolBar`が含まれています、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)します。 ただし、古いツールバーはサポートもします。 記事をご覧ください[ツールバー](../mfc/mfc-toolbar-implementation.md)します。

## <a name="status-bars"></a>ステータス バー

ステータス バーは、テキスト出力ペイン、または「インジケーター」を含むコントロール バー メッセージの行と状態インジケーターとして、出力ウィンドウがよく使用されます。 メッセージの行の例には、選択したメニューまたは MFC アプリケーション ウィザードによって作成された既定のステータス バーの一番左のウィンドウで、ツールバーのコマンドを簡単に説明するコマンドライン ヘルプ メッセージにはが含まれます。 状態インジケーターの例には、SCROLL LOCK、NUM LOCK、およびその他のキーが含まれます。 ステータス バーは通常、フレーム ウィンドウの下部に配置されます。 クラスを参照してください。 [CStatusBar](../mfc/reference/cstatusbar-class.md)とクラス[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)します。

## <a name="dialog-bars"></a>ダイアログ バー

ダイアログ バーは、モードレス ダイアログ ボックスの機能と、ダイアログ テンプレート リソースに基づいて、コントロール バーです。 ダイアログ バーは、Windows を含めることができるカスタム、または ActiveX コントロール。 ダイアログ ボックスでは、ように、ユーザーは、コントロール間タブことができます。 ダイアログ バーは、top、bottom、left、またはフレーム ウィンドウの右側に配置できるし、独自のフレーム ウィンドウにフロートすることもできます。 クラスを参照してください。 [CDialogBar](../mfc/reference/cdialogbar-class.md)します。

## <a name="rebars"></a>Rebars

A [rebar](../mfc/using-crebarctrl.md)は rebar コントロールのドッキング、レイアウト、状態、および持続性の情報を提供するコントロール バーです。 Rebar オブジェクトは、さまざまな子ウィンドウ、通常は他のコントロールのエディット ボックス、ツールバー、リスト ボックスなどを含めることができます。 Rebar オブジェクトは、指定したビットマップをその子ウィンドウを表示できます。 自動または手動でサイズを変更できる、クリックするかのグリップ バーをドラッグします。 クラスを参照してください。 [CReBar](../mfc/reference/crebar-class.md)します。

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)
