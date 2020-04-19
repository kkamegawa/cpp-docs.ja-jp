---
title: 印刷
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: e0cd2d6d85cb9820b23495a003068994b13f9c85
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339578"
---
# <a name="printing"></a>印刷

Microsoft Windows では、デバイスに依存しない表示を実装します。 Mfc では、つまり、同じの描画呼び出しで、`OnDraw`ビュー クラスのメンバー関数は、ディスプレイおよびプリンターなどの他のデバイスでの描画を担当します。 印刷プレビューは、ターゲット デバイスは、表示するためのシミュレートされたプリンターの出力です。

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> フレームワークの役割と印刷でのロール

ビュー クラスには、次の責任があります。

- ページ数が、ドキュメントではフレームワークに通知します。

- 指定したページを印刷するメッセージが表示されたら、ドキュメントの部分を描画します。

- 割り当てし、任意のフォントまたは印刷に必要な他のグラフィックス デバイス インターフェイス (GDI) のリソースの割り当てを解除します。

- 必要に応じて、いずれかの送信など、特定のページを印刷する前に、プリンターのモードを変更する、ページ単位で印刷の向きを変更するために必要なコードをエスケープします。

フレームワークの役割は次のとおりです。

- 表示、**印刷** ダイアログ ボックス。

- 作成、 [CDC](../mfc/reference/cdc-class.md)プリンターのオブジェクト。

- 呼び出す、 [StartDoc](../mfc/reference/cdc-class.md#startdoc)と[EndDoc](../mfc/reference/cdc-class.md#enddoc)のメンバー関数は、`CDC`オブジェクト。

- 繰り返し呼び出し、 [StartPage](../mfc/reference/cdc-class.md#startpage)のメンバー関数、`CDC`オブジェクト、ページを印刷するか、および呼び出しビュー クラスの通知、 [EndPage](../mfc/reference/cdc-class.md#endpage)のメンバー関数、`CDC`オブジェクト。

- 適切なタイミングで、ビューでは、オーバーライド可能な関数を呼び出します。

次の記事では、フレームワークが印刷と印刷プレビューをサポートする方法について説明します。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [既定の印刷を行う方法](../mfc/how-default-printing-is-done.md)

- [マルチページ ドキュメント](../mfc/multipage-documents.md)

- [ヘッダーとフッター](../mfc/headers-and-footers.md)

- [印刷の GDI リソースの割り当てください。](../mfc/allocating-gdi-resources.md)

- [印刷プレビュー](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>関連項目

[[印刷と印刷プレビュー]](../mfc/printing-and-print-preview.md)
