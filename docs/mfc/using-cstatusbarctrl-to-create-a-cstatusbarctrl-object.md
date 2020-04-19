---
title: CStatusBarCtrl を使用して CStatusBarCtrl オブジェクトを作成する方法
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 3242986d66de7d423b8ab744a691ca1904328de8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411709"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>CStatusBarCtrl を使用して CStatusBarCtrl オブジェクトを作成する方法

一般的な用途の例を次に示します[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>パーツでステータス バー コントロールを使用するには

1. 構築、`CStatusBarCtrl`オブジェクト。

1. 呼び出す[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)ステータス バー コントロールの高さの最小値を設定する場合の領域を描画します。

1. 呼び出す[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)ステータス バー コントロールの背景色を設定します。

1. 呼び出す[呼び出した](../mfc/reference/cstatusbarctrl-class.md#setparts)ステータス バーのコントロールと各部分の右端の座標で部分の数を設定します。

1. 呼び出す[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)ステータス バー コントロールの特定の部分でテキストを設定します。 メッセージは、原因で、コントロールが次に WM_PAINT メッセージを受信すると、新しいテキストを表示するように、変更されたコントロールの部分を無効にします。

場合によっては、ステータス バーは、行のテキストを表示するだけ済みます。 この場合、呼び出しを行う[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)します。 これにより、ステータス バー コントロールが 1 行のテキストが表示されます「簡単」モードには。

## <a name="see-also"></a>関連項目

[CStatusBarCtrl の使い方](../mfc/using-cstatusbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
