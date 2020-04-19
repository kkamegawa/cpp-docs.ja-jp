---
title: ツリー コントロールの項目の情報
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: e0eb8af4fbbb6f59c0dda75ec3705183ce916350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407862"
---
# <a name="tree-control-item-information"></a>ツリー コントロールの項目の情報

ツリー コントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) のコントロール内の項目に関する情報を取得するメンバー関数の数があります。 [GetItem](../mfc/reference/ctreectrl-class.md#getitem)メンバー関数は、一部またはすべての項目に関連付けられているデータを取得します。 このデータは、項目のテキスト、状態、イメージ、子項目の数、およびアプリケーション定義の 32 ビット データ値を含めることができます。 [SetItem](../mfc/reference/ctreectrl-class.md#setitem)一部またはすべての項目に関連付けられているデータを設定する関数。

[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)、 [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext)、 [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata)、および[GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage)メンバー関数の個々 の属性を取得します。項目。 これらの各関数は、項目の属性を設定するための対応する Set 関数があります。

[れた](../mfc/reference/ctreectrl-class.md#getnextitem)メンバー関数を現在の項目に指定されたリレーションシップを持つツリー コントロール項目を取得します。 この関数および取得できます、項目の親、次または前に表示される項目、最初子項目にします。 ツリーを走査するメンバー関数もあります。[GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem)、 [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem)、 [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem)、 [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem)、 [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem)、[GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem)、 [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem)、 [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem)、 [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem)、および[GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem)します。

[GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect)メンバー関数は、ツリー コントロールの項目の外接する四角形を取得します。 [GetCount](../mfc/reference/ctreectrl-class.md#getcount)と[GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount)メンバー関数は、ツリー コントロール内の項目の数と、現在表示されているツリー コントロールのウィンドウで、それぞれの項目の数を取得します。 呼び出すことによって、特定の項目が表示されていることを確認することができます、 [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible)メンバー関数。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
