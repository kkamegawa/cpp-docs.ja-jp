---
title: ドキュメント/ビュー アーキテクチャの利点
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: e250630bf3c9714fc01ff66b66fba3ac0d5b1cc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394729"
---
# <a name="advantages-of-the-documentview-architecture"></a>ドキュメント/ビュー アーキテクチャの利点

MFC ドキュメント/ビュー アーキテクチャを使用する主な利点は、アーキテクチャが同じドキュメントの複数のビューを特にもサポートしています。 (複数のビューが不要なドキュメント/ビューの少量のオーバーヘッドは、アプリケーションで過剰な場合は、回避できますアーキテクチャ。 [ドキュメント/ビュー アーキテクチャの代替手段](../mfc/alternatives-to-the-document-view-architecture.md))。

たとえば、アプリケーションにより、ユーザーがスプレッドシート形式またはグラフ形式で数値データを表示します。 ユーザーは、同時に両方の生データのスプレッドシート形式とデータに起因するグラフを表示する場合があります。 個別のフレーム ウィンドウで、または 1 つのウィンドウ内の分割ペインでは、それぞれのビューを表示します。 ようになりましたユーザーが編集できるを参照してください、スプレッドシート内のデータと変更は瞬時にグラフに反映します。

Mfc では、スプレッドシートのビューとグラフ ビューが基に CView から派生した異なるクラスです。 両方のビューは 1 つのドキュメント オブジェクトに関連付けられたになります。 ドキュメントは、データを保存 (または、データベースから取得)。 両方のビューでは、ドキュメントにアクセスし、そこから取得したデータを表示します。

ユーザーがオブジェクトの呼び出しを表示すると、ビューのいずれかを更新するときに`CDocument::UpdateAllViews`します。 その関数では、すべてのドキュメントのビューに通知し、それぞれのビューは、ドキュメントから最新のデータを使用して自身を更新します。 1 回呼び出す`UpdateAllViews`さまざまなビューを同期します。

このシナリオは、困難なデータの分離を使用しないコードをビューからビューには、自分でデータが格納されている場合に特にがあります。 ドキュメント/ビューでは簡単です。 フレームワークの調整作業のほとんどを動作します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメント/ビューの代替手段](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
