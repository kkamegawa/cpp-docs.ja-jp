---
title: スライダー コントロールのメンバー関数
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: a88dd1a49eb928261393a4473ee7eb53628c607a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307432"
---
# <a name="slider-control-member-functions"></a>スライダー コントロールのメンバー関数

アプリケーションがスライダー コントロールに関する情報を取得するコントロールのメンバー関数には、スライダーの呼び出すことができます ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) とその特性を変更します。

(つまり、ユーザーが選択した値) のスライダーの位置を取得するには、使用、 [GetPos](../mfc/reference/csliderctrl-class.md#getpos)メンバー関数。 スライダーの位置を設定するには、使用、 [SetPos](../mfc/reference/csliderctrl-class.md#setpos)メンバー関数。 使用することができます、いつでも、`VerifyPos`メンバー関数は、スライダーが最小と最大値の間にあるかどうかを確認します。

スライダー コントロールの範囲は、スライダー コントロールを表すことのできる連続した値のセットです。 ほとんどのアプリケーションを使用して、 [SetRange](../mfc/reference/csliderctrl-class.md#setrange)メンバー関数が最初に作成されるときに、スライダー コントロールの範囲を設定します。 スライダー コントロールを使用して作成した後、アプリケーションは、範囲を alter 動的にことができます、 [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax)と[SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin)メンバー関数。 通常動的に変更する範囲を許可するアプリケーションは、ユーザーがスライダー コントロールの操作を完了すると、最終的な範囲の設定を取得します。 これらの設定を取得する、 [GetRange](../mfc/reference/csliderctrl-class.md#getrange)、 [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)、および[GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin)メンバー関数。

アプリケーションでは、スライダー コントロールの目盛りは、自動的に表示させる TBS_AUTOTICKS スタイルを使用できます。 アプリケーションは、位置またはティックの頻度を制御する必要があります、ただし、多数のメンバー関数が使用できます。

目盛りの位置を設定するアプリケーションを使用できる、 [SetTic](../mfc/reference/csliderctrl-class.md#settic)メンバー関数。 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)メンバー関数により、アプリケーションが目盛りをスライダー コントロールの範囲内で一定の間隔で表示される設定にします。 たとえば、アプリケーションでは、1 ~ 100 の範囲の 10 個の目盛りを表示するのにこのメンバー関数を使用できます。

目盛りに対応する範囲内のインデックスを取得する、 [GetTic](../mfc/reference/csliderctrl-class.md#gettic)メンバー関数。 [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray)メンバー関数は、これらのインデックスの配列を取得します。 クライアント座標で、目盛りの位置を取得するには、使用、 [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos)メンバー関数。 目盛りの数を取得して、アプリケーション、 [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics)メンバー関数。

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics)メンバー関数は、すべてのスライダー コントロールの目盛りを削除します。

スライダー コントロールの行サイズは、アプリケーションは TB_LINEDOWN または TB_LINEUP 通知メッセージを受信すると、スライダーが移動距離を決定します。 同様に、ページ サイズは、TB_PAGEDOWN と TB_PAGEUP 通知メッセージに応答を決定します。 アプリケーションの取得し、を使用して行およびページ サイズの値を設定することができます、 [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize)、 [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize)、 [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)、および[SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize)メンバー関数。

アプリケーションは、スライダー コントロールの寸法を取得するのにメンバー関数を使用することができます。 [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect)メンバー関数は、スライダーの外接する四角形を取得します。 [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect)メンバー関数は、スライダー コントロールのチャネルの外接する四角形を取得します。 (チャネルは、領域、スライダーの移動と範囲を選択すると、強調表示が含まれています。)

スライダー コントロールに TBS_ENABLESELRANGE スタイルがある場合は、ユーザーはそこから連続する値の範囲を選択できます。 多数のメンバー関数は、動的に調整する選択範囲を許可します。 [SetSelection](../mfc/reference/csliderctrl-class.md#setselection)メンバー関数は、開始位置と終了位置の選択範囲を設定します。 ユーザーは、選択範囲の設定が完了したら、アプリケーションを使用して設定を取得できます、 [GetSelection](../mfc/reference/csliderctrl-class.md#getselection)メンバー関数。 ユーザーの選択をクリアするには、使用、 [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel)メンバー関数。

## <a name="see-also"></a>関連項目

[CSliderCtrl の使い方](../mfc/using-csliderctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
