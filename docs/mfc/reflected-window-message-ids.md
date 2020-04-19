---
title: 返送されたウィンドウ メッセージの ID
ms.date: 11/04/2016
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
ms.openlocfilehash: 6be7d29a4b43ac10980601708f5bcc666a48dd58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511387"
---
# <a name="reflected-window-message-ids"></a>返送されたウィンドウ メッセージの ID

ActiveX コントロールやその他の特殊なコントロールを簡単に作成する方法は、ウィンドウをサブクラス化することです。 詳細については[、「MFC ActiveX コントロール:Windows コントロール](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)のサブクラス化。

サブクラス化された Windows コントロールによって送信されたウィンドウメッセージをコントロールのコンテナーが受信しないようにするために、"リフレクター" ウィンドウを作成して、[特定のウィンドウ](../mfc/reference/colecontrol-class.md)メッセージをインターセプトし、コントロールに送り返します。 その後、ウィンドウプロシージャ内のコントロールは、ActiveX コントロールに適切なアクションを実行することで、これらのリフレクションメッセージを処理できます。

次の表は、インターセプトされるメッセージと、リフレクタウィンドウが送信する対応メッセージを示しています。

|コントロールによって送信されたメッセージ|コントロールに反映されたメッセージ|
|---------------------------------|--------------------------------------|
|[WM_COMMAND](/windows/win32/menurc/wm-command)|OCM_COMMAND|
|[WM_CTLCOLORBTN](/windows/win32/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|
|[WM_CTLCOLOREDIT](/windows/win32/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|
|[WM_CTLCOLORDLG](/windows/win32/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|
|[WM_CTLCOLORLISTBOX](/windows/win32/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|
|[WM_CTLCOLORSCROLLBAR](/windows/win32/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|
|[WM_CTLCOLORSTATIC](/windows/win32/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|
|[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)|OCM_DRAWITEM|
|[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)|OCM_MEASUREITEM|
|[WM_DELETEITEM](/windows/win32/Controls/wm-deleteitem)|OCM_DELETEITEM|
|[WM_VKEYTOITEM](/windows/win32/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|
|[WM_CHARTOITEM](/windows/win32/Controls/wm-chartoitem)|OCM_CHARTOITEM|
|[WM_COMPAREITEM](/windows/win32/Controls/wm-compareitem)|OCM_COMPAREITEM|
|[WM_HSCROLL](/windows/win32/Controls/wm-hscroll)|OCM_HSCROLL|
|[WM_VSCROLL](/windows/win32/Controls/wm-vscroll)|OCM_VSCROLL|
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|
|[WM_NOTIFY](/windows/win32/controls/wm-notify)|OCM_NOTIFY|

> [!NOTE]
>  コントロールが Win32 システム上で実行されている場合は、いくつ\*かの種類の WM_CTLCOLOR メッセージを受け取ることができます。 詳細については、「WM_CTLCOLORBTN、WM_CTLCOLORDLG、WM_CTLCOLOREDIT、WM_CTLCOLORLISTBOX、WM_CTLCOLORMSGBOX、WM_CTLCOLORSCROLLBAR、WM_CTLCOLORSTATIC」を参照してください。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: Windows コントロールのサブクラス化](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[テクニカル ノート 62: Windows コントロールへのメッセージ リフレクション](../mfc/tn062-message-reflection-for-windows-controls.md)
