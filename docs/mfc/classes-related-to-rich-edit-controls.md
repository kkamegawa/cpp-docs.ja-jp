---
title: リッチ エディット コントロールに関連するクラス
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
ms.openlocfilehash: 349a8b5c26b7260c9af496d0f4a3a997ee753020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327237"
---
# <a name="classes-related-to-rich-edit-controls"></a>リッチ エディット コントロールに関連するクラス

[CRichEditView](../mfc/reference/cricheditview-class.md)、 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)、および[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)リッチ エディット コントロールの機能を提供するクラス ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))MFC のドキュメント/ビュー アーキテクチャのコンテキスト。 `CRichEditView` テキストとテキストの書式設定特性を保持します。 `CRichEditDoc` ビューに含まれる OLE クライアント アイテムの一覧を保持します。 `CRichEditCntrItem` コンテナー側 OLE クライアント アイテムへのアクセスを提供します。 内容を変更する、`CRichEditView`を使用して、 [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl)リッチ エディット コントロールを基になるにアクセスします。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
