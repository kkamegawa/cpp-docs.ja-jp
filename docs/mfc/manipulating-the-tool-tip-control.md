---
title: ツール ヒント コントロールの操作
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: d8c994748239871f17b878dd8ea7505a2a8a0b65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226158"
---
# <a name="manipulating-the-tool-tip-control"></a>ツール ヒント コントロールの操作

クラス`CToolTipCtrl`メンバーのグループのさまざまな属性を制御する機能を提供、`CToolTipCtrl`オブジェクトとツール ヒントのウィンドウ。

初期、ポップアップで、windows のツール ヒントを設定してへの呼び出しで取得できるは、期間を表示[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)と[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)します。

次の関数で、ツール ヒント ウィンドウの外観を変更します。

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)と[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)ヒントのテキストをツール ヒントの境界線と、ツールの幅を取得および設定します。

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)と[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)ツールの最大の幅のヒント ウィンドウを取得および設定します。

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)と[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)ツールの背景色のヒント ウィンドウを取得および設定します。

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)と[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)ツールのテキストの色のヒント ウィンドウを取得および設定します。

ツール ヒント コントロール WM_LBUTTONXXX メッセージなどの重要なメッセージの通知を受け取るために、ツール ヒント コントロールにメッセージを中継する必要があります。 この中継の最適な方法は、呼び出しを行うには[CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent)の`PreTranslateMessage`オーナー ウィンドウの関数。 次の例では、1 つの可能なメソッドを示しています (ツール ヒント コントロールと仮定した場合と呼ばれる`m_ToolTip`)。

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

ツール ヒントのウィンドウをすぐに削除するを呼び出して、[ポップ](../mfc/reference/ctooltipctrl-class.md#pop)メンバー関数。

## <a name="see-also"></a>関連項目

[CToolTipCtrl の使い方](../mfc/using-ctooltipctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
