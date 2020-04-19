---
title: '方法: コントロールの追加、編集、またはC++削除 ()'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
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
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: b940e94faf710de8ae5bc604b47dc35a1bc290a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491167"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>方法: コントロールの追加、編集、またはC++削除 ()

ダイアログ**エディター**を使用すると、ダイアログボックス内のコントロールの追加、サイズ変更、編集、および削除を行うことができます。 また、ID などのコントロールのプロパティや、実行時に最初に表示されるかどうかを編集することもできます。

ダイアログエディターで作業している場合は、[[ツールボックス](/visualstudio/ide/reference/toolbox)] ウィンドウに **[ダイアログエディター]** タブが表示されます。 **ツールボックス**ウィンドウをカスタマイズして、簡単に使用できるようにすることもできます。 詳細については、「[ツールボックスの使用](/visualstudio/ide/using-the-toolbox)」および「[ツールボックスウィンドウの表示と非表示](showing-or-hiding-the-dialog-editor-toolbar.md)を切り替える」を参照してください。

> [!TIP]
> **ダイアログエディター**を使用する場合、多くの場合、マウスの右ボタンを選択すると、頻繁に使用するコマンドのショートカットメニューを表示できます。

## <a name="add-controls"></a>コントロールの追加

### <a name="to-add-a-control"></a>コントロールを追加するには

1. ダイアログ ボックスのタブ付きウィンドウがエディター フレーム内の現在のドキュメントであることを確認します。 ダイアログが現在のドキュメントでない場合は、**ツールボックス**に [**ダイアログエディター] タブ**が表示されません。

1. **[ツールボックス]** ウィンドウの **[ダイアログエディター]** タブで、目的のコントロールを選択し、次のいずれかの操作を行います。

   - コントロールを配置する場所でダイアログボックスを選択すると、コントロールが選択した場所に表示されます。

   - コントロールを **[ツールボックス]** ウィンドウからダイアログボックス上の場所にドラッグアンドドロップします。 その後、コントロールを移動したり、サイズと形状を変更したりできます。

   - **[ツールボックス]** ウィンドウでコントロールをダブルクリックすると、ダイアログボックスに表示されます。 コントロールを好きな位置に移動します。

### <a name="to-add-multiple-controls"></a>複数のコントロールを追加するには

1. **Ctrl**キーを押しながら、 **[ツールボックス]** ウィンドウでコントロールを選択します。

1. **Ctrl**キーを離し、特定のコントロールを追加するのと同じ回数だけダイアログボックスを選択します。

1. **Esc**キーを押して、コントロールの配置を停止します。

### <a name="to-size-a-control-while-you-add-it"></a>コントロールを追加するときにサイズを変更するには

1. **[ツールボックス]** ウィンドウでコントロールを選択します。

1. 十字カーソルとして表示されるカーソルを配置します。この場合、新しいコントロールの左上隅がダイアログボックスに表示されます。

1. ダイアログボックス上のコントロールの左上隅を固定するには、マウスボタンを押したままにします。 次に、カーソルを右にドラッグして、コントロールが必要なサイズになるまでドラッグします。

   > [!NOTE]
   > 描画するコントロールの四隅のいずれかを固定することができます。 この手順では、例として左上隅を使用しています。

1. マウスのボタンを離します。 指定したサイズのダイアログボックスにコントロールが表示されます。

> [!TIP]
> コントロールの境界線のサイズ変更ハンドルを移動すると、ダイアログボックスにドロップした後でコントロールのサイズを変更できます。 詳細については、「[個々のコントロールのサイズ変更](../windows/sizing-individual-controls.md)」を参照してください。

### <a name="to-add-a-custom-control"></a>カスタム コントロールを追加するには

ダイアログボックスにカスタムコントロールを追加できます。 **ツールボックス**の **[カスタムコントロール]** アイコンを選択し、ダイアログボックスにドラッグします。 `Syslink`コントロールを追加するには、カスタムコントロールを追加し、コントロールの **[クラス]** `Syslink`プロパティをに変更します。 この操作により、プロパティが更新され、 `Syslink`コントロールのプロパティが表示されます。 MFC ラッパークラスの詳細については、「 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)」を参照してください。

## <a name="edit-controls"></a>コントロールの編集

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>コントロールまたはコントロールのプロパティを編集するには

1. ダイアログボックスで、変更するコントロールを選択します。

   > [!NOTE]
   > 複数のコントロールを選択した場合は、選択したコントロールに共通のプロパティだけを編集できます。

