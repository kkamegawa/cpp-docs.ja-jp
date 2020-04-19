---
title: リッチ エディット コントロールでのクリップボード操作
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508962"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>リッチ エディット コントロールでのクリップボード操作

アプリケーションでは、クリップボードの内容をリッチエディットコントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) に貼り付けることができます。これは、最適なクリップボード形式または特定のクリップボード形式を使用します。 また、リッチエディットコントロールがクリップボード形式を貼り付けることができるかどうかを判断することもできます。

[Copy](../mfc/reference/cricheditctrl-class.md#copy)または[cut](../mfc/reference/cricheditctrl-class.md#cut)メンバー関数を使用して、現在の選択内容をコピーまたは切り取りできます。 同様に、 [paste](../mfc/reference/cricheditctrl-class.md#paste)メンバー関数を使用すると、クリップボードの内容をリッチエディットコントロールに貼り付けることができます。 コントロールは、認識されている最初の使用可能な形式を貼り付けます。これは、おそらく最もわかりやすい形式です。

特定のクリップボード形式を貼り付けるには、 [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial)メンバー関数を使用します。 この関数は、ユーザーがクリップボード形式を選択できるようにするための、貼り付けの特別なコマンドを使用するアプリケーションに便利です。 [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste)メンバー関数を使用すると、指定した書式がコントロールによって認識されているかどうかを判断できます。

また、を使用`CanPaste`して、リッチエディットコントロールによって使用可能なクリップボード形式が認識されるかどうかを判断することもできます。 この関数は、 `OnInitMenuPopup`ハンドラーで役に立ちます。 アプリケーションでは、使用可能な任意の形式をコントロールが貼り付けることができるかどうかに応じて、貼り付けコマンドを有効または灰色にすることができます。

リッチエディットコントロールは、リッチテキスト形式と、RichEdit テキストおよびオブジェクトという形式の2つのクリップボード形式を登録します。 アプリケーションでは、 **CF_RTF**と**CF_RETEXTOBJ**の値を指定して、 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数を使用してこれらの形式を登録できます。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
