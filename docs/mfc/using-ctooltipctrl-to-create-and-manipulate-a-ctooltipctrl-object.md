---
title: CToolTipCtrl を使用して CToolTipCtrl オブジェクトを作成および操作する方法
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: b0f008c70eeb43455408e5b0ad302df6b923608e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411644"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>CToolTipCtrl を使用して CToolTipCtrl オブジェクトを作成および操作する方法

次の例に示します[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)使用状況。

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>作成し、CToolTipCtrl を操作するには

1. 構築、`CToolTipCtrl`オブジェクト。

1. 呼び出す[作成](../mfc/reference/ctooltipctrl-class.md#create)Windows ツール ヒントの一般的なコントロールを作成してに接続する、`CToolTipCtrl`オブジェクト。

1. 呼び出す[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)ツールのカーソルがあるときにツール ヒントに格納されている情報が表示されるようにツール ヒント コントロールで、ツールを登録します。

1. 呼び出す[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)ツール ヒントが保持するツールの情報を設定します。

1. 呼び出す[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)ツールの新しい外接する四角形を設定します。

1. 呼び出す[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)場合と指定したツールの外接する四角形内にあるかどうかを判断する点をテストするには、ツールに関する情報を取得します。

1. 呼び出す[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount)ツール ヒント コントロールに登録されているツールの数を取得します。

## <a name="see-also"></a>関連項目

[CToolTipCtrl の使い方](../mfc/using-ctooltipctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
