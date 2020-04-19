---
title: コールバック項目とコールバック マスク
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509139"
---
# <a name="callback-items-and-the-callback-mask"></a>コールバック項目とコールバック マスク

リストビューコントロールは、各項目について、通常、ラベルテキスト、項目のアイコンのイメージリストインデックス、および項目の状態に対する一連のビットフラグを格納します。 個々の項目をコールバック項目として定義できます。これは、アプリケーションが項目の情報の一部を既に格納している場合に便利です。

項目をコールバック項目として定義するには、 `pszText` `LVITEM`構造体`iImage`のメンバーとメンバーに適切な値を指定します (「 [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)」を参照)。 アプリケーションが項目またはサブ項目のテキストを保持している場合は、 `pszText`メンバーの LPSTR_TEXTCALLBACK 値を指定します。 アプリケーションが項目のアイコンを追跡し続ける場合は、 `iImage`メンバーの**I_IMAGECALLBACK**値を指定します。

コールバック項目を定義するだけでなく、コントロールのコールバックマスクを変更することもできます。 このマスクは、コントロールではなく、アプリケーションが現在のデータを格納する項目の状態を指定するビットフラグのセットです。 コールバックマスクは、特定の項目に適用されるコールバック項目の指定とは異なり、コントロールのすべての項目に適用されます。 既定では、コールバックマスクは0です。これは、コントロールがすべての項目の状態を追跡することを意味します。 この既定の動作を変更するには、マスクを次の値の任意の組み合わせに初期化します。

- **LVIS_CUT**切り取りと貼り付けの操作用に項目がマークされています。

- **LVIS_DROPHILITED**項目はドラッグアンドドロップのターゲットとして強調表示されます。

- **LVIS_FOCUSED**項目にフォーカスがあります。

- **LVIS_SELECTED**項目が選択されています。

- **LVIS_OVERLAYMASK**アプリケーションは、各項目の現在のオーバーレイイメージのイメージリストインデックスを格納します。

- **LVIS_STATEIMAGEMASK**アプリケーションは、各項目の現在の状態イメージのイメージリストインデックスを格納します。

このマスクの取得と設定の詳細については、「 [clistctrl:: GetSetCallbackMask mask](../mfc/reference/clistctrl-class.md#getcallbackmask) 」および「 [Clistctrl::](../mfc/reference/clistctrl-class.md#setcallbackmask)」を参照してください。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](../mfc/using-clistctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
