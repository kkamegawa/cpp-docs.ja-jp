---
title: スレッド固有のホット キー
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 68c50ec5f29dab271f9af9abc50eb72ec15157e7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893328"
---
# <a name="thread-specific-hot-keys"></a>スレッド固有のホット キー

アプリケーション スレッドに固有のホット キーの設定 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md))、Windows を使用して`RegisterHotKey`関数。 ユーザーは、スレッド固有のホット キーを押すと、Windows の投稿、 [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey)メッセージを特定のスレッドのメッセージ キューの先頭にします。 WM_HOTKEY メッセージには、仮想キー コード、シフト状態および押されたホット キーの特定のユーザー定義の ID が含まれています。 標準の仮想キー コードの一覧は、Winuser.h を参照してください。 このメソッドの詳細については、次を参照してください。 [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)します。

フラグのシフト状態への呼び出しで使用される注`RegisterHotKey`がによって返されるものと同じでない、 [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)メンバー関数の呼び出しの前にこれらのフラグを変換する必要があります`RegisterHotKey`します。

## <a name="see-also"></a>関連項目

[CHotKeyCtrl の使い方](../mfc/using-chotkeyctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)

