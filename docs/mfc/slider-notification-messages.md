---
title: スライダー コントロールの通知メッセージ
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
ms.openlocfilehash: bee2d602512ea1a6af39b0bb218ee7333b399c80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307329"
---
# <a name="slider-notification-messages"></a>スライダー コントロールの通知メッセージ

スライダー コントロールを親にスライダー コントロールの向きに応じて、兄弟または WM_VSCROLL メッセージを送信することによってユーザーの操作の親ウィンドウに通知します。 これらのメッセージを処理するには、親ウィンドウに兄弟および WM_VSCROLL メッセージのハンドラーを追加します。 [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll)と[OnVScroll](../mfc/reference/cwnd-class.md#onvscroll)メンバー関数は、スライダーとへのポインターの位置で、通知コードに渡される、 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)オブジェクト。 ポインターの型が注`CScrollBar *`を指す場合でも、`CSliderCtrl`オブジェクト。 スライダー コントロールを操作する必要がある場合は、このポインターをキャストする必要があります。

スクロール バーの通知コードを使用してではなくは、スライダー コントロールは、さまざまな通知コードを送信します。 スライダー コントロールは、ユーザーは、キーボードを使用して、スライダー コントロールと対話するときにのみ、TB_BOTTOM、TB_LINEDOWN、TB_LINEUP、および TB_TOP 通知コードを送信します。 ユーザーがマウスを使用する場合、TB_THUMBPOSITION と TB_THUMBTRACK 通知メッセージは送信のみされます。 TB_ENDTRACK、TB_PAGEDOWN、および TB_PAGEUP 通知コードは、どちらの場合も送信されます。

次の表には、スライダー コントロールの通知メッセージと通知を送信するイベント (仮想キー コードまたはマウス イベント) が一覧表示します。 (標準の仮想キー コードの一覧は、Winuser.h を参照してください)。

|通知メッセージ|イベント通知を送信できます。|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (ユーザーは、関連する仮想キー コードを送信するキーをリリース)|
|TB_LINEDOWN|VK_RIGHT または VK_DOWN|
|TB_LINEUP|VK_LEFT または VK_UP|
|TB_PAGEDOWN|VK_NEXT (ユーザーがクリックしたスライダーの右側または下のチャネル)|
|TB_PAGEUP|VK_PRIOR (ユーザーがクリックしたスライダーの左または上のチャネル)|
|TB_THUMBPOSITION|通知メッセージに TB_THUMBTRACK 続く WM_LBUTTONUP|
|TB_THUMBTRACK|スライダーの移動 (ユーザーは、スライダーをドラッグ)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>関連項目

[CSliderCtrl の使い方](../mfc/using-csliderctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
