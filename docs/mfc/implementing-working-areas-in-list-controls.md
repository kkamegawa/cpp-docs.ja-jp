---
title: リスト コントロールの作業領域の実装
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 01b166243c9032a113d46ff297b9f6e53429da21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297217"
---
# <a name="implementing-working-areas-in-list-controls"></a>リスト コントロールの作業領域の実装

既定では、リスト コントロールは、標準的なグリッドのすべてのアイテムを整列します。 ただし、別の方法がサポートされて、作業領域で、リスト アイテムを四角形のグループに配置します。 作業領域を実装するリスト コントロールのイメージは、Windows SDK でリスト ビュー コントロールの使用を参照してください。

> [!NOTE]
>  作業領域は、リスト コントロールがアイコンまたは小さいアイコンのモードである場合にのみ表示されます。 ただし、ビューがレポートまたはリスト モードに切り替えられた場合、現在の作業領域が維持されます。

作業領域 (上、左、上およびアイテムの右側)、空の境界線を表示させたり、水平スクロール バーが通常はいずれかを指定すると表示に使用できます。 もう 1 つの一般的な使用方法では、複数の作業領域を項目に移動したり、削除を作成します。 この方法で異なる意味を持つ 1 つのビューで領域を作成できます。 ユーザー別の領域に置くことで、項目を分類します。 この例は、読み取り/書き込みファイルの領域と読み取り専用ファイルの別の領域を持つファイル システムのビューになります。 ファイルの項目は、読み取り専用領域に移動された場合は自動的になる場合が読み取り専用です。 読み取り専用領域から読み取り/書き込み領域にファイルの移動を読み取り/書き込みファイルとなります。

`CListCtrl` 作成およびリスト コントロールでの作業領域を管理するためには、いくつかのメンバー関数を提供します。 [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas)と[SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas)取得および設定の配列`CRect`オブジェクト (または`RECT`構造体)、リスト コントロールの現在の実装の作業領域を格納します。 さらに、 [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas)リスト コントロールの作業領域の現在の数を取得します (既定では、0)。

## <a name="items-and-working-areas"></a>項目し、作業領域

作業領域が作成されると、作業領域内にある項目のメンバーになります。 同様に、作業領域に項目を移動すると、移動先となる作業領域のメンバーがなります。 どの作業領域に項目が重ならない場合は、最初の (インデックス 0) の作業領域のメンバーが自動的になります。 項目を作成して、それを特定の作業領域内に配置する場合をへの呼び出しに必要な作業領域に移動して、項目を作成する必要があります。 [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)します。 次の 2 つ目の例では、この手法を示します。

次の例では、次の 4 つの作業領域の実装 (`rcWorkAreas`)、10 ピクセル幅のリスト コントロール内のそれぞれの作業領域境界線と等しいサイズの (`m_WorkAreaListCtrl`)。

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

呼び出し[例で](../mfc/reference/clistctrl-class.md#approximateviewrect)を 1 つのリージョンにすべての項目を表示するために必要な合計領域の推定値を取得しました。 この見積もりは、4 つのリージョンに分割され、5 ピクセル幅の枠線で埋められます。

次の例では、既存のリスト アイテムを各グループに割り当てられます (`rcWorkAreas`) コントロールのビューを更新します (`m_WorkAreaListCtrl`) 効果を完了します。

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
