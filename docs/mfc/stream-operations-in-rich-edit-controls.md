---
title: リッチ エディット コントロールでのストリーム操作
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 73277f59dc0ad4dfe21d481d0b893903ed407ea9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512943"
---
# <a name="stream-operations-in-rich-edit-controls"></a>リッチ エディット コントロールでのストリーム操作

ストリームを使用して、リッチエディットコントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) との間でデータを転送できます。 ストリームは、バッファーとアプリケーション定義のコールバック関数を指定する[editstream](/windows/win32/api/richedit/ns-richedit-editstream)構造体によって定義されます。

リッチエディットコントロールにデータを読み込む (つまり、でデータをストリームする) には、 [Streamin](../mfc/reference/cricheditctrl-class.md#streamin)メンバー関数を使用します。 コントロールは、アプリケーション定義のコールバック関数を繰り返し呼び出します。このコールバック関数は、データの一部を毎回バッファーに転送します。

リッチエディットコントロールの内容 (つまり、データをストリーム出力する) を保存するには、 [Streamout](../mfc/reference/cricheditctrl-class.md#streamout)メンバー関数を使用します。 コントロールは、バッファーへの書き込みを繰り返し、アプリケーション定義のコールバック関数を呼び出します。 コールバック関数は、呼び出しごとに、バッファーの内容を保存します。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
