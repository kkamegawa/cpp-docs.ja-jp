---
title: スレッド固有のホット キー
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511142"
---
# <a name="thread-specific-hot-keys"></a>スレッド固有のホット キー

アプリケーションは、Windows `RegisterHotKey`の関数を使用して、スレッド固有のホットキー ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) を設定します。 ユーザーがスレッド固有のホットキーを押すと、 [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey)メッセージが特定のスレッドのメッセージキューの先頭にポストされます。 WM_HOTKEY メッセージには、押された特定のホットキーの仮想キーコード、シフト状態、およびユーザー定義の ID が含まれています。 標準の仮想キーコードの一覧については、「Winuser. h」を参照してください。 この方法の詳細については、「 [Registerhotkey キー](/windows/win32/api/winuser/nf-winuser-registerhotkey)」を参照してください。

の呼び出し`RegisterHotKey`で使用されている shift 状態フラグは、 [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)メンバー関数によって返されるフラグとは異なります。を呼び出す`RegisterHotKey`前に、これらのフラグを変換する必要があります。

## <a name="see-also"></a>関連項目

[CHotKeyCtrl の使い方](../mfc/using-chotkeyctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
