---
title: ツリー コントロールの親項目と子項目
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513962"
---
# <a name="tree-control-parent-and-child-items"></a>ツリー コントロールの親項目と子項目

ツリーコントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 内のすべての項目には、子項目と呼ばれるサブ項目のリストが関連付けられています。 1つ以上の子項目を持つ項目を親項目と呼びます。 子項目は親項目の下に表示され、親の下位要素であることを示すためにインデントされます。 親を持たないアイテムは、階層の最上位にあり、ルートアイテムと呼ばれます。

任意の時点で、親項目の子項目のリストの状態を展開または折りたたむことができます。 状態が展開されると、子項目が親項目の下に表示されます。 折りたたまれている場合、子項目は表示されません。 ユーザーが親項目をダブルクリックすると、展開された状態と折りたたまれた状態が自動的に切り替わります。親が**TVS_HASBUTTONS**の場合は、ユーザーが親項目に関連付けられているボタンをクリックしたときに表示されます。 アプリケーションでは、 [expand](../mfc/reference/ctreectrl-class.md#expand)メンバー関数を使用して子項目を展開または折りたたむことができます。

項目をツリーコントロールに追加するには、 [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)メンバー関数を呼び出します。 この関数は、項目を一意に識別する**HTREEITEM**型のハンドルを返します。 項目を追加するときは、新しい項目の親項目のハンドルを指定する必要があります。 [TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) structure または*hparent*パラメーターで親項目ハンドルの代わりに**NULL**または**TVI_ROOT**値を指定すると、項目がルート項目として追加されます。

親項目の子項目のリストが展開または折りたたまれようとしているときに、ツリーコントロールは[TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding)通知メッセージを送信します。 通知を使用すると、子項目の一覧の状態に依存する親項目の属性を変更したり、設定したりすることができます。 リストの状態を変更すると、ツリーコントロールは[TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded)通知メッセージを送信します。

子項目のリストが展開されると、親項目に対して相対的にインデントされます。 インデントの量を設定するには、 [Setindent](../mfc/reference/ctreectrl-class.md#setindent)メンバー関数を使用するか、 [getindent](../mfc/reference/ctreectrl-class.md#getindent)メンバー関数を使用して現在の量を取得します。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
