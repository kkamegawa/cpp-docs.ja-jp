---
title: AFX メッセージ
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: 5caf40fc757e2c5c90c06e1698ce4c15d1ed6240
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338060"
---
# <a name="afx-messages"></a>AFX メッセージ

これらのメッセージは、MFC で使用されます。

## <a name="messages"></a>メッセージ

次の表では、MFC ライブラリで使用されるメッセージを示します。

||||||
|-|-|-|-|-|
|メッセージ|説明|[in] *wParam*|*lParam* (すべてのパラメーターは [in] 特に明記しない限り)。|戻り値|
|AFX_WM_ACCGETOBJECT|使用しません。|使用しません。|該当なし。|該当なし。|
|AFX_WM_ACCGETSTATE|ユーザー補助のサポートに使用されます。 このメッセージを送信`CMFCPopupMenu`または`CMFCRibbonPanelMenu`現在の要素の状態を取得します。|メニュー ボタンまたは区切り記号である可能性がある、要素のインデックス。|使用しません。|要素の状態。 インデックスが有効でない場合は-1、メニュー ボタンが特別な属性を持っていない場合は 0。 それ以外の場合、次のフラグの組み合わせです。<br /><br /> TBBS_DISABLED: 項目が無効になっています<br /><br /> TBBS_CHECKED: 項目は、オンします。<br /><br /> TBBS_BUTTON-項目が標準のプッシュ ボタンです。<br /><br /> TBBS_PRESSED: ボタンが押されました。<br /><br /> TBBS_INDETERMINATE: 未定義の状態<br /><br /> TBBS_SEPARATOR - ではなくメニュー ボタンでは、他のメニュー項目間の分離をこの要素のフォーム|
|AFX_WM_CHANGE_ACTIVE_TAB|フレームワークは、サイズ変更可能なコントロール バー コントロールにこのメッセージを送信します。 通知を受信するには、このメッセージを処理`CMFCTabCtrl`オブジェクトをユーザーには、アクティブなタブが変更されたとき。|タブのインデックス。|使用しません。|0 以外の値。|
|AFX_WM_CHANGE_CURRENT_FOLDER|フレームワークでは、このメッセージを送信の親に`CMFCShellListCtrl`ユーザーが、現在のフォルダーに変更されたとき。|使用しません。|使用しません。|使用しません。|
|AFX_WM_CHANGEVISUALMANAGER|フレームワークでは、現在のビジュアル マネージャーを変更したときに、すべてのフレーム ウィンドウにこのメッセージを送信します。 このメッセージに応答してでは、フレーム ウィンドウは、その領域を再計算し、必要に応じて、他のパラメーターを調整します。 このイベントに関する通知を受ける必要がある場合、アプリケーションで AFX_WM_CHANGEVISUALMANAGER メッセージを処理することができます。 基底クラスのハンドラーを呼び出す必要があります (`OnChangeVisualManager`) フレームワークの内部であることを確認するのにはこのイベントの処理は行われます。|使用しません。|使用しません。|使用しません。|
|AFX_WM_CHANGING_ACTIVE_TAB|親に送信される`CMFCTabCtrl`オブジェクト。  通知を受信する場合は、このメッセージを処理`CMFCTabCtrl`オブジェクトをユーザーがタブをリセットします。|アクティブ化していますが、タブのインデックス。|使用しません。|0 以外の値。|
|AFX_WM_CHECKEMPTYMINIFRAME|内部使用のみ。|該当なし。|該当なし。|該当なし。|
|AFX_WM_CREATETOOLBAR|送信された`CMFCToolBarsListPropertyPage`カスタマイズ プロセス中に、ユーザーが新しいツールバーを作成する場合。 カスタム CMFCToolBar から派生したオブジェクトをインスタンス化するには、このメッセージを処理することができます。 このメッセージを処理し、独自のツールバーを作成した場合は、既定のハンドラーへの呼び出しを省略します。|使用しません。|ツールバーの名前を含む文字列へのポインター。|新しく作成したツールバーへのポインター。 NULL では、ツールバーの作成が取り消されたことを示します。|
|AFX_WM_CUSTOMIZEHELP|カスタマイズのプロパティ シートからメイン フレーム ウィンドウに送信された`CMFCToolbarCustomize Dialog`押されたとき、**ヘルプ**ボタンまたは F1 キーを押します。|カスタマイズのプロパティ シートの現在のページを指定します。|`CMFCToolbarCustomize Dialog` オブジェクトへのポインター。|0 を返します。|
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog`親フレームに、ユーザーが新しいツールバーを作成することを通知するには、このメッセージを送信します。|TRUE のカスタマイズが開始されると、FALSE のカスタマイズが完了するとします。|使用しません。|0 を返します。|
|AFX_WM_DELETETOOLBAR|ユーザーがカスタマイズ モードでツールバーを削除すると、メイン フレーム ウィンドウに送信されます。<br /><br /> ユーザーがカスタマイズ モードでツールバーを削除するときに、多くのアクションを実行するには、このメッセージを処理します。 既定のハンドラーを呼び出す必要がありますも (`OnToolbarDelete`)、これはツールバーを削除します。 既定のハンドラーは、ツールバーを削除することであるかどうかを示す値を返します。|使用しません。|ポインターを`CMFCToolBar`を削除するオブジェクト。|0 以外の場合、ツールバーを削除できません。それ以外の場合 0 を返します。|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` ドキュメントの色を取得するメイン フレーム ウィンドウには、このメッセージを送信します。|使用しません。|[入力、出力]ポインターを`CList<COLORREF, COLORREF>`オブジェクト。|0 を返します。|
|AFX_WM_GETDRAGBOUNDS|内部使用のみ。|該当なし。|該当なし。|該当なし。|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|ユーザーがリボンのリスト項目を強調表示したときに、メイン フレーム ウィンドウに送信されます。|強調表示されている項目のインデックス|ポインター `CMFCBaseRibbonElement`|使用しません。|
|AFX_WM_ON_AFTER_SHELL_COMMAND|親に送信される`CMFCShellListCtrl`または`CMFCShellTreeCtrl`ユーザーのシェル コマンドの実行が終了したときを制御します。|ユーザーが実行したコマンドの ID|使用しません。|アプリケーションでは、このメッセージを処理する場合は 0 を返します。|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|フレームワークでは、ポップアップ メニューを表示する前に、このメッセージをリボンの親に送信します。 このメッセージを処理し、ポップアップ メニューをいつでもでも変更できます。|使用しません。|ポインター `CMFCBaseRibbonElement`|使用しません。|
|AFX_WM_ON_CANCELTABMOVE|内部使用のみ。|該当なし。|該当なし。||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|フレームワークでは、アクティブなリボン コントロールのカテゴリを変更したときに、メイン フレームにこのメッセージを送信します。|使用しません。|ポインター、`CMFCRibbonBar`カテゴリが変更されています。|使用しません。|
|AFX_WM_ON_CLOSEPOPUPWINDOW|フレームワークの所有者に通知するには、このメッセージを送信`CMFCDesktopAlertWnd`ウィンドウの期限が終了されます。|使用しません。|ポインター`CMFCDesktopAlertWnd`オブジェクト。|使用しません。|
|AFX_WM_ON_DRAGCOMPLETE|内部使用のみ。|該当なし。|該当なし。|該当なし。|
|AFX_WM_ON_GET_TAB_TOOLTIP|タブ ウィンドウがカスタム ツールヒントが有効になっている場合に、タブのツールヒントを表示するときに、メイン フレーム ウィンドウに送信されます。|使用しません。|ポインター、`CMFCTabToolTipInfo`構造体。|使用しません。|
|AFX_WM_ON_HSCROLL|サイズ変更可能なコントロール バー コントロールに送信します。 通知を受信するには、このメッセージを処理`CMFCTabCtrl`タブ ウィジェットの水平スクロール バーでスクロール イベントが発生したときのオブジェクトします。|下位ワードは、スクロール バーの値を示す、ユーザーの要求のスクロールを指定します。  詳細については、このトピックで後に示す表を参照してください。|使用しません。|0 以外の値。|
|AFX_WM_ON_MOVE_TAB|ユーザーが新しい位置にタブをドラッグすると、タブ付きウィンドウの親に送信されます。|元の位置で、タブの 0 から始まるインデックス。|[out]タブの新しい位置の 0 から始まるインデックス。|0 を返します。|
|AFX_WM_ON_MOVETABCOMPLETE|内部使用のみ。|該当なし。|該当なし。|該当なし。|
|AFX_WM_ON_MOVETOTABGROUP|ユーザーでは、1 つのタブ付きグループ間 MDI 子ウィンドウを移動するときに、メイン フレーム ウィンドウに送信されます。|タブ付きウィンドウを識別するハンドル (`CMFCTabCtrl`) から、MDI 子ウィンドウが削除されました。|[out]タブ付きウィンドウを識別するハンドル (`CMFCTabCtrl`) MDI 子ウィンドウに挿入されています。|無視されます。|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|親に送信される`CDockablePane`ユーザーがクリックすると、**閉じる**コントロール バーのキャプションのボタンをクリックします。|使用しません。|ユーザーがクリックされたドッキング可能ペインへのポインター、**閉じる**ボタンをクリックします。|TRUE の場合、ウィンドウを閉じることができません。それ以外の場合は FALSE です。|
|AFX_WM_ON_RENAME_TAB|ユーザーが編集可能なタブの名前を変更した後、タブ付きウィンドウの親に送信されます。|名前が変更されたタブの 0 から始まるインデックス。|[out]新しいタブ名を含む文字列へのポインター。|アプリケーションは、このメッセージを処理する場合、0 以外の場合フレームワークでの呼び出しを抑制する`CMFCBaseTabCtrl::SetTabLabel`します。  0 が返された場合`CMFCBaseTabCtrl::SetTabLabel`はフレームワークによって呼び出されます。|
|AFX_WM_ON_RIBBON_CUSTOMIZE|ユーザーのカスタマイズの開始時に親フレームに送信されます。 独自のカスタマイズ ダイアログ ボックスを表示する場合は、このメッセージを処理します。|使用しません。|カスタマイズをリボン コントロールへのポインター。|以外の場合は、アプリケーションは、このメッセージを処理し、独自のカスタマイズ ダイアログ ボックスが表示されます。 アプリケーションがゼロを返す場合、フレームワークによって、組み込みのカスタマイズ ダイアログ ボックスが表示されます。|
|AFX_WM_ON_TABGROUPMOUSEMOVE|内部使用のみ。|該当なし。|該当なし。|該当なし。|
|AFX_WM_POSTSETPREVIEWFRAME|ユーザーが印刷プレビュー モードを変更したメイン フレームに通知されます。|TRUE は、印刷プレビュー モードが設定されていることを示します。 FALSE は、印刷プレビュー モードがになっていることを示します。|使用しません。|使用しません。|
|AFX_WM_PROPERTY_CHANGED|プロパティ グリッド コントロールの所有者に送信される (`CMFCPropertyGridCtrl`) に、ユーザーが選択されているプロパティの値を変更します。|プロパティ リストのコントロール ID。|プロパティへのポインター (`CMFCPropertyGridProperty`) に変更します。|使用しません。|
|AFX_WM_RESETCONTEXTMENU|ユーザーがカスタマイズするときに、コンテキスト メニューをリセットしたときに、メイン フレーム ウィンドウに送信されます。|コンテキスト メニューのリソース ID。|現在のコンテキスト メニューへのポインター`CMFCPopupMenu`します。|使用しません。|
|AFX_WM_RESETKEYBOARD|フレームワークでは、ユーザーがカスタマイズするときにすべてのキーボード アクセラレータをリセットしたときに、このメッセージをメイン フレーム ウィンドウに送信します。|使用しません。|使用しません。|使用しません。|
|AFX_WM_RESETMENU|フレームワークでは、このメッセージを送信 メニューの所有者 (フレーム ウィンドウ) に、ユーザーがカスタマイズするときに、アプリケーションのフレームのメニューをリセットすると|メニューの リソース id です。|使用しません。|使用しません。|
|AFX_WM_RESETPROMPT|フレームワークは、ツールバー、ツールバーから、ユーザーのリセット ダイアログ ボックスをカスタマイズするときに、このメッセージを送信します。 既定のハンドラーでは、ユーザーがツールバーをリセットするかどうかを確認するメッセージ ボックスが表示されます。|使用しません。|使用しません。|使用しません。|
|AFX_WM_RESETTOOLBAR|A`CMFCToolBar`ツールバーは復元元の状態には、リソースから読み込まれたときに、オブジェクトがこのメッセージを送信します。 ツールバーのボタンに同名のクラスから派生した、再挿入するには、このメッセージを処理`CMFCToolbarButton`します。 詳細については、「 `CMFCToolbarComboBoxButton` 」を参照してください。|状態が復元されたツールバーのリソース ID。|使用しません。|0 を返します。|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` オブジェクトは、通常のメニュー ボタンをクリックすると、その所有者にこのメッセージを送信します。 使用するたびにこのメッセージを処理`CMFCToolbarMenuButton`ユーザーがボタンをクリックしたときに、ポップアップ メニューを表示します。|メッセージを送信するボタンのコマンド ID。|カーソルの画面座標。 下位ワードには、x 座標を指定します。 上位ワードには、y 座標を指定します。|使用しません。|
|AFX_WM_TOOLBARMENU|マウス ポインターが、クライアントまたはウィンドウの非クライアント領域内にあるときに、ユーザーがマウスの右ボタンを離したときに、メイン フレーム ウィンドウに送信されます。|使用しません。|マウス ポインターの画面座標。 下位ワードには、x 座標を指定します。 上位ワードには、y 座標を指定します。|アプリケーションは、このメッセージを処理する場合は 0 します。それ以外の場合、0 以外の値。|
|AFX_WM_UPDATETOOLTIPS|ツールヒント コントロールを再作成することを示すために、ツールヒントのすべての所有者に送信します。|このメッセージを処理するコントロールの型。 使用可能な値の一覧は、このトピックの後半の表を参照してください。|使用しません。|使用しません。|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` ユーザーがクリックすると親フレームにこのメッセージを送信、**ヘルプ**クリックするかをクリックしてヘルプ モードに入った、**ヘルプ**キャプション ボタンまたは F1 キーを押します。|使用しません。|インスタンスへのポインター`CMFCWindowsManagerDialog`します。|使用しません。|

