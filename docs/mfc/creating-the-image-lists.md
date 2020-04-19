---
title: イメージ リストの作成
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508786"
---
# <a name="creating-the-image-lists"></a>イメージ リストの作成

[CListView](../mfc/reference/clistview-class.md)と[CListCtrl](../mfc/reference/clistctrl-class.md)のどちらを使用する場合でも、イメージリストの作成は同じです。

> [!NOTE]
>  リストコントロールに`LVS_ICON`スタイルが含まれている場合にのみ、イメージリストが必要になります。

クラス`CImageList`を使用して、1つまたは複数のイメージリストを作成します (フルサイズのアイコン、小さいアイコン、状態)。 「 [CImageList](../mfc/reference/cimagelist-class.md)」を参照し、Windows SDK の[リストビューのイメージリスト](/windows/win32/Controls/using-list-view-controls)を参照してください。

各イメージリストに対して、 [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist)を呼び出します。適切な`CImageList`オブジェクトへのポインターを渡します。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
