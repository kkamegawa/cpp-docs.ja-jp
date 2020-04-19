---
title: プログレス コントロールの操作
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279191"
---
# <a name="manipulating-the-progress-control"></a>プログレス コントロールの操作

プログレス コントロールの現在位置を変更する 3 つの方法はあります ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md))。

- 事前設定された増分で位置を変更できます。

- 位置は、任意の量によって変更できます。

- 位置は、特定の値に変更できます。

### <a name="to-change-the-position-by-a-preset-amount"></a>事前設定された量だけ位置を変更するには

1. 使用して、 [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)増分量を設定します。 既定ではこの値は 10 です。 この値は通常、コントロールの初期設定の 1 つとして設定します。 ステップ値を負にすることができます。

1. 使用して、 [StepIt](../mfc/reference/cprogressctrl-class.md#stepit)の位置をインクリメントするメンバー関数。 これにより、自動的に再描画するコントロール。

    > [!NOTE]
    >  `StepIt` ラップする位置になります。 たとえば、20、ステップと 90 の場合、位置 1 の-100 の範囲を指定`StepIt`位置を 10 に設定されます。

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>任意の大きさで位置を変更するには

1. 使用して、 [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos)メンバー関数は、位置を変更します。 `OffsetPos` 負の値を受け入れます。

    > [!NOTE]
    >  `OffsetPos`、とは異なり`StepIt`、位置は折り返されません。 新しい位置を調整して、範囲内に保持されます。

### <a name="to-change-the-position-to-a-specific-value"></a>特定の値に位置を変更するには

1. 使用して、 [SetPos](../mfc/reference/cprogressctrl-class.md#setpos)メンバー関数は、位置を特定の値に設定します。 必要に応じて、範囲内に新しい位置が調整されます。

通常、進行状況コントロールは、出力にのみ使用されます。 新しい値を指定せず、現在の位置を取得する[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)します。

## <a name="see-also"></a>関連項目

[CProgressCtrl の使い方](../mfc/using-cprogressctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
