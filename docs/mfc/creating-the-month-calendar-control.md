---
title: 月間予定表コントロールの作成
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 9e430a86c2ac08bde0f031a4c91b9ae5c6f570f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907502"
---
# <a name="creating-the-month-calendar-control"></a>月間予定表コントロールの作成

月間予定表コントロールの作成方法は、ダイアログボックスでコントロールを使用しているか、nondialog ウィンドウで作成したかによって異なります。

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>ダイアログボックスで CMonthCalCtrl を直接使用するには

1. ダイアログエディターで、ダイアログテンプレートリソースに月間予定表コントロールを追加します。 コントロール ID を指定します。

1. 月間予定表コントロールの [プロパティ] ダイアログボックスを使用して、必要なスタイルを指定します。

1. [メンバー変数の追加ウィザード](../ide/adding-a-member-variable-visual-cpp.md)を使用して、 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)型のメンバー変数をコントロールプロパティに追加します。 このメンバーを使用して、 `CMonthCalCtrl`メンバー関数を呼び出すことができます。

1. [クラスウィザード](reference/mfc-class-wizard.md)を使用すると、処理する必要がある月間予定表コントロールの通知メッセージのダイアログクラスのハンドラー関数をマップできます (「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください)。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)で、 `CMonthCalCtrl`オブジェクトの追加のスタイルを設定します。

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Nondialog ウィンドウで CMonthCalCtrl を使用するには

1. ビューまたはウィンドウクラスでコントロールを定義します。

1. コントロールの Create member 関数を呼び出します。これは、おそらく親ウィンドウの[OnCreate](../mfc/reference/cwnd-class.md#oncreate) handler 関数 (コントロールをサブクラス化している場合) のように、 [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)で[作成](../mfc/reference/cmonthcalctrl-class.md#create)します。 コントロールのスタイルを設定します。

## <a name="see-also"></a>関連項目

[CMonthCalCtrl の使い方](../mfc/using-cmonthcalctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
