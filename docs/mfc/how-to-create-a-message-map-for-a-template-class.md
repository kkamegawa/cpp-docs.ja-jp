---
title: '方法: テンプレート クラスのメッセージ マップを作成します。'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 676e698a899327eee8305731b5d609b5b95ece76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389503"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>方法: テンプレート クラスのメッセージ マップを作成します。

MFC でのメッセージ マッピングでは、適切な C++ オブジェクトのインスタンスに Windows メッセージを効率的な方法を提供します。 MFC メッセージ マップのターゲットの例には、アプリケーションのクラス、ドキュメントとビュー クラス、コントロールのクラスおよびなどが含まれます。

従来の MFC メッセージ マップを使用して宣言は、 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)マクロをメッセージ マップ マクロ エントリを各メッセージ ハンドラー クラスのメソッドの開始を宣言し、最後に、 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)マクロをメッセージ マップの最後を宣言します。

1 つの制限事項、 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)マクロは、テンプレート引数を含むクラスと組み合わせて使用した場合に発生します。 テンプレート クラスと共に使用するとこのマクロでは、マクロの展開時にテンプレートのパラメーターが不足しているため、コンパイル時エラーが発生します。 [同じよう](reference/message-map-macros-mfc.md#begin_template_message_map)マクロが、独自のメッセージを宣言する 1 つのテンプレート引数を含むクラスのマップを許可するように設計します。

## <a name="example"></a>例

例を考えて、MFC [CListBox](../mfc/reference/clistbox-class.md)外部データ ソースとの同期を提供するクラスを拡張します。 架空`CSyncListBox`クラスに次のように宣言されます。

[!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`クラスは、データ ソースと同期することを説明する 1 つの型で template 宣言されます。 クラスのメッセージ マップに参加する 3 つのメソッドも宣言されています: `OnPaint`、 `OnDestroy`、および`OnSynchronize`します。 `OnSynchronize`メソッドは次のように実装されます。

[!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

上記の実装を使用、`CSyncListBox`クラスを実装する任意のクラス型に特殊化する、`GetCount`メソッドなど`CArray`、 `CList`、および`CMap`します。 `StringizeElement`関数は、以下にプロトタイプ宣言されたテンプレート関数です。

[!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

通常、このクラスのメッセージ マップとして定義します。

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

場所**LBN_SYNCHRONIZE**など、アプリケーションで定義されたカスタム ユーザー メッセージします。

[!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

上記のマクロのマップはコンパイルされません原因という事実にテンプレートの仕様、`CSyncListBox`クラスはマクロの展開中に失われます。 **同じよう**マクロが展開されたマクロのマップに指定されたテンプレート パラメーターを組み込むことによってこれを解決します。 このクラスのメッセージ マップになります。

[!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

次の使用例を示します、`CSyncListBox`クラスを使用して、`CStringList`オブジェクト。

[!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

テストを完了する、`StringizeElement`関数を使用する特殊化する必要があります、`CStringList`クラス。

[!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>関連項目

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[メッセージの処理とマップ](../mfc/message-handling-and-mapping.md)
