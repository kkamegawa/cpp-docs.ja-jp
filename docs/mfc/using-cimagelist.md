---
title: CImageList の使い方
ms.date: 11/04/2016
f1_keywords:
- CImageList
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: c3e4cec75ce23beb2a617d672170f86c608ca0a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411839"
---
# <a name="using-cimagelist"></a>CImageList の使い方

イメージ リストは、クラスによって表される[CImageList](../mfc/reference/cimagelist-class.md)、それぞれのインデックスを使用してを参照できます、同じサイズのイメージのコレクションです。 イメージ リストを使用して、アイコンまたはビットマップの大規模なセットを効率的に管理できます。 イメージ リスト ウィンドウではないためにコントロール自体ではありませんがただし、コントロール、リスト コントロールを含むのさまざまな種類で使用されます ([CListCtrl](../mfc/reference/clistctrl-class.md))、ツリー コントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))、タブ コントロールと ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。

イメージ リストのすべてのイメージは、単一のワイド画面デバイス形式のビットマップに格納されます。 イメージ リストは、透過的にイメージを描画するために使用されるマスク (アイコンのスタイル) を含むモノクロ ビットマップを含めることもできます。 `CImageList` メンバー関数を使用すると、イメージの描画、作成しイメージ リストを破棄、追加しイメージを削除する、イメージの置換、イメージのマージ、およびイメージのドラッグを提供します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [イメージ リストの種類](../mfc/types-of-image-lists.md)

- [イメージ リストの使い方](../mfc/using-an-image-list.md)

- [イメージ リストの操作](../mfc/manipulating-image-lists.md)

- [イメージ リストのイメージの描画](../mfc/drawing-images-from-an-image-list.md)

- [イメージ リストのイメージのオーバーレイ](../mfc/image-overlays-in-image-lists.md)

- [イメージ リストのイメージのドラッグ](../mfc/dragging-images-from-an-image-list.md)

- [イメージ リストのイメージ情報](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>関連項目

[コントロール](../mfc/controls-mfc.md)
