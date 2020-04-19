---
title: タブ コントロールへのタブの追加
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 8915b3af083ebe318e8527b2f83099bf61e7e3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509299"
---
# <a name="adding-tabs-to-a-tab-control"></a>タブ コントロールへのタブの追加

タブコントロール ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) を作成したら、必要な数だけタブを追加します。

### <a name="to-add-a-tab-item"></a>タブ項目を追加するには

1. [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)構造体を準備します。

1. 構造体を渡して、 [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem)を呼び出します。

1. 追加のタブ項目について、手順 1. と手順 2. を繰り返します。

詳細については、「Windows SDK での[タブコントロールの作成](/windows/win32/Controls/tab-controls)」を参照してください。

## <a name="see-also"></a>関連項目

[CTabCtrl の使い方](../mfc/using-ctabctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
