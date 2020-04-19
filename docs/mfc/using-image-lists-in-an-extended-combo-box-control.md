---
title: 拡張コンボ ボックス コントロールでのイメージ リストの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 6e4d983d53e49fc8d9c80c206f1a23078eb82f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411553"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>拡張コンボ ボックス コントロールでのイメージ リストの使い方

拡張コンボ ボックス コントロールの主な機能にイメージの一覧からイメージをコンボ ボックス コントロール内の各項目に関連付ける機能があります。 各項目が次の 3 つの異なる画像を表示できる: 選択した状態、その選択解除状態、およびオーバーレイ画像の 3 つ目に 1 つのいずれか。

次の手順では、拡張コンボ ボックス コントロールをイメージ リストを関連付けます。

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>拡張コンボ ボックス コントロールにイメージ リストを関連付ける

1. 新しいイメージ リストの構築 (または既存のイメージ リスト オブジェクトを使用) を使用して、 [CImageList](../mfc/reference/cimagelist-class.md)コンス トラクターと結果のポインターを格納します。

1. 新しいイメージ リスト オブジェクトを呼び出すことによって初期化[CImageList::Create](../mfc/reference/cimagelist-class.md#create)します。 次のコードは、この呼び出しの 1 つの例です。

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. 考えられる各状態用の省略可能なイメージの追加: 選択または選択されていない、およびオーバーレイします。 次のコードは、次の 3 つの定義済みのイメージを追加します。

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. イメージ リストへの呼び出しにコントロールを関連付ける[CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)します。

イメージ リスト コントロールに関連付けられていると、個別には次の 3 つの可能な状態の各項目を使用するイメージを指定できます。 詳細については、次を参照してください。 [、個々 の項目のイメージの設定](../mfc/setting-the-images-for-an-individual-item.md)します。

## <a name="see-also"></a>関連項目

[CComboBoxEx の使い方](../mfc/using-ccomboboxex.md)<br/>
[コントロール](../mfc/controls-mfc.md)
