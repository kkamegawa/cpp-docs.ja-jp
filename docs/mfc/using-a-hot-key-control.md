---
title: ホット キー コントロールの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: d9178fe989e476111a3da55861642e9aa6311872
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180532"
---
# <a name="using-a-hot-key-control"></a>ホット キー コントロールの使い方

ホット キー コントロールの一般的な使用方法では、次のパターンに従います。

- コントロールが作成されます。 コントロールがダイアログ ボックスのテンプレートで指定されている場合、ダイアログ ボックスが作成されると作成は自動です。 (必要、 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)ホット キー コントロールに対応するダイアログ クラスのメンバーです)。また、使用することができます、[作成](../mfc/reference/chotkeyctrl-class.md#create)メンバー関数は、すべてのウィンドウの子ウィンドウとして、コントロールを作成します。

- コントロールの既定値を設定する場合は、呼び出し、 [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey)メンバー関数。 特定のシフト状態を禁止する場合は、呼び出す[SetRules](../mfc/reference/chotkeyctrl-class.md#setrules)します。 これを行う適切な時刻は ダイアログ ボックスで、[コントロール] ダイアログ ボックスの[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)関数。

- ユーザーは、ホット キー コントロールにフォーカスがある場合は、ホット キーの組み合わせを押すと、コントロールと対話します。 ユーザー、何らかの方法であることを示しますこのタスク完了すると、おそらく ダイアログ ボックスのボタンをクリックしています。

- メンバー関数を使用するときに、プログラムには、ユーザーのホット キーが選択されている通知、 [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)ホット キー コントロールから、仮想キーと shift キーの状態の値を取得します。

- 説明する方法のいずれかを使用して、ホット キーを設定することができます、ユーザーが選択したキーがわかったら、[ホット キーの設定](../mfc/setting-a-hot-key.md)します。

- ホット キー コントロールがダイアログ ボックスでは、場合、および`CHotKeyCtrl`オブジェクトが自動的に破棄されます。 かどうか、する必要があることに、両方のコントロールを確認し、`CHotKeyCtrl`オブジェクトが破棄されました。

## <a name="see-also"></a>関連項目

[CHotKeyCtrl の使い方](../mfc/using-chotkeyctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