1. [プロパティウィンドウ](/visualstudio/ide/reference/properties-window)で、コントロールのプロパティを変更します。

   > [!NOTE]
   > ボタン、オプションボタン、またはチェックボックスコントロールの**Bitmap**プロパティを**True**に設定すると、スタイル BS_BITMAP がコントロールに対して実装されます。 詳細については、「[ボタンのスタイル](../mfc/reference/styles-used-by-mfc.md#button-styles)」を参照してください。 ビットマップをコントロールに関連付ける例については、「 [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)」を参照してください。 **ダイアログエディター**では、コントロールにビットマップが表示されません。

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>コントロールのプロパティへの変更を元に戻すには

1. **ダイアログエディター**でコントロールにフォーカスがあることを確認します。

1. メニューにアクセスして、 **[元に戻す]** を**編集** > します。 フォーカスがコントロールにない場合、 **[元に戻す]** コマンドは使用できません。

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>ボタン以外のダイアログ ボックス コントロールのメンバー変数を定義するには

> [!NOTE]
> このプロセスは、MFC プロジェクト内のダイアログコントロールにのみ適用されます。 ATL プロジェクトでは、 **[新しい Windows メッセージとイベントハンドラー]** ダイアログボックスを使用する必要があります。 詳細については、「[ユーザーインターフェイスオブジェクトに関連付けられたメッセージ型](../mfc/reference/message-types-associated-with-user-interface-objects.md)」、「[メッセージハンドラーの編集](../mfc/reference/editing-a-message-handler.md)」、および「[リフレクションメッセージ用のメッセージハンドラーの定義](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)」を参照してください。

1. [ダイアログエディター](../windows/dialog-editor.md)で、コントロールを選択します。

1. **Ctrl**キーを押しながら、ダイアログボックスコントロールをダブルクリックします。

   [メンバー変数の追加ウィザード](../ide/add-member-variable-wizard.md)が表示されます。

1. [**メンバー変数の追加**ウィザード] に適切な情報を入力します。 詳細については、「[ダイアログデータエクスチェンジ](../mfc/dialog-data-exchange.md)」を参照してください。

1. **[OK]** を選択して、**ダイアログエディター**に戻ります。

> [!TIP]
> ダイアログ ボックス コントロールから既存のハンドラーにジャンプするには、コントロールをダブルクリックします。

[MFC クラスウィザード](../mfc/reference/mfc-class-wizard.md)の **[メンバー変数]** タブを使用して、指定したクラスの新しいメンバー変数を追加したり、既に定義されているメンバー変数を表示したりすることもできます。

## <a name="delete-controls"></a>コントロールの削除

ダイアログボックスで、コントロールを選択し、 **del**キーを押すか、[メニューの**編集** > ] **[削除]** の順にクリックします。

## <a name="other-issues"></a>その他の問題

### <a name="troubleshooting"></a>トラブルシューティング

コモンコントロールまたはリッチエディットコントロールをダイアログボックスに追加した後は、ダイアログボックスをテストしても表示されません。 または、ダイアログ自体も表示されません。 例えば:

1. Win32 プロジェクトを作成し、アプリケーションの設定を変更して (コンソールアプリケーションではなく) Windows アプリケーションを作成します。

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、 *.rc*ファイルをダブルクリックします。

1. ダイアログオプションの下で、 **[バージョン情報]** ボックスをダブルクリックします。

1. ダイアログボックスに**IP アドレスコントロール**を追加します。

1. すべてを保存して**リビルド**します。

1. プログラムを実行します。

1. ダイアログボックスの **[ヘルプ]** メニューで、 **[バージョン情報]** コマンドを選択して、ダイアログボックスが表示されないことを確認します。

現在、ダイアログ**エディター**では、次のコモンコントロールまたはリッチエディットコントロールをダイアログボックスにドラッグアンドドロップしたときに、プロジェクトにコードが自動的に追加されません。 また、この問題が発生したときに、Visual Studio によってエラーまたは警告が表示されることもありません。 修正するには、コントロールのコードを手動で追加します。

||||
|-|-|-|
|スライダー コントロール|ツリーコントロール|Date Time Picker|
|スピンコントロール|タブコントロール|Month Calendar|
|プログレスコントロール|アニメーションコントロール|IP アドレスの管理|
|ホットキー|リッチエディットコントロール|拡張コンボボックス|
|リストコントロール|リッチエディット2.0 コントロール|カスタム コントロール|

ダイアログボックスでコモンコントロールを使用するには`AFXInitCommonControls` 、ダイアログボックスを作成する前に、 [initcommoncontrolsex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)を呼び出す必要があります。

RichEdit コントロールを使用するには、 `LoadLibrary`を呼び出す必要があります。 詳細については、「Windows SDK の[リッチエディットコントロールについて](/windows/win32/Controls/about-rich-edit-controls)」および「[リッチエディットコントロールの概要](../mfc/overview-of-the-rich-edit-control.md)」を参照してください。

> [!NOTE]
> MFC で RichEdit コントロールを使用するには、まず[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)を呼び出して、Richedit 2.0 コントロール (riched20.dll) を読み込む必要があります。DLL) を呼び出すか、 [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)を呼び出して古い RichEdit 1.0 コントロール (RICHED32) を読み込みます。DLL)。
>
> 古い richedit 1.0 コントロール`CRichEditCtrl`で現在の[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)クラスを使用できますが、は richedit 2.0 コントロールをサポートするように設計されています。 RichEdit 1.0 と RichEdit 2.0 は似ているため、ほとんどのメソッドは動作します。 ただし、1.0 と2.0 のコントロールにはいくつかの違いがあるため、一部のメソッドが正しく機能しないか、まったく動作しない可能性があります。

