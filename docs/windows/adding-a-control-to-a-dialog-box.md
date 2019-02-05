---
title: コントロールの追加 ダイアログ ボックス (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293625"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>コントロールの追加 ダイアログ ボックス (C++)

**ダイアログ エディター**タブに表示されます、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)作業するとき、**ダイアログ**エディター。 新しいダイアログ ボックスにコントロールを追加するからコントロールをドラッグ、**ツールボックス** ダイアログ ボックスを作成します。 次いでコントロールの移動、またはサイズと形状の変更ができます。

使用できる標準のコントロール、**ツールボックス**は。

- [ボタン コントロール](../mfc/reference/cbutton-class.md)

- [チェック ボックス コントロール](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [コンボ ボックス コントロール](../mfc/reference/ccombobox-class.md)

- [コントロールを編集します。](../mfc/reference/cedit-class.md)

- グループ ボックス

- [リスト ボックス コントロール](../mfc/reference/clistbox-class.md)

- [ラジオ ボタン コントロール](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [スタティック テキスト コントロール](../mfc/reference/cstatic-class.md)

- [画像コントロール](../mfc/reference/cpictureholder-class.md)

- [リッチ エディット 2.0 コントロール](../mfc/using-cricheditctrl.md)

- [スクロール バー コントロール](../mfc/reference/cscrollbar-class.md)

[Windows コモン コントロール](../mfc/controls-mfc.md)で使用できる、**ツールボックス**アプリケーションで高度な機能を提供します。 それには以下が含まれます。

- [スライダー コントロール](../mfc/slider-control-styles.md)

- [スピン コントロール](../mfc/using-cspinbuttonctrl.md)

- [プログレス コントロール](../mfc/styles-for-the-progress-control.md)

- [ホット キー コントロール](../mfc/using-a-hot-key-control.md)

- [リスト コントロール](../mfc/list-control-and-list-view.md)

- [ツリー コントロール](../mfc/tree-control-styles.md)

- [タブ コントロール](../mfc/tab-controls-and-property-sheets.md)

- [アニメーション コントロール](../mfc/using-an-animation-control.md)

- [日時指定コントロール](../mfc/creating-the-date-and-time-picker-control.md)

- [月間予定表コントロールします。](../mfc/month-calendar-control-examples.md)

- [IP アドレス コントロール](../mfc/reference/cipaddressctrl-class.md)

- [拡張コンボ ボックス コントロール](../mfc/creating-an-extended-combo-box-control.md)

- [カスタム コントロール](custom-controls-in-the-dialog-editor.md)

ダイアログ ボックスにカスタム コントロールを追加するには選択して、**カスタム コントロール**アイコン、**ツールボックス**ダイアログ ボックスにドラッグするとします。 追加する、 **Syslink**を制御し、カスタム コントロールを追加、変更、コントロールの**クラス**プロパティを**Syslink**します。 これにより、プロパティを更新し、表示、 **Syslink**プロパティを制御します。 MFC ラッパー クラスについては、次を参照してください。 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)します。

必要な場合も[、ダイアログ ボックスに ActiveX コントロールを追加](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)します。

カスタマイズすることも、**ツールボックス**ウィンドウを簡単に使用します。 詳細については、「[ツールボックスの使用](/visualstudio/ide/using-the-toolbox)」を参照してください。

使用しての詳細については、 **RichEdit 1.0** MFC でコントロールを参照してください[MFC での RichEdit 1.0 コントロールの使用](../windows/using-the-richedit-1-0-control-with-mfc.md)

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-add-a-control-to-a-dialog-box"></a>ダイアログ ボックスにコントロールを追加するには

1. ダイアログ ボックスのタブ付きウィンドウがエディター フレーム内の現在のドキュメントであることを確認します。 ダイアログ ボックスが現在のドキュメントでない場合は表示されません、**ダイアログ エディターのタブ**で、**ツールボックス**します。

1. **ダイアログ エディター**のタブ、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)、し、目的のコントロールを選択します。

   - コントロールを配置する場所 ダイアログ ボックスを選択します。 選択したコントロールが表示されます。

       \- または -

   - ドラッグ アンド ドロップのコントロール、**ツールボックス**ウィンドウ、ダイアログ ボックス上の場所にします。

       \- または -

   - コントロールをダブルクリック、**ツールボックス**ウィンドウ (ダイアログ ボックスに表示) したい場所にコントロールを再配置します。

## <a name="to-add-multiple-controls"></a>複数のコントロールを追加するには

1. 押しながら、 **Ctrl**キーでコントロールを選び、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)します。

1. リリース、 **Ctrl**キーを何度でも、特定のコントロールを追加すると、ダイアログ ボックスを選択します。

1. キーを押して**Esc**コントロールの配置を停止します。

## <a name="to-size-a-control-while-you-add-it"></a>追加するコントロールのサイズ

1. コントロールを選び、[ツールボックス ウィンドウ](/visualstudio/ide/reference/toolbox)します。

1. ダイアログ ボックスで、新しいコントロールの左上隅となる (これに十字が表示されます)、カーソルを置きます。

1. 選択し、ダイアログ ボックスで、コントロールの左上隅に固定するマウス ボタンを押したまま、目的のサイズになるまで、右、下にカーソルをドラッグします。

   > [!NOTE]
   > 実際に描画するコントロールの四隅のいずれかを固定できます。 この手順では、例として、左上隅にあるを使用します。

1. マウスのボタンを離します。 指定したサイズでダイアログ ボックスにコントロールが配置されます。

   > [!TIP]
   > コントロールのサイズを変更するには、コントロールの境界線にサイズ変更ハンドルを移動することによって、ダイアログ ボックスの上にドロップするとします。 詳細については、次を参照してください。[個々 のコントロールをサイズ変更](../windows/sizing-individual-controls.md)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[ダイアログ ボックス コントロールへのイベント ハンドラーの追加](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[ダイアログ ボックス コントロールおよび変数の型](../ide/dialog-box-controls-and-variable-types.md)<br/>
[コントロール](../mfc/controls-mfc.md)<br/>
[コントロール クラス](../mfc/control-classes.md)<br/>
[ダイアログ ボックス クラス](../mfc/dialog-box-classes.md)<br/>
[スクロール バー スタイル](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[リッチ エディット コントロールの例](../mfc/rich-edit-control-examples.md)<br/>
