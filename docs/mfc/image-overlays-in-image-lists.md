---
title: イメージ リストのイメージのオーバーレイ
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508383"
---
# <a name="image-overlays-in-image-lists"></a>イメージ リストのイメージのオーバーレイ

すべてのイメージリスト ([CImageList](../mfc/reference/cimagelist-class.md)) には、オーバーレイマスクとして使用するイメージの一覧が含まれています。 "オーバーレイマスク" は、別のイメージに対して透過的に描画されるイメージです。 任意のイメージをオーバーレイマスクとして使用できます。 イメージリストごとに最大4つのオーバーレイマスクを指定できます。

オーバーレイマスクの一覧にイメージのインデックスを追加するには、 [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)メンバー関数、イメージのインデックス、およびオーバーレイマスクのインデックスを使用します。 オーバーレイマスクのインデックスは、0から始まるのではなく、1から始まることに注意してください。

の1回の呼び出し`Draw`を使用して、イメージにオーバーレイマスクを描画します。 パラメーターには、描画するイメージのインデックスとオーバーレイマスクのインデックスが含まれます。 オーバーレイマスクのインデックスを指定するには、 [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)マクロを使用する必要があります。 [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)メンバー関数を呼び出すときに、オーバーレイイメージを指定することもできます。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)
