---
title: コントロール (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: 3155889f2fd4002286340ccec7f4a35d1a6a9c20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508798"
---
# <a name="controls-mfc"></a>コントロール (MFC)

コントロールは、データを入力または操作するときにユーザーが取り扱うオブジェクトです。 通常は、ダイアログ ボックスまたはツール バー上に表示されます。 ここでは、主な 3 種類のコントロールについて説明します。

- オーナー描画コントロールなどの Windows コモン コントロール

- ActiveX コントロール

- MFC (Microsoft Foundation Class) ライブラリで提供される、その他のコントロール クラス

## <a name="windows-common-controls"></a>Windows コモン コントロール

Windows オペレーティング システムでは、多数の Windows コモン コントロールが提供されています。 これらのコントロール オブジェクトはコードから操作できます。また、Visual C++ ダイアログ エディターを使用して、コントロール オブジェクトをダイアログ ボックスに追加できます。 MFC (Microsoft Foundation Class) ライブラリでは、表「 [Windows コモン コントロールと MFC クラス](#_core_windows_common_controls_and_mfc_classes)」に記述されているように、各コントロールをカプセル化するためのクラスが提供されています。 (表内の一部の項目は、詳細を説明するトピックに関連付けられています)。 トピックに関連付けられていないコントロールについては、MFC クラスに関するドキュメントを参照してください。

[CWnd](../mfc/reference/cwnd-class.md) クラスは、コントロール クラスをすべて含む、すべてのウィンドウ クラスの基底クラスです。

## <a name="activex-controls"></a>ActiveX コントロール

ActiveX コントロールは、以前は OLE コントロールと呼ばれていたもので、Windows アプリケーション、または WWW (World Wide Web) の HTML ページで使用できます。 詳細については、「 [MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)」を参照してください。

## <a name="other-mfc-control-classes"></a>その他の MFC コントロール クラス

すべての Windows コモン コントロールをカプセル化するクラスと、ユーザー独自の (または他のアプリケーションにより提供された) ActiveX コントロールのプログラミングをサポートするクラスに加えて、MFC では以下のコントロール クラスを独自に提供します。

- [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)

- [CCheckListBox](../mfc/reference/cchecklistbox-class.md)

- [CDragListBox](../mfc/reference/cdraglistbox-class.md)

##  <a name="_core_finding_information_about_windows_common_controls"></a> Windows コモン コントロールに関する情報

次の表では、MFC ラッパー クラスを含む Windows コモン コントロールについて簡単に説明します。

### <a name="_core_windows_common_controls_and_mfc_classes"></a>  Windows コモン コントロールと MFC クラス

|コントロール|MFC クラス|説明|Windows 95 の新方法|
|-------------|---------------|-----------------|------------------------|
|[アニメーション](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|AVI ビデオ クリップのフレームを連続的に表示します。|[はい]|
|ボタン|[CButton](../mfc/reference/cbutton-class.md)|アクションを発生させるプッシュ ボタン。チェック ボックス、オプション ボタン、およびグループ ボックスにも使用します。|いいえ|
|コンボ ボックス|[CComboBox](../mfc/reference/ccombobox-class.md)|エディット ボックスとリスト ボックスを組み合わせたものです。|いいえ|
|[日時指定](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|ユーザーが特定の日付または時刻の値を選択できます。|[はい]|
|エディット ボックス|[CEdit](../mfc/reference/cedit-class.md)|テキスト入力用のボックスです。|いいえ|
|[拡張コンボ ボックス](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|イメージを表示できるコンボ ボックス コントロールです。|[はい]|
|[ヘッダー](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|テキストの列の上に表示されるボタンで、テキストの表示幅を制御します。|[はい]|
|[ホット キー](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|アクションをすばやく実行するための "ホット キー" を作成できるウィンドウです。|[はい]|
|[イメージ リスト。](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|多数のアイコンまたはビットマップの管理に使用するイメージのコレクションです。イメージ リストは実際にはコントロールではなく、他のコントロールで使用されるリストをサポートします。|[はい]|
|[リスト](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|アイコンと共にテキストのリストを表示するウィンドウです。|[はい]|
|リスト ボックス|[CListBox](../mfc/reference/clistbox-class.md)|文字列のリストを格納するボックスです。|いいえ|
|[月間予定表](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|日付情報を表示するコントロールです。|[はい]|
|[progress](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|時間のかかる処理を実行する場合に、その進行状況を示すウィンドウです。|[はい]|
|[rebar](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|子ウィンドウをコントロールとして追加できるツール バーです。|[はい]|
|[リッチ エディット](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|ユーザーが文字書式および段落書式を設定して編集できるウィンドウです (「 [リッチ エディット コントロールに関連するクラス](../mfc/classes-related-to-rich-edit-controls.md)」を参照)。|[はい]|
|スクロール バー|[CScrollBar](../mfc/reference/cscrollbar-class.md)|ウィンドウ上ではなくダイアログ ボックス内のコントロールとして使用されるスクロール バーです。|いいえ|
|[スライダー](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|オプションで軸目盛りを表示できるスライダー コントロールが配置されたウィンドウです。|[はい]|
|[スピン ボタン](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|ユーザーが値の増減をクリック操作で指定できる矢印ボタンです。増加用と減少用がペアになっています。|[はい]|
|静的テキスト|[CStatic](../mfc/reference/cstatic-class.md)|他のコントロールのラベルに使用するテキストです。|いいえ|
|[ステータス バー](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|ステータス情報を表示するためのウィンドウです。MFC クラスの `CStatusBar`に似ています。|[はい]|
|[タブ](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|ノートの仕切りのような役割を果たします。"タブ ダイアログ ボックス" またはプロパティ シートで使用します。|[はい]|
|[ツール バー](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|コマンド生成ボタンを持つウィンドウです。MFC クラスの `CToolBar`に似ています。|[はい]|
|[ツール ヒント](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|ツール バー ボタンなどのツールの用途の説明を表示する小さなポップアップ ウィンドウです。|[はい]|
|[ツリー](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|項目を階層化されたリストとして表示するウィンドウです。|[はい]|

### <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- 各コントロールへのリンクについては、上記の「 [Windows コモン コントロールと MFC クラス](#_core_windows_common_controls_and_mfc_classes) 」を参照してください。

- [コントロールの作成方法と使い方](../mfc/making-and-using-controls.md)

- [ダイアログ エディターを使用したコントロールの追加](../mfc/using-the-dialog-editor-to-add-controls.md)

- [手動でコントロールを追加する方法](../mfc/adding-controls-by-hand.md)

- [MFC コントロール クラスからのコントロール クラスの派生](../mfc/deriving-controls-from-a-standard-control.md)

- [子ウィンドウとしてのコモン コントロールの使い方](../mfc/using-a-common-control-as-a-child-window.md)

- [コモン コントロールからの通知の受信](../mfc/receiving-notification-from-common-controls.md)

- ["Add common controls to a dialog box (ダイアログ ボックスへのコントロールの追加)"](../mfc/using-common-controls-in-a-dialog-box.md)。

- [Windows 標準コントロールからのコントロールの派生](../mfc/deriving-controls-from-a-standard-control.md)

- [ダイアログ ボックスのコントロールへのタイプ セーフ アクセス](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [コモン コントロールからの通知の受信](../mfc/receiving-notification-from-common-controls.md)

- [サンプル](../mfc/common-control-sample-list.md)

Windows SDK の Windows コモンコントロールの詳細については、「[コモンコントロール](/windows/win32/Controls/common-controls-intro)」を参照してください。

## <a name="see-also"></a>関連項目

[ユーザーインターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[ダイアログ エディター](../windows/dialog-editor.md)
