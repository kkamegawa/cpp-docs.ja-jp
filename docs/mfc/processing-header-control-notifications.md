---
title: ヘッダー コントロール通知の処理
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: bc811763fe3f4717b8baaeb4a23df1ae59bb1979
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908135"
---
# <a name="processing-header-control-notifications"></a>ヘッダー コントロール通知の処理

ビューまたはダイアログクラスで、[クラスウィザード](reference/mfc-class-wizard.md)を使用して、処理するすべてのヘッダーコントロール ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 通知メッセージの Switch ステートメントを含む[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) handler 関数を作成します (「メッセージのマッピング」を参照)。 [関数](../mfc/reference/mapping-messages-to-functions.md))。 ユーザーがヘッダー項目をクリックまたはダブルクリックしたり、項目の間に区分線をドラッグしたりすると、通知が親ウィンドウに送信されます。

ヘッダーコントロールに関連付けられている通知メッセージは、Windows SDK の[ヘッダーコントロールリファレンス](/windows/win32/controls/header-control-reference)に一覧表示されます。

## <a name="see-also"></a>関連項目

[CHeaderCtrl の使い方](../mfc/using-cheaderctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
