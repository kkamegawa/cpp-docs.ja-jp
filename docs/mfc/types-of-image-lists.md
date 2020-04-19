---
title: イメージ リストの種類
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180851"
---
# <a name="types-of-image-lists"></a>イメージ リストの種類

イメージ リストの 2 種類があります ([CImageList](../mfc/reference/cimagelist-class.md)): マスクとマスク。 「マスクされていないイメージ リスト」は、1 つまたは複数のイメージを含むカラー ビットマップで構成されます。 「マスクされたイメージ一覧」は、等しいサイズの 2 つのビットマップで構成されます。 色のビットマップ イメージを含む 1 つ目は、2 番目の一連のマスクを含むモノクロ ビットマップ、ビットマップ内の各イメージのいずれか。

オーバー ロードの 1 つ、`Create`メンバー関数は、イメージ リストをマスクするかどうかを示すフラグを受け取ります。 (他のオーバー ロードは、マスクされたイメージのリストを作成します)。

マスクされていないイメージが描画されるときに、ターゲット デバイス コンテキストにコピーされます。つまり、デバイス コンテキストの既存の背景色の上に描画されます。 マスクされたイメージが描画されるときに、イメージのビットは、通常、ビットマップ内の透明な領域を作成、ターゲット デバイス コンテキストの背景色が透けて、マスクのビットと結合されます。 マスクされたイメージを描画するときに、いくつかの描画スタイルを指定できます。 たとえば、イメージは、選択したオブジェクトを示すディザーをかけることを指定できます。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)
