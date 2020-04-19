---
title: ダイアログ ボックス コントロール (C++) |Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 568754bc514ae017293805fab1b25849d5ffe5f8
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400881"
---
# <a name="dialog-box-controls-c"></a>ダイアログ ボックス コントロール (C++)

コントロールを使用して、ダイアログ ボックスを追加することができます、**ダイアログ エディター**  タブで、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox) ダイアログ ボックスにドラッグしてコントロールを選択することができます。 既定で、**ツールボックス**ウィンドウ自動非表示に設定されます。 ソリューションの左側の余白のタブとして表示されるときに、**ダイアログ エディター**が開いています。 ただし、ピン留めできます、**ツールボックス**ウィンドウ位置を選択して、**自動的に隠す**ウィンドウの右上隅のボタンをクリックします。 このウィンドウの動作を制御する方法の詳細については、次を参照してください。[ウィンドウ管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)します。

ダイアログ ボックスにコントロールを追加、既存のコントロールの位置を変更または 1 つのダイアログ ボックスから、コントロールを移動する最も簡単な方法では、ドラッグ アンド ドロップを使用します。 ダイアログ ボックスに、削除されるまで、コントロールの位置は点線で囲まれます。 ドラッグ アンド ドロップしてダイアログ ボックスにコントロールを追加すると、コントロールには、その種類のコントロールに適切な標準の高さが与えられます。

ガイドや、余白によって決定されます、最終的な配置 ダイアログ ボックスにコントロールを追加または位置を変更するときまたはレイアウト グリッドをオンにする必要があるかどうか。

キャプションなどのプロパティを変更するには、ダイアログ ボックスにコントロールを追加した後、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。 複数のコントロールを選択し、それらのプロパティをすべて一度に変更できます。

詳細については、**ダイアログ エディター**を参照してください方法[追加、編集、または削除コントロール](adding-editing-or-deleting-controls.md)、[レイアウト コントロール](../windows/arrangement-of-controls-on-dialog-boxes.md)、および[コントロール アクセスの定義と値](../windows/defining-mnemonics-access-keys.md).

コントロールとダイアログ ボックスの詳細については、次を参照してください。[コントロール クラス](../mfc/control-classes.md)、[ダイアログ ボックス クラス](../mfc/dialog-box-classes.md)、および[スクロール バー スタイル](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)します。

使用できる標準のコントロール、**ツールボックス**イベントは、既定値。

|コントロール名|既定のイベント|
|---|---|
|[ボタン コントロール](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[チェック ボックス コントロール](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[コンボ ボックス コントロール](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[コントロールを編集します。](../mfc/reference/cedit-class.md)|EN_CHANGE|
|グループ ボックス|(該当なし)|
|[リスト ボックス コントロール](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[ラジオ ボタン コントロール](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[スタティック テキスト コントロール](../mfc/reference/cstatic-class.md)|(該当なし)|
|[画像コントロール](../mfc/reference/cpictureholder-class.md)|(該当なし)|
|[リッチ エディット 2.0 コントロール](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[スクロール バー コントロール](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> 使用しての詳細については、 **RichEdit 1.0** MFC でコントロールを参照してください[MFC での RichEdit 1.0 コントロールの使用](../windows/using-the-richedit-1-0-control-with-mfc.md)と[リッチ エディット コントロールの例](../mfc/rich-edit-control-examples.md)します。

[Windows コモン コントロール](../mfc/controls-mfc.md)で使用できる、**ツールボックス**拡張機能を提供します。

|コントロール名|既定のイベント|
|---|---|
|[スライダー コントロール](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[スピン コントロール](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[プログレス コントロール](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[ホット キー コントロール](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[リスト コントロール](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[ツリー コントロール](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[タブ コントロール](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[アニメーション コントロール](../mfc/using-an-animation-control.md)|ACN_START|
|[日時指定コントロール](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[月間予定表コントロールします。](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP アドレス コントロール](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[拡張コンボ ボックス コントロール](../mfc/creating-an-extended-combo-box-control.md)||
|カスタム コントロール|TTN_GETDISPINFO|

## <a name="custom-controls"></a>カスタム コントロール

**ダイアログ エディター**では、既存のカスタムまたはダイアログ ボックスのテンプレートでユーザー コントロール。

> [!NOTE]
> この意味でのカスタム コントロールでは、ActiveX コントロールと混同しないようにします。 ActiveX コントロールがカスタムの OLE コントロールとも呼ばれます。 また、Windows でオーナー描画コントロールでこれらのコントロールを混同しないでください。

この機能は、Windows によって提供されるもの以外のコントロールを使用することができます。 実行時に、コントロールは、ウィンドウ クラス (いないのと同じ C++ クラス) に関連付けられます。 同じタスクを実行する一般的な方法では、ダイアログ ボックスで、静的コントロールなどの任意のコントロールをインストールします。 実行時で、 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)機能、そのコントロールを削除し、独自のカスタム コントロールに置き換えます。

> [!NOTE]
> これは、以前の技術です。 今すぐ ActiveX コントロールまたは Windows のコモン コントロールのサブクラスを作成するほとんどの場合に推奨します。

これらのカスタム コントロール用に限定されます。

- ダイアログ ボックスで、場所を設定します。

- キャプションを入力します。

- コントロールの Windows クラスの名前を識別するため、アプリケーション コードは、この名前でコントロールを登録する必要があります。

- コントロールのスタイルを設定する 32 ビット 16 進値を入力します。

- 拡張スタイルを設定します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ エディター](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->