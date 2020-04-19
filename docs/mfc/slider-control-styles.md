---
title: スライダー コントロールのスタイル
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: c6765445552826b71cca278c1fbbc66e500cb75a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307402"
---
# <a name="slider-control-styles"></a>スライダー コントロールのスタイル

スライダー コントロール ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 垂直または水平方向の向きを持つことができます。 いずれかの側では、目盛りが持てる側、またはどちらもします。 また、連続値の範囲を指定することも使用できます。 これらのプロパティは、スライダー コントロールを作成する場合を指定するスライダー コントロールのスタイルを使用して制御されます。

TBS_HORZ と TBS_VERT スタイルでは、スライダー コントロールの向きを決定します。 水平方向に印刷の向きを指定しない場合にスライダー コントロールの方向。

TBS_AUTOTICKS スタイルは、値の範囲内の各インクリメントに目盛りマークがあるスライダー コントロールを作成します。 呼び出すと、これらの目盛りが自動的に追加されます、 [SetRange](../mfc/reference/csliderctrl-class.md#setrange)メンバー関数。 TBS_AUTOTICKS を指定しない場合、メンバー関数をなど、使用できる[SetTic](../mfc/reference/csliderctrl-class.md#settic)と[SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)目盛りの位置を指定します。 目盛りは表示されませんが、スライダー コントロールを作成するには、TBS_NOTICKS スタイルを使用できます。

スライダー コントロールのいずれかまたは両方の側では、目盛りを表示できます。 水平方向のスライダー コントロール、TBS_BOTTOM または TBS_TOP スタイルを指定できます。 垂直方向のスライダー コントロール、TBS_RIGHT または TBS_LEFT スタイルを指定できます。 (TBS_BOTTOM と TBS_RIGHT は既定の設定) です。任意の方向のスライダー コントロールの両側に目盛り、TBS_BOTH スタイルを指定します。

スライダー コントロールは、作成するときに、TBS_ENABLESELRANGE スタイルを指定する場合にのみ、選択範囲を表示できます。 スライダー コントロールにこのスタイルが設定されているときは、(垂直方向の破線) ではなく三角形として選択範囲の開始と終了位置にある目盛りが表示され、選択範囲が強調表示されます。 たとえば、選択範囲が単純なスケジュール アプリケーションであります。 ユーザーは、スケジュールされた会議の時間を識別するために、1 日の時間に対応する目盛りの範囲を選択できます。

既定では、スライダー コントロールのスライダーの長さは、選択範囲が変更されるとは異なります。 スライダー コントロールが TBS_FIXEDLENGTH スタイル スライダーの長さは変わりません場合でも、選択範囲を変更します。 TBS_NOTHUMB スタイルがスライダー コントロールでは、スライダーは含まれません。

## <a name="see-also"></a>関連項目

[CSliderCtrl の使い方](../mfc/using-csliderctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
