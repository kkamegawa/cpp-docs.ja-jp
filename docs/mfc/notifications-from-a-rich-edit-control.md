---
title: リッチ エディット コントロールからの通知メッセージ
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: d097996e61a3d461dacd3d30e13b9262c7d32434
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508052"
---
# <a name="notifications-from-a-rich-edit-control"></a>リッチ エディット コントロールからの通知メッセージ

通知メッセージは、リッチエディットコントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) に影響を与えるイベントを報告します。 これらは、親ウィンドウ、またはリッチエディットコントロール自体によってメッセージリフレクションを使用して処理できます。 リッチエディットコントロールでは、エディットコントロールで使用されるすべての通知メッセージに加えて、いくつかの追加の通知メッセージがサポートされます。 リッチエディットコントロールが親ウィンドウを送信する通知メッセージを特定するには、"イベントマスク" を設定します。

リッチエディットコントロールのイベントマスクを設定するには、 [Seteventmask](../mfc/reference/cricheditctrl-class.md#seteventmask)メンバー関数を使用します。 リッチエディットコントロールの現在のイベントマスクを取得するには、 [Geteventmask](../mfc/reference/cricheditctrl-class.md#geteventmask)メンバー関数を使用します。

次の段落では、いくつかの特定の通知とその使用方法を示しています。

- EN_MSGFILTER EN_MSGFILTER notification を処理することで、クラスは、リッチエディットコントロールまたはその親ウィンドウのいずれかを使用して、コントロールに対するすべてのキーボードとマウス入力をフィルター処理できます。 ハンドラーでは、キーボードまたはマウスメッセージが処理されないようにすることも、指定した[Msgfilter](/windows/win32/api/richedit/ns-richedit-msgfilter)構造体を変更することによってメッセージを変更することもできます。

- EN_PROTECTED は、ユーザーが保護されたテキストを変更しようとしたときを検出するために、EN_PROTECTED 通知メッセージを処理します。 テキストの範囲を保護済みとしてマークするには、保護された文字効果を設定します。 詳細については、「[リッチエディットコントロールでの文字の書式設定](../mfc/character-formatting-in-rich-edit-controls.md)」を参照してください。

- EN_DROPFILES ユーザーは、EN_DROPFILES 通知メッセージを処理することによって、リッチエディットコントロールにファイルをドロップできます。 指定された[ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles)構造体には、削除されるファイルに関する情報が含まれています。

- EN_SELCHANGE アプリケーションは、EN_SELCHANGE 通知メッセージを処理することにより、現在の選択範囲が変更されたことを検出できます。 通知メッセージには、新しい選択に関する情報を含む[Selchange](/windows/win32/api/richedit/ns-richedit-selchange)構造が指定されています。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
