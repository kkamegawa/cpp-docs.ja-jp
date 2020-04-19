---
title: コントロール クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 79a71a4660cd49f85726d730c9fad0b2f10f83bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338169"
---
# <a name="control-classes"></a>コントロール クラス

コントロール クラスには、さまざまな標準の Windows コントロールのツリー コントロールに静的なテキスト コントロールの範囲がカプセル化します。 さらに、MFC には、ビットマップとコントロール バーのボタンなど、いくつかの新しいコントロールが用意されています。

コントロールのクラス名の終わり"**Ctrl**"は Windows 95 および Windows NT 3.51 の新しい機能です。

## <a name="static-display-controls"></a>静的表示コントロール

[CStatic](../mfc/reference/cstatic-class.md)<br/>
静的な表示のウィンドウ。 スタティック コントロールは、ラベル付け、ボックス、またはダイアログ ボックスまたはウィンドウの他のコントロールを個別に使用されます。 グラフィカル イメージではなくテキストまたはボックスを表示することもできます。

## <a name="text-controls"></a>テキスト コントロール

[CEdit](../mfc/reference/cedit-class.md)<br/>
編集可能なテキスト コントロール ウィンドウの場合。 編集コントロールを使用して、ユーザーからのテキストの入力をそのまま使用します。

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
インターネット プロトコル (IP) アドレスを操作するためのエディット ボックスをサポートしています。

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
これで、ユーザーは入力し、テキストを編集するコントロール。 カプセル化されているコントロールとは異なり`CEdit`、リッチ エディット コントロールには、文字および段落の書式設定と OLE オブジェクトがサポートしています。

## <a name="controls-that-represent-numbers"></a>数値を表すコントロール

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
ユーザーが値または値のセットを選択するに移動するスライダーを格納しているコントロール。

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
矢印ボタンのペア、ユーザーは、インクリメントまたはデクリメントの値をクリックできます。

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
左から右にある操作の進行状況を徐々 に塗りつぶされる四角形が表示されます。

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
スクロール バー コントロールのウィンドウ。 クラスは、ダイアログ ボックスまたはウィンドウで、ユーザーが範囲内の位置を指定のコントロールとして使用するためのスクロール バーの機能を提供します。

## <a name="buttons"></a>ボタン

[CButton](../mfc/reference/cbutton-class.md)<br/>
ボタン コントロールのウィンドウ。 クラスは、プッシュ ボタン、チェック ボックスをオンまたはダイアログ ボックスまたはウィンドウでのラジオ ボタンのプログラム インターフェイスを提供します。

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
テキスト キャプションではなく、ビットマップのボタンをクリックします。

## <a name="lists"></a>表示内容

[CListBox](../mfc/reference/clistbox-class.md)<br/>
リスト ボックス コントロールのウィンドウ。 リスト ボックスは、ユーザーが表示および選択項目の一覧を表示します。

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
Windows リスト ボックスの機能を提供しますによりユーザーは、リスト ボックス内でファイル名と文字列のリテラルなど、リスト ボックス アイテムを移動できます。 この機能を持つリスト ボックスにアルファベット以外の順序で項目一覧には便利ですなどのパス名またはファイルをプロジェクトに含めます。

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
コンボ ボックス コントロールのウィンドウ。 コンボ ボックスは、エディット コントロールとリスト ボックスで構成されます。

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
イメージ リストをサポートすることにより、コンボ ボックス コントロールを拡張します。

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
ユーザーが確認またはオフに、各項目の横にあるチェック ボックスを持つ項目の一覧を表示します。

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
アイコンとラベルをファイル エクスプ ローラーの右側のウィンドウと同様の方法で構成される各項目のコレクションを表示します。

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
ファイル エクスプ ローラーの左側のウィンドウと同様の方法で配置されたラベルとアイコンの階層リストを表示します。

## <a name="toolbars-and-status-bars"></a>ツールバーとステータス バー

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Windows ツール バー コモン コントロールの機能が用意されています。 ほとんどの MFC プログラムを使用して[CToolBar](../mfc/reference/ctoolbar-class.md)このクラスの代わりにします。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平方向のウィンドウでは、通常はウィンドウ、アプリケーションが状態情報を表示できますに分かれています。 ほとんどの MFC プログラムを使用して[CStatusBar](../mfc/reference/cstatusbar-class.md)このクラスの代わりにします。

## <a name="miscellaneous-controls"></a>その他のコントロール

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
簡単なビデオ クリップを表示します。

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
単一のアプリケーションでのツールの目的を説明するテキストを表示する小さなポップアップ ウィンドウ。

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
拡張の編集コントロール、またはユーザーが特定の日付または時刻の値を選択できる単純なカレンダー インターフェイスのコントロールのいずれかをサポートしています。

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
タイトルまたは列のラベルが表示されます。

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
ユーザーが日付を選択できる単純なカレンダー インターフェイス コントロールをサポートしています。

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
ユーザーがクリックしてできる、ノートの仕切ページに似ていますのタブ コントロール。

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
ホット キーの組み合わせをすばやく操作を実行するユーザーが押すを作成するユーザーを有効にします。

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
テキストをレンダリングし、埋め込みリンクをクリックすると、適切なアプリケーションを起動します。

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
MFC ウィンドウ内の WebBrowser ActiveX コントロールの機能が用意されています。

## <a name="related-classes"></a>関連するクラス

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Windows イメージ リストの機能を提供します。 イメージ リストは、リスト コントロールとツリー コントロールで使用されます。 また、格納や一連の同じサイズのビットマップの保存にも使用できます。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows のコントロールに関連付けられているすべてのビューの基本クラスです。 コントロールに基づくビューを以下に示します。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
標準の Windows を含むビューでは、コントロールを編集します。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
豊富な Windows を含むビューでは、コントロールを編集します。

[CListView](../mfc/reference/clistview-class.md)<br/>
Windows のリスト コントロールを含むビュー。

[Ctreeview の比較](../mfc/reference/ctreeview-class.md)<br/>
Windows のツリー コントロールを含むビュー。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
