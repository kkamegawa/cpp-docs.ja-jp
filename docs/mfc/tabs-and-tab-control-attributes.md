---
title: タブおよびタブ コントロールの属性
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511243"
---
# <a name="tabs-and-tab-control-attributes"></a>タブおよびタブ コントロールの属性

タブコントロール ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) を構成するタブの外観と動作をかなり細かく制御できます。 各タブには、ラベル、アイコン、項目の状態、およびアプリケーションによって定義された32ビット値が関連付けられています。 各タブには、アイコン、ラベル、またはその両方を表示できます。

さらに、各タブ項目には、押された状態、unpressed、または強調表示された3つの状態があります。 この状態は、既存のタブ項目を変更することによってのみ設定できます。 既存のタブ項目を変更するには、 [GetItem](../mfc/reference/ctabctrl-class.md#getitem)の呼び出しを使用して`TCITEM`取得し、構造体 (具体的には*dwstate*と*dwStateMask*のデータメンバー) `TCITEM`を変更してから、を呼び出して変更された構造体を返します。[SetItem](../mfc/reference/ctabctrl-class.md#setitem)。 `CTabCtrl`オブジェクト内のすべてのタブ項目の項目の状態をクリアする必要がある場合は、の[呼び出しを行います。](../mfc/reference/ctabctrl-class.md#deselectall) この関数は、現在選択されている項目を除くすべてのタブ項目またはすべての項目の状態をリセットします。

次のコードは、すべてのタブ項目の状態をクリアし、3番目の項目の状態を変更します。

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

タブ属性の詳細については、Windows SDK の「[タブおよびタブ属性](/windows/win32/Controls/tab-controls)」を参照してください。 タブコントロールへのタブの追加の詳細については、このトピックの「[タブコントロールへ](../mfc/adding-tabs-to-a-tab-control.md)のタブの追加」を参照してください。

## <a name="see-also"></a>関連項目

[CTabCtrl の使い方](../mfc/using-ctabctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
