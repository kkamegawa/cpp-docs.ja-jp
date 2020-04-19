---
title: 日時指定コントロールの作成
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: de9baf63577d163b82da1c5977a6ccba6539c73a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907604"
---
# <a name="creating-the-date-and-time-picker-control"></a>日時指定コントロールの作成

日付と時刻の選択コントロールの作成方法は、ダイアログボックスでコントロールを使用するか、nondialog ウィンドウで作成するかによって異なります。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>ダイアログボックスで Cdatetimectrl 使い方を直接使用するには

1. ダイアログエディターで、[日付と時刻の選択] コントロールをダイアログテンプレートリソースに追加します。 コントロール ID を指定します。

1. [日付と時刻の選択] コントロールの [プロパティ] ダイアログボックスを使用して、必要なスタイルを指定します。

1. [メンバー変数の追加ウィザード](../ide/adding-a-member-variable-visual-cpp.md)を使用して、 [cdatetimectrl 使い方](../mfc/reference/cdatetimectrl-class.md)型のメンバー変数をコントロールプロパティに追加します。 このメンバーを使用して、 `CDateTimeCtrl`メンバー関数を呼び出すことができます。

1. [クラスウィザード](reference/mfc-class-wizard.md)を使用すると、処理する必要がある任意の日時指定コントロールの[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)メッセージのダイアログクラスのハンドラー関数をマップできます (「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください)。

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)で、 `CDateTimeCtrl`オブジェクトの追加のスタイルを設定します。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Nondialog ウィンドウで Cdatetimectrl 使い方を使用するには

1. ビューまたはウィンドウクラスでコントロールを宣言します。

1. コントロールの Create member 関数を呼び出します。これは、おそらく親ウィンドウの[OnCreate](../mfc/reference/cwnd-class.md#oncreate) handler 関数 (コントロールをサブクラス化している場合) のように、 [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)で[作成](../mfc/reference/ctabctrl-class.md#create)します。 コントロールのスタイルを設定します。

## <a name="see-also"></a>関連項目

[CDateTimeCtrl の使い方](../mfc/using-cdatetimectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
