---
title: ダイアログ ボックスの破棄
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685851"
---
# <a name="destroying-the-dialog-box"></a>ダイアログ ボックスの破棄

モーダルダイアログボックスは通常、スタックフレーム上に作成され、それを作成した関数が終了すると破棄されます。 ダイアログオブジェクトのデストラクターは、オブジェクトがスコープ外に出ると呼び出されます。

モードレスダイアログボックスは通常、親ビューまたはフレームウィンドウ (アプリケーションのメインフレームウィンドウまたはドキュメントフレームウィンドウ) によって作成および所有されます。 既定の[OnClose](../mfc/reference/cwnd-class.md#onclose)ハンドラーは[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)を呼び出します。これにより、ダイアログボックスウィンドウが破棄されます。 ダイアログボックスが単独で表示される場合、またはその他の特別な所有権のセマンティクスにポインターがないC++場合は、[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) をオーバーライドしてダイアログオブジェクトを破棄する必要があります。 また、 [OnCancel](../mfc/reference/cdialog-class.md#oncancel)をオーバーライドし、その中から `DestroyWindow` を呼び出す必要があります。 そうでない場合、ダイアログボックスの所有者は、 C++不要になったオブジェクトを破棄する必要があります。

## <a name="see-also"></a>関連項目

[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
