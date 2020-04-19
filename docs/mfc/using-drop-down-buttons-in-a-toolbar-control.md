---
title: ツール バー コントロールでのドロップダウン ボタンの使い方
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 8d1a13b1921f111d97bb515e7932a0116277f9ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411605"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>ツール バー コントロールでのドロップダウン ボタンの使い方

標準のプッシュ ボタンに加えて、ツールバーはドロップダウン ボタンをこともできます。 ドロップダウン ボタンは通常の下向きの矢印によって示されます。

> [!NOTE]
>  下向きの矢印は、拡張スタイル TBSTYLE_EX_DRAWDDARROWS が設定されている場合にのみ表示されます。

ユーザーは、この矢印 (または、ボタン自体、矢印が存在しない場合) をクリックすると、ツール バー コントロールの親に TBN_DROPDOWN 通知メッセージが送信されます。 この通知を処理し、ポップアップ メニューを表示Internet Explorer の動作に似ています。

次の手順では、ポップアップ メニューのドロップダウン ツール バー ボタンを実装する方法を示します。

### <a name="to-implement-a-drop-down-button"></a>ドロップダウン ボタンを実装するには

1. 1 回、`CToolBarCtrl`オブジェクトが作成されたら、次のコードを使用して、TBSTYLE_EX_DRAWDDARROWS スタイルを設定します。

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. いずれかの新しい TBSTYLE_DROPDOWN スタイルを設定 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton)または[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) または既存の ([です](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) が表示されるドロップダウン ボタンのボタン。 次の例で既存のボタンの変更、`CToolBarCtrl`オブジェクト。

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. ツールバーのオブジェクトの親クラスに TBN_DROPDOWN ハンドラーを追加します。

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. 新しいハンドラーでは、適切なポップアップ メニューを表示します。 次のコードでは、1 つの方法を示します。

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>関連項目

[CToolBarCtrl の使い方](../mfc/using-ctoolbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
