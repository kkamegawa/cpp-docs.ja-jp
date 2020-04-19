---
title: ドキュメント/ビュー アーキテクチャの全体像
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: 51f963acf5aacdfe4050a076d3bb0e651a92d021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392976"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>ドキュメント/ビュー アーキテクチャの全体像

一般的な MFC アプリケーションでは、ドキュメントとビューがペアリングされます。 ドキュメント内のデータが格納されているが、ビューは、データへのアクセスを特権します。 ビューからドキュメントの分離は、その表示から、ストレージとデータのメンテナンスを区切ります。

## <a name="gaining-access-to-document-data-from-the-view"></a>ドキュメント、ビューからデータにアクセスするため

ビュー データにアクセスする、ドキュメントのいずれかで、 [GetDocument](../mfc/reference/cview-class.md#getdocument)関数は、ドキュメント、または C++ のクラス ビューを作成して、ポインターを返します`friend`ドキュメント クラスの。 ビューは、このデータへのアクセスを使用して描画したり、それ以外の場合を操作するのに準備ができた場合は、データを取得します。

ビューの例: から[OnDraw](../mfc/reference/cview-class.md#ondraw)ビューで使用するメンバー関数は、`GetDocument`ドキュメント ポインターを取得します。 アクセスにそのポインターを使用して、`CString`ドキュメント内のデータ メンバー。 文字列に、ビュー、`TextOut`関数。 この例のコードを表示するには、次を参照してください。[ビューの描画](../mfc/drawing-in-a-view.md)します。

## <a name="user-input-to-the-view"></a>ビューにユーザー入力

ビューの選択またはデータの編集のいずれかとしてそれ自体の中のマウス クリック解釈できます。 同様に、データ入力または編集としてキーストロークを解釈可能性があります。 テキストを管理するビューで、ユーザーの種類を文字列とします。 ビューは、ドキュメントへのポインターを取得し、ポインターを使用して、ドキュメントでは、いくつかのデータ構造に格納する新しいデータを渡します。

## <a name="updating-multiple-views-of-the-same-document"></a>同じドキュメントの複数のビューを更新しています

アプリケーションで同じドキュメントの複数のビュー-テキスト エディターでの分割ウィンドウなど、ビューがドキュメントに最初に、新しいデータを渡します。 ドキュメントの呼び出して[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)メンバー関数を新しいデータを反映して更新するためにドキュメントのすべてのビューが示されます。 これは、ビューを同期します。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメント/ビュー アーキテクチャの利点](../mfc/advantages-of-the-document-view-architecture.md)

- [ドキュメント/ビュー アーキテクチャの代替手段](../mfc/alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
