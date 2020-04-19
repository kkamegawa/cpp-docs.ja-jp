---
title: グローバル ホット キー
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508562"
---
# <a name="global-hot-keys"></a>グローバル ホット キー

グローバルホットキーは、特定の子以外のウィンドウに関連付けられています。 これにより、ユーザーはシステムの任意の部分からウィンドウをアクティブ化できるようになります。 アプリケーションでは、 [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey)メッセージをそのウィンドウに送信することによって、特定のウィンドウのグローバルホットキーを設定します。 たとえば、が`m_HotKeyCtrl` [CHotKeyCtrl オブジェクト](../mfc/reference/chotkeyctrl-class.md)であり、ホットキーが押されたときにアクティブになるウィンドウへのポインターである場合、次のコードを使用して、コントロールで指定されたホットキーを、が指すウィンドウに関連付けることができます`pMainWnd``pMainWnd`。

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

ユーザーがグローバルホットキーを押すたびに、指定されたウィンドウは、コマンドの種類として**SC_HOTKEY**を指定する[WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand)メッセージを受け取ります。 このメッセージは、それを受信するウィンドウもアクティブにします。 このメッセージには、押されたキーに関する情報は含まれていないため、この方法を使用すると、同じウィンドウに接続されている可能性のある異なるホットキーを区別できません。 ホットキーは、 **WM_SETHOTKEY**を送信したアプリケーションが終了するまで有効なままです。

## <a name="see-also"></a>関連項目

[CHotKeyCtrl の使い方](../mfc/using-chotkeyctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
