---
title: リッチ エディット コントロールでの印刷
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 671aec27584af975ce1635793ae80879e7208d4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508012"
---
# <a name="printing-in-rich-edit-controls"></a>リッチ エディット コントロールでの印刷

リッチエディットコントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) に対して、プリンターなど、指定されたデバイスの出力を表示するように指示できます。 リッチエディットコントロールがテキストを書式設定する出力デバイスを指定することもできます。

特定のデバイスのリッチエディットコントロールの内容の一部を書式設定するには、 [Formatrange](../mfc/reference/cricheditctrl-class.md#formatrange)メンバー関数を使用します。 この関数で使用される[formatrange](/windows/win32/api/richedit/ns-richedit-formatrange)構造体は、フォーマットするテキストの範囲と、ターゲットデバイスのデバイスコンテキスト (DC) を指定します。

出力デバイスのテキストの書式を設定した後、 [Displayband](../mfc/reference/cricheditctrl-class.md#displayband)メンバー関数を使用して、出力をデバイスに送信できます。 とを繰り返し`FormatRange`使用`DisplayBand`すると、リッチエディットコントロールの内容を出力するアプリケーションでは、縞模様を実装できます。 (縞模様は出力を小さな部分に分割して印刷するために使用します)。

[Settargetdevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)メンバー関数を使用すると、リッチエディットコントロールがテキストを書式設定する対象デバイスを指定できます。 この関数は、WYSIWYG (表示される内容) の書式設定に役立ちます。これは、アプリケーションが画面のではなく、既定のプリンターのフォントメトリックを使用してテキストを配置します。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
