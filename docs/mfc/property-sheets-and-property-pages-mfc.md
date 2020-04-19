---
title: プロパティ シートとプロパティ ページ (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685076"
---
# <a name="property-sheets-and-property-pages-mfc"></a>プロパティ シートとプロパティ ページ (MFC)

MFC[ダイアログボックス](../mfc/dialog-boxes.md)では、プロパティシートとプロパティページを組み込むことによって、"タブダイアログ" を表示できます。 MFC の "プロパティシート" と呼ばれるこの種のダイアログボックスは、Microsoft Word、Excel、および Visual C++の多くのダイアログボックスに似ていますが、前面から戻るファイルフォルダーのスタックや、カスケードウィンドウのグループのように、タブシートのスタックが含まれているように見えます。 前面のタブにあるコントロールが表示されます。背面のタブには、ラベル付きタブのみが表示されます。 プロパティシートは、複数のグループに細分化された多数のプロパティまたは設定を管理する場合に特に便利です。 通常、1つのプロパティシートを使用すると、複数の個別のダイアログボックスを置き換えることで、ユーザーインターフェイスを簡略化できます。

MFC バージョン4.0 では、プロパティシートとプロパティページは、Windows 95 および Windows NT バージョン3.51 以降に付属する共通コントロールを使用して実装されます。

プロパティシートは、 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)および[CPropertyPage](../mfc/reference/cpropertypage-class.md)クラスを使用して実装されます ( *MFC リファレンス*で説明されています)。 `CPropertySheet` は、`CPropertyPage` に基づく複数の "ページ" を含むことができるダイアログボックス全体を定義します。

プロパティシートの作成と操作の詳細については、「[プロパティシート](../mfc/property-sheets-mfc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC のプロパティ シートとプロパティ ページ](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[データの交換](../mfc/exchanging-data.md)<br/>
[モードレス プロパティ シートの作成](../mfc/creating-a-modeless-property-sheet.md)<br/>
[[適用] ボタンの処理](../mfc/handling-the-apply-button.md)
