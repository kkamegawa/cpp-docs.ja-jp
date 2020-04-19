---
title: コントロールへの項目の追加
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 6c03be6f04746ec2e3146916d72cad637a204187
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509334"
---
# <a name="adding-items-to-the-control"></a>コントロールへの項目の追加

リストコントロール ([CListCtrl](../mfc/reference/clistctrl-class.md)) に項目を追加するには、使用している情報に応じて、いくつかのバージョンの[InsertItem](../mfc/reference/clistctrl-class.md#insertitem)メンバー関数のいずれかを呼び出します。 1つのバージョンでは、準備する[LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw)構造体が使用されます。 構造体`LVITEM`には多数のメンバーが含まれているため、リストコントロール項目の属性をより詳細に制御できます。

`LVITEM`構造体の2つの重要なメンバー (レポートビューに関して) `iItem`は`iSubItem` 、メンバーとメンバーです。 メンバーは、構造体が参照`iSubItem`している項目の0から始まるインデックスであり、メンバーはサブ項目の1から始まるインデックスです。また、構造体に項目に関する情報が含まれている場合は0になります。 `iItem` この2つのメンバーを使用して、項目ごとに、リストコントロールがレポートビューであるときに表示されるサブ項目情報の型と値を決定します。 詳細については、「 [CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem)」を参照してください。

追加のメンバーは、項目のテキスト、アイコン、状態、および項目データを指定します。 "Item data" は、リストビューアイテムに関連付けられたアプリケーション定義の値です。 構造体の`LVITEM`詳細については、「 [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)」を参照してください。

他のバージョン`InsertItem`の`LVITEM`では、構造体のメンバーに対応する1つ以上の個別の値を受け取ります。これにより、サポートするメンバーだけを初期化できます。 一般に、リストコントロールはリスト項目のストレージを管理しますが、"コールバック項目" を使用して、情報の一部をアプリケーションに格納することができます。 詳細については、このトピックの「[コールバック項目と](../mfc/callback-items-and-the-callback-mask.md)コールバックマスク」、および「Windows SDK のコールバック[項目と](/windows/win32/Controls/using-list-view-controls)コールバックマスク」を参照してください。

詳細については、「[リストビューの項目と](/windows/win32/Controls/using-list-view-controls)サブ項目の追加」を参照してください。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
