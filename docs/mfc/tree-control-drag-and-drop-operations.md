---
title: ツリー コントロールのドラッグ アンド ドロップ操作
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510910"
---
# <a name="tree-control-drag-and-drop-operations"></a>ツリー コントロールのドラッグ アンド ドロップ操作

ツリーコントロール ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) は、ユーザーが項目のドラッグを開始したときに通知を送信します。 ユーザーがマウスの左ボタンを使用して項目のドラッグを開始すると、コントロールは[TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag)通知メッセージを送信します。ユーザーが右ボタンでドラッグを開始すると、 [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag)通知メッセージが送信されます。 ツリーコントロールに TVS_DISABLEDRAGDROP スタイルを提供することで、ツリーコントロールがこれらの通知を送信しないようにすることができます。

[Createdragimage](../mfc/reference/ctreectrl-class.md#createdragimage)メンバー関数を呼び出すと、ドラッグ操作中に表示するイメージを取得できます。 ツリーコントロールは、ドラッグされている項目のラベルに基づいて、ドラッグするビットマップを作成します。 次に、ツリーコントロールがイメージリストを作成し、ビットマップを追加して、 [CImageList](../mfc/reference/cimagelist-class.md)オブジェクトへのポインターを返します。

項目を実際にドラッグするコードを指定する必要があります。 これには通常、イメージリスト関数のドラッグ機能を使用し、ドラッグ操作の開始後に送信された[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)および[WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (または[WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) メッセージを処理する必要があります。 イメージリスト関数の詳細については、「Windows SDK」の「 [CImageList](../mfc/reference/cimagelist-class.md) In The *MFC Reference* and [image](/windows/win32/controls/image-lists) list」を参照してください。 ツリーコントロール項目のドラッグの詳細については、「Windows SDK での[ツリービュー項目のドラッグ](/windows/win32/Controls/tree-view-controls)」も参照してください。

ツリーコントロール内の項目をドラッグアンドドロップ操作の対象にする場合は、マウスカーソルがターゲット項目上にあることを把握しておく必要があります。 [System.windows.media.visualtreehelper.hittest](../mfc/reference/ctreectrl-class.md#hittest)メンバー関数を呼び出すことによって確認できます。 ポイントと整数を指定するか、マウスカーソルの現在の座標を含む[TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo)構造体のアドレスを指定します。 関数から制御が戻ると、整数または構造体に、ツリーコントロールを基準とするマウスカーソルの位置を示すフラグが含まれます。 カーソルがツリーコントロールの項目の上にある場合は、その項目のハンドルも構造体に格納されます。

項目がドラッグアンドドロップ操作の対象であることを示すには、 [SetItem](../mfc/reference/ctreectrl-class.md#setitem)メンバー関数を呼び出して状態を`TVIS_DROPHILITED`値に設定します。 この状態の項目は、ドラッグアンドドロップのターゲットを示すために使用されるスタイルで描画されます。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
