---
title: ツール ヒントの作成方法
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 2ba935f52f24f62dded3b89df1563454cf7e0335
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383912"
---
# <a name="methods-of-creating-tool-tips"></a>ツール ヒントの作成方法

MFC には、3 つのクラスを作成および管理ツール ヒント コントロールが用意されています。[CWnd](../mfc/reference/cwnd-class.md)、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)、 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)と[CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)します。 これらのクラスで、ツール ヒントのメンバー関数は、Windows のコモン コントロール API をラップします。 クラス`CToolBarCtrl`とクラス`CToolTipCtrl`クラスから派生されて`CWnd`します。

`CWnd` 次の 4 つのメンバー関数を作成および管理ツール ヒントを提供します。[EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)、 [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips)、 [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage)、および[OnToolHitTest](../mfc/reference/cwnd-class.md#ontoolhittest)します。 ツール ヒントの実装方法の詳細についてはこれらの個々 のメンバー関数を参照してください。

使用してツールバーを作成する場合`CToolBarCtrl`、次のメンバー関数を使用して直接、ツールバーのツール ヒントを実装することができます。[GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips)と[SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips)します。 これらの個々 のメンバー関数を参照してくださいと[ツール ヒントの通知の処理](../mfc/handling-tool-tip-notifications.md)ツール ヒントの実装方法の詳細についてはします。

`CToolTipCtrl`クラスには、Windows の一般的なツール ヒント コントロールの機能が用意されています。 1 つのツール ヒント コントロールは、1 つ以上のツールの情報を提供できます。 ツールは、子ウィンドウやコントロール、ウィンドウのクライアント領域内でアプリケーションで定義された四角形領域など、いずれかのウィンドウです。 [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)クラスから派生`CToolTipCtrl`visual スタイルの追加と機能を提供します。

## <a name="see-also"></a>関連項目

[CToolTipCtrl の使い方](../mfc/using-ctooltipctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
