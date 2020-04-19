---
title: ビューの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
ms.openlocfilehash: 81668f7409f2b1a4480bde958dc06ce1156e03fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411423"
---
# <a name="using-views"></a>ビューの使い方

ビューの役割では、ユーザーに、ドキュメントのデータをグラフィカルに表示し、、受け入れるし、ドキュメントに対する操作としてユーザー入力を解釈します。 ビュー クラスの作成で、タスクは次のとおりです。

- ビュー クラスの記述[OnDraw](../mfc/reference/cview-class.md#ondraw)メンバー関数は、ドキュメントのデータを表示します。

- ビュー クラスのメッセージ ハンドラー メンバー関数には、適切な Windows メッセージとメニュー項目などのユーザー インターフェイス オブジェクトを接続します。

- ユーザー入力を解釈するハンドラーを実装します。

さらに、その他をオーバーライドする必要があります`CView`派生ビュー クラスのメンバー関数。 具体的には、無効にすることがあります[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)ビューの特別な初期化を実行して[OnUpdate](../mfc/reference/cview-class.md#onupdate)ビュー自体を再描画する前に必要な特別な処理を実行します。 マルチページ ドキュメントは、オーバーライドすることも必要があります[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)を印刷するページとその他の情報の数と印刷 ダイアログ ボックスを初期化します。 オーバーライドの詳細については`CView`のメンバー関数は、クラスを参照してください[CView](../mfc/reference/cview-class.md)で、 *MFC リファレンス*します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [MFC で使用できる派生ビュー クラス](../mfc/derived-view-classes-available-in-mfc.md)

- [ビューの描画](../mfc/drawing-in-a-view.md)

- [ビューによるユーザー入力を解釈します。](../mfc/interpreting-user-input-through-a-view.md)

- [印刷でのビューの役割](../mfc/role-of-the-view-in-printing.md)

- [スケール ビューのスクロールと](../mfc/scrolling-and-scaling-views.md)

- [ドキュメントとビューの初期化と後処理](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)<br/>
[CFormView クラス](../mfc/reference/cformview-class.md)<br/>
[レコード ビュー (MFC データ アクセス)](../data/record-views-mfc-data-access.md)<br/>
[シリアル化機構のバイパス](../mfc/bypassing-the-serialization-mechanism.md)
