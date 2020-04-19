---
title: ヘッダー コントロールの項目の並べ替え
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: bae351d921c25993d6b7029f9052e1938179673b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392651"
---
# <a name="ordering-items-in-the-header-control"></a>ヘッダー コントロールの項目の並べ替え

すると[ヘッダー コントロールに項目を追加](../mfc/adding-items-to-the-header-control.md)、操作するか、次の関数では、その順序に関する情報を取得します。

- [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray)と[CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   取得し、ヘッダー項目の左から右の順序を設定します。

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex)します。

   特定のヘッダー項目のインデックス値を取得します。

に加えて、前のメンバー関数は、HDS_DRAGDROP 形式は、ドラッグ アンド ドロップのヘッダー コントロールのヘッダー項目にユーザーをできます。 詳細については、次を参照してください。[ヘッダー項目に対するドラッグ アンド ドロップのサポートを提供する](../mfc/providing-drag-and-drop-support-for-header-items.md)します。

## <a name="see-also"></a>関連項目

[CHeaderCtrl の使い方](../mfc/using-cheaderctrl.md)
