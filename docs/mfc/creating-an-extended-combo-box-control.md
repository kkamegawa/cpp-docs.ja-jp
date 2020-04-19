---
title: 拡張コンボ ボックス コントロールの作成
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907732"
---
# <a name="creating-an-extended-combo-box-control"></a>拡張コンボ ボックス コントロールの作成

拡張コンボボックスコントロールの作成方法は、ダイアログボックスでコントロールを使用しているか、nondialog ウィンドウで作成したかによって異なります。

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>ダイアログボックスで CComboBoxEx を直接使用するには

1. ダイアログエディターで、ダイアログテンプレートリソースに拡張コンボボックスコントロールを追加します。 コントロール ID を指定します。

1. 拡張コンボボックスコントロールの [プロパティ] ダイアログボックスを使用して、必要なスタイルを指定します。

1. [メンバー変数の追加ウィザード](../ide/adding-a-member-variable-visual-cpp.md)を使用して、 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)型のメンバー変数をコントロールプロパティに追加します。 このメンバーを使用して、 `CComboBoxEx`メンバー関数を呼び出すことができます。

1. [クラスウィザード](reference/mfc-class-wizard.md)を使用して、処理する必要がある拡張コンボボックスコントロールの通知メッセージのダイアログクラスのハンドラー関数をマップします (「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください)。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)で、 `CComboBoxEx`オブジェクトの追加のスタイルを設定します。

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Nondialog ウィンドウで CComboBoxEx を使用するには

1. ビューまたはウィンドウクラスでコントロールを定義します。

1. [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)のように、コントロールの[Create](../mfc/reference/ctabctrl-class.md#create) member 関数を呼び出します (おそらく、親ウィンドウの[OnCreate](../mfc/reference/cwnd-class.md#oncreate) handler 関数と同じようにします)。 コントロールのスタイルを設定します。

## <a name="see-also"></a>関連項目

[CComboBoxEx の使い方](../mfc/using-ccomboboxex.md)<br/>
[コントロール](../mfc/controls-mfc.md)
