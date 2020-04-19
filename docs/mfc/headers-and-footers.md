---
title: ヘッダーとフッター
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 1e2e57331ccbc7f0afd7b82dc035410af495abd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297230"
---
# <a name="headers-and-footers"></a>ヘッダーとフッター

この記事では、ヘッダーとフッターを印刷したドキュメントに追加する方法について説明します。

画面のドキュメントを参照するときに、ドキュメントと、ドキュメントで現在の場所の名前がタイトル バーおよびステータス バーによく表示されます。 ドキュメントの印刷を見たときに、ヘッダーまたはフッターに表示名とページ番号にすると便利です。 これは、どのでも WYSIWYG でプログラムの異なる印刷および画面表示の実行での一般的な方法です。

[OnPrint](../mfc/reference/cview-class.md#onprint)メンバー関数は、ページごとに呼び出されるため、および画面表示ではなく、印刷にのみ呼び出されるために、ヘッダーまたはフッターを印刷する適切な場所。 ヘッダーまたはフッターを印刷する個別の関数を定義してから、プリンター デバイス コンテキストを渡す`OnPrint`します。 配信元のウィンドウまたは呼び出す前に範囲を調整する必要があります[OnDraw](../mfc/reference/cview-class.md#ondraw)本文、ヘッダーまたはページ フッター、ページが重なるを避けるようにします。 変更する必要がありますも`OnDraw` ページに適合するドキュメントの量を削減することがあるためです。

補正は、ヘッダーまたはフッターで使用されている領域を使用する 1 つの方法、 **m_rectDraw**のメンバー [CPrintInfo](../mfc/reference/cprintinfo-structure.md)します。 ページが印刷されるたびにこのメンバーは、ページの使用可能な領域で初期化されます。 格納されている四角形のサイズを小さくには、ページの本文を印刷する前に、ヘッダーまたはフッターを印刷する場合**m_rectDraw**ヘッダーまたはフッターで使用されている領域を考慮します。 `OnPrint`を参照できます**m_rectDraw**量の領域は、印刷ページの本文を確認します。

ヘッダー、または、他のものを印刷することはできません[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)、前に呼び出されるため、`StartPage`のメンバー関数[CDC](../mfc/reference/cdc-class.md)が呼び出されました。 その時点では、プリンター デバイス コンテキストは、ページの境界であると見なされます。 印刷だけを行うことができます、`OnPrint`メンバー関数。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [マルチページ ドキュメント](../mfc/multipage-documents.md)

- [印刷の GDI リソースの割り当てください。](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>関連項目

[印刷](../mfc/printing.md)
