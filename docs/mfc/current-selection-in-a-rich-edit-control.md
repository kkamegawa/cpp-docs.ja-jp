---
title: リッチ エディット コントロールでの現在の選択項目
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 43a68d63f7888d762eee031196453eb156ecf105
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508769"
---
# <a name="current-selection-in-a-rich-edit-control"></a>リッチ エディット コントロールでの現在の選択項目

ユーザーは、マウスまたはキーボードを使用して、リッチエディットコントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 内のテキストを選択できます。 現在の選択範囲は、選択した文字の範囲、または文字が選択されていない場合は挿入ポイントの位置を示します。 アプリケーションでは、現在の選択項目に関する情報を取得し、現在の選択範囲を設定し、現在の選択範囲を変更するタイミングを決定し、選択範囲の強調表示を表示または非表示にすることができます。

リッチエディットコントロールで現在選択されている項目を確認するには、 [Getsel](../mfc/reference/cricheditctrl-class.md#getsel)メンバー関数を使用します。 現在の選択項目を設定するには、 [SetSel](../mfc/reference/cricheditctrl-class.md#setsel)メンバー関数を使用します。 [Charrange](/windows/win32/api/richedit/ns-richedit-charrange)構造体は、文字の範囲を指定するためにこれらの関数と共に使用されます。 現在の選択範囲の内容に関する情報を取得するには、 [Getselectiontype](../mfc/reference/cricheditctrl-class.md#getselectiontype)メンバー関数を使用します。

既定では、リッチエディットコントロールは、フォーカスを取得したり失ったりしたときに選択範囲の強調表示を表示したり、非表示にしたりします。 [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)メンバー関数を使用すると、いつでも選択範囲を強調表示または非表示にすることができます。 たとえば、アプリケーションでは、リッチエディットコントロールのテキストを検索するための検索ダイアログボックスが提供される場合があります。 アプリケーションでは、ダイアログボックスを閉じずに一致するテキストを選択する場合が`HideSelection`あります。この場合は、を使用して選択内容を強調表示する必要があります。

リッチエディットコントロールで選択したテキストを取得するには、 [Getseltext](../mfc/reference/cricheditctrl-class.md#getseltext)メンバー関数を使用します。 テキストは、指定された文字配列にコピーされます。 配列が、選択したテキストと終端の null 文字を保持するのに十分な大きさであることを確認する必要があります。

[FindText](../mfc/reference/cricheditctrl-class.md#findtext)メンバー関数を使用して、リッチエディットコントロールで文字列を検索することができます。この関数で使用される[findtextex](/windows/win32/api/richedit/ns-richedit-findtextexw)構造体では、検索するテキスト範囲と検索する文字列を指定します。 検索で大文字と小文字を区別するかどうかなどのオプションを指定することもできます。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