### <a name="activex-controls"></a>ActiveX コントロール

Visual Studio では、ActiveX コントロールをダイアログ ボックスに挿入することができます。 詳細については、「 [MFC Activex コントロール](../mfc/mfc-activex-controls.md)と[activex コントロールコンテナー](../mfc/activex-control-containers.md)」を参照してください。

**[Activex コントロールの挿入]** ダイアログボックスを使用すると、ダイアログ[エディター](../windows/dialog-editor.md)を使用しているときに、activex コントロールをダイアログボックスに挿入できます。 このダイアログには、次のプロパティが含まれています。

|プロパティ|説明|
|---|---|
|**ActiveX コントロール**|ActiveX コントロールの一覧を表示します。<br/><br/>このダイアログボックスからコントロールを挿入しても、ラッパークラスは生成されません。 ラッパークラスが必要な場合は、[クラスビュー](/visualstudio/ide/viewing-the-structure-of-code)を使用して作成します。「[クラスの追加](../ide/adding-a-class-visual-cpp.md)」を参照してください。<br/><br/>ActiveX コントロールがこのダイアログボックスに表示されない場合は、ベンダーの指示に従ってコントロールをインストールしてみてください。|
|**パス**|ActiveX コントロールが検出されたファイルを表示します。|

> [!CAUTION]
> システム上の ActiveX コントロールの中には、配布が法的に許可されていないものもあります。 コントロールをインストールしたソフトウェアの使用許諾契約書を参照するか、ソフトウェア会社に問い合わせてください。

#### <a name="to-add-an-activex-control"></a>ActiveX コントロールを追加するには

1. ダイアログ**エディター**でダイアログボックスを開きます。

1. ダイアログボックスの本文の任意の場所を右クリックし、 **[ActiveX コントロールの挿入]** を選択します。

   **[Activex コントロールの挿入]** ダイアログボックスが表示され、システム上のすべての ActiveX コントロールが表示されます。 ダイアログ ボックスの下部には、ActiveX コントロール ファイルへのパスが表示されます。

1. ダイアログボックスに追加するコントロールを選択し、[ **OK]** をクリックします。

   コントロールがダイアログ ボックスに表示されます。このダイアログ ボックスで、他のコントロールでするのと同じように、コントロールの編集またはそのハンドラーの作成を行います。

> [!TIP]
> **ダイアログエディター**のショートカットメニューを使用して、登録されている activex コントロールをダイアログボックスにすばやく追加したり、**ツールボックス**ウィンドウに activex コントロールを追加して簡単にアクセスしたりすることができます。

#### <a name="to-edit-properties-for-an-activex-control"></a>ActiveX コントロールのプロパティを編集するには

独立系ベンダーによって提供される ActiveX コントロールには、独自のプロパティと特性が用意されている場合があります。 これらのプロパティは、 **[プロパティ]** ウィンドウに表示されます。 ActiveX コントロールのライターによって作成されたプロパティページは、 **[プロパティページ]** ダイアログボックスに表示されます。 (特定の ActiveX コントロールの**プロパティページ**を表示するには、[プロパティウィンドウ](/visualstudio/ide/reference/properties-window)の **[プロパティページ]** ボタンを選択します)。

- **ActiveX**コントロールを選択し、メニュー**ビュー** > の**プロパティページ**にアクセスして、プロパティを表示します。 必要に応じて、プロパティページで変更を行います。

   Activex コントロールの一部として表示されるプロパティシートに応じて、ActiveX コントロールのプロパティページにはさまざまなタブが表示されます。

> [!NOTE]
> この手順は、プロパティページを使用して ActiveX コントロールを編集する場合に適用されます。 また、[新しい**プロパティ**] ウィンドウで ActiveX プロパティを参照および編集することもできます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログボックスコントロールの管理](controls-in-dialog-boxes.md)<br/>
[方法: レイアウト コントロール](arrangement-of-controls-on-dialog-boxes.md)<br/>
[方法: コントロールのアクセスおよび値を定義する](defining-mnemonics-access-keys.md)

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->