次の表は、値の下位ワード、 *lParam* AFX_WM_HSCROLL メソッドのパラメーター。

|||
|-|-|
|[値]|説明|
|SB_ENDSCROLL|ユーザーがスクロールを終了します。|
|SB_LEFT|ユーザーは、左上にスクロールします。|
|SB_RIGHT|ユーザーは、右下にスクロールします。|
|SB_LINELEFT|ユーザーは、1 つの単位で左側をスクロールします。|
|SB_LINERIGHT|ユーザーは、1 単位の右にスクロールします。|
|SB_PAGELEFT|ユーザーは、左ウィンドウの幅をスクロールします。|
|SB_PAGERIGHT|ユーザーでは、ウィンドウの幅に右にスクロールします。|
|SB_THUMBPOSITION|ユーザーがスクロール ボックス (つまみ) をドラッグし、マウス ボタンを解放します。 上位の単語では、ドラッグ操作の最後のスクロール ボックスの位置を示します。|
|SB_THUMBTRACK|ユーザーがスクロール ボックスをドラッグします。 マウス ボタンを離すまで繰り返し AFX_WM_ON_HSCROLL メッセージを送信し、この値を持つされます。 上位の単語は、スクロール ボックスをドラッグした位置を示します。|

> [!NOTE]
>  上位ワード、 *lParam*下位ワードが SB_THUMBPOSITION または SB_THUMBTRACK の場合、パラメーターをスクロール ボックスの現在の位置を指定します。 それ以外の場合、この単語は使用されません。

次の表では、フラグ値の*lParam* AFX_WM_UPDATETOOLTIPS メッセージのパラメーター。

|||
|-|-|
|フラグ|[値]|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0 xffff|

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
