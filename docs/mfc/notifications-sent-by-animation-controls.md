---
title: アニメーション コントロールによる通知の送信
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508025"
---
# <a name="notifications-sent-by-animation-controls"></a>アニメーション コントロールによる通知の送信

アニメーションコントロール ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) は、2つの異なる種類の通知メッセージを送信します。 通知は、 [WM_COMMAND](/windows/win32/menurc/wm-command)メッセージの形式で送信されます。

[ACN_START](/windows/win32/Controls/acn-start)メッセージは、アニメーションコントロールがクリップの再生を開始したときに送信されます。 [ACN_STOP](/windows/win32/Controls/acn-stop)メッセージは、アニメーションコントロールがクリップの再生を完了または停止したときに送信されます。

## <a name="see-also"></a>関連項目

[CAnimateCtrl の使い方](../mfc/using-canimatectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
