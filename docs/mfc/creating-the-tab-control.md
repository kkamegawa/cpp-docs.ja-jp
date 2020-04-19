---
title: タブ コントロールの作成
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 4627009e2e07d1c5692d83d8d6262a9fcd37977e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241963"
---
# <a name="creating-the-tab-control"></a>タブ コントロールの作成

タブ コントロールを作成する方法は、ダイアログ ボックスで、コントロールの使用または以外のウィンドウで作成するかどうかによって異なります。

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>ダイアログ ボックスで直接 CTabCtrl を使用するには

1. ダイアログ エディターでダイアログ テンプレート リソースをタブ コントロールを追加します。 そのコントロールの ID を指定します

1. 使用して、[メンバー変数の追加ウィザード](../ide/adding-a-member-variable-visual-cpp.md)型のメンバー変数を追加する[CTabCtrl](../mfc/reference/ctabctrl-class.md)コントロール プロパティにします。 このメンバーを使用するには、呼び出しと`CTabCtrl`メンバー関数。

1. 処理する必要がある任意のタブ コントロール通知のメッセージのダイアログ クラスのハンドラー関数にマップします。 詳細については、次を参照してください。[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md)します。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)のスタイルを設定、`CTabCtrl`します。

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>CTabCtrl を以外のウィンドウで使用するには

1. ビューまたはウィンドウのクラスでは、コントロールを定義します。

1. コントロールの呼び出し[作成](../mfc/reference/ctabctrl-class.md#create)メンバー関数は、おそらくで[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)、親ウィンドウの可能性がありますの早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate)いる場合、ハンドラー関数コントロールをサブクラス)。 コントロールのスタイルを設定します。

後に、`CTabCtrl`オブジェクトが作成された、設定または、次の拡張スタイルをオフにすることができます。

- **TCS_EX_FLATSEPARATORS**タブ コントロールは、タブ項目間の区切り記号を描画します。 これは、拡張スタイルのみに影響を持つコントロールのタブ、 **TCS_BUTTONS**と**TCS_FLATBUTTONS**スタイル。 既定では、使用して、タブ コントロールを作成、 **TCS_FLATBUTTONS**スタイルでは、この拡張スタイルを設定します。

- **TCS_EX_REGISTERDROP**タブ コントロールを生成**TCN_GETOBJECT**オブジェクトは、コントロールのタブ項目をドラッグするオブジェクトの通知メッセージをドロップ先を要求します。

    > [!NOTE]
    >  受信する、 **TCN_GETOBJECT** 、通知への呼び出しで OLE ライブラリを初期化する必要があります[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)します。

これらのスタイルを取得して、コントロールが作成されている、それぞれの呼び出しの後に、設定できる、 [GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle)と[SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle)メンバー関数。

たとえば、設定、 **TCS_EX_FLATSEPARATORS**次のコード行のスタイル。

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

クリア、 **TCS_EX_FLATSEPARATORS**スタイルを`CTabCtrl`次のコード行を持つオブジェクト。

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

これにより、区切り記号のボタンの間に表示される、`CTabCtrl`オブジェクト。

## <a name="see-also"></a>関連項目

[CTabCtrl の使い方](../mfc/using-ctabctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
