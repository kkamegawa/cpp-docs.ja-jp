---
title: CStatusBarCtrl オブジェクトでのツール ヒントの使い方
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411436"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>CStatusBarCtrl オブジェクトでのツール ヒントの使い方

ステータス バー コントロールのツールヒントを有効にするのには、作成、`CStatusBarCtrl`オブジェクトにはスタイルを使用します。

> [!NOTE]
>  使用する場合、 `CStatusBar` 、ステータス バーの実装を使用するオブジェクト、`CStatusBar::CreateEx`関数。 埋め込みの追加のスタイルを指定できます`CStatusBarCtrl`オブジェクト。

1 回、`CStatusBarCtrl`オブジェクトが正常に作成されたを使用して、 [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext)と[CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext)を設定し、特定のウィンドウに関するツールヒントのテキストを取得します。

ツール ヒントを設定すると、パーツ内のすべてのテキストを表示できない場合や、一部がある、アイコンとテキストがない場合にのみ表示されます。 ツール ヒントは簡易モードではサポートされていません。

## <a name="see-also"></a>関連項目

[CStatusBarCtrl の使い方](../mfc/using-cstatusbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
