---
title: ホット キーの設定
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: 7b49f24039b130f74693e7567f5287476126f225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511208"
---
# <a name="setting-a-hot-key"></a>ホット キーの設定

アプリケーションでは、次の2つの方法のいずれかでホットキー ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) コントロールによって提供される情報を使用できます。

- アクティブ化するウィンドウに[WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey)メッセージを送信して、非子ウィンドウをアクティブにするためのグローバルホットキーを設定します。

- Windows の関数[registerhotkey](/windows/win32/api/winuser/nf-winuser-registerhotkey)キーを呼び出して、スレッド固有のホットキーを設定します。

## <a name="see-also"></a>関連項目

[CHotKeyCtrl の使い方](../mfc/using-chotkeyctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
