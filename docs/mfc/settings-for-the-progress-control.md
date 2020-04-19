---
title: プログレス コントロールの設定
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 1960b15c2f76d7cbfc9f249a77481b795e6a27ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307680"
---
# <a name="settings-for-the-progress-control"></a>プログレス コントロールの設定

プログレス コントロールの基本設定 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) は、範囲と現在の位置。 範囲は、操作の全体の期間を表します。 現在の位置は、アプリケーションによって、操作の完了に向けた準備された進行状況を表します。 範囲や位置を変更するには、進行状況コントロール自体を再描画するが発生します。

既定で範囲を設定する 0 - 100、および初期位置が 0 に設定されます。 プログレス コントロールの現在の範囲の設定を取得するには、使用、 [GetRange](../mfc/reference/cprogressctrl-class.md#getrange)メンバー関数。 範囲を変更するには、使用、 [SetRange](../mfc/reference/cprogressctrl-class.md#setrange)メンバー関数。

位置を設定する[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)します。 新しい値を指定せず、現在の位置を取得する[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)します。 たとえば、単純に現在の操作の状態に対してクエリを実行します。

プログレス コントロールの現在の位置を手順を使用して[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)します。 ステップごとの量を設定する[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>関連項目

[CProgressCtrl の使い方](../mfc/using-cprogressctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
