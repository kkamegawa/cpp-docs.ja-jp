---
title: ToolBar コントロールの操作
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 60cc527493e2a68751c201b998ab171c564d6c1f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510581"
---
# <a name="working-with-the-toolbar-control"></a>ToolBar コントロールの操作

この記事では、 [CToolBar](../mfc/reference/ctoolbar-class.md)の基になっている[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクトにアクセスして、ツールバーをより細かく制御する方法について説明します。 これは高度なトピックです。

## <a name="procedures"></a>手順

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>CToolBar オブジェクトの基になるツールバーコモンコントロールにアクセスするには

1. [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)を呼び出します。

`GetToolBarCtrl`[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクトへの参照を返します。 この参照を使用して、toolbar コントロールクラスのメンバー関数を呼び出すことができます。

> [!CAUTION]
>  **Get**関数`CToolBarCtrl`の呼び出しは安全ですが、 **Set**関数を呼び出す場合は注意が必要です。 これは高度なトピックです。 通常、基になるツールバーコントロールにアクセスする必要はありません。

### <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [コントロール (Windows コモンコントロール)](../mfc/controls-mfc.md)

- [ツールバーの基礎](../mfc/toolbar-fundamentals.md)

- [ドッキングツールバーとフローティングツールバー](../mfc/docking-and-floating-toolbars.md)

- [ツールバーのサイズを動的に変更する](../mfc/docking-and-floating-toolbars.md)

- [ツールバーのツールヒント](../mfc/toolbar-tool-tips.md)

- [Flyby ステータスバーの更新](../mfc/toolbar-tool-tips.md)

- [ツールヒントの通知の処理](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)クラスと[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)クラス

- [カスタマイズ通知の処理](../mfc/handling-customization-notifications.md)

- [複数のツールバー](../mfc/toolbar-fundamentals.md)

- [以前のツールバーの使用](../mfc/using-your-old-toolbars.md)

- [コントロールバー](../mfc/control-bars.md)

Windows コモンコントロールの使用に関する一般的な情報については、「[コモンコントロール](/windows/win32/Controls/common-controls-intro)」を参照してください。

## <a name="see-also"></a>関連項目

[MFC ツール バーの実装](../mfc/mfc-toolbar-implementation.md)
