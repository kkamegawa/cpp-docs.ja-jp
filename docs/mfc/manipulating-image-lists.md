---
title: イメージ リストの操作
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 1e86961980c91ade47a3d6510dec5c04ac36cffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262789"
---
# <a name="manipulating-image-lists"></a>イメージ リストの操作

[置換](../mfc/reference/cimagelist-class.md#replace)メンバー関数は、イメージ リスト内のイメージ ([CImageList](../mfc/reference/cimagelist-class.md)) 新しいイメージを使用します。 この関数もイメージ リスト オブジェクト内のイメージの数を動的に増加する必要がある場合に役立ちます。 [呼び出す前](../mfc/reference/cimagelist-class.md#setimagecount)関数は、イメージ リストに格納されているイメージの数を動的に変更します。 イメージ リストのサイズを大きくした場合は、呼び出す`Replace`イメージの新しいスロットにイメージを追加します。 イメージ リストのサイズを小さくした場合は、新しいサイズを超えるイメージが解放されます。

[削除](../mfc/reference/cimagelist-class.md#remove)メンバー関数は、イメージの一覧からイメージを削除します。 [コピー](../mfc/reference/cimagelist-class.md#copy)メンバー関数は、コピーまたはイメージ リスト内のイメージをスワップできます。 この関数を使用すると、ソース イメージは、コピー先のインデックスにコピーする必要がありますか、ソースと宛先のイメージを交換するかを示すことができます。

2 つのイメージ リストをマージすることで、新しいイメージ リストを作成するには、適切なオーバー ロードを使用して、[作成](../mfc/reference/cimagelist-class.md#create)メンバー関数。 このオーバー ロード`Create`マージの結果のイメージを格納する新しいイメージ リスト オブジェクト内の既存のイメージは、最初のイメージが一覧表示します。 最初に透過的に 2 番目のイメージを描画することで、新しいイメージが作成されます。 新しいイメージのマスクは、2 つの既存のイメージのマスクのビットの論理 OR 演算を実行した結果です。

すべてのイメージがマージされ、新しいイメージ リスト オブジェクトに追加されるまでは、これが繰り返されます。

イメージ情報をアーカイブに記述するには呼び出すことによって、[書き込み](../mfc/reference/cimagelist-class.md#write)メンバー関数は、そのファイルを読み取る呼び出すことによって、[読み取り](../mfc/reference/cimagelist-class.md#read)メンバー関数。

[GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle)、[アタッチ](../mfc/reference/cimagelist-class.md#attach)、および[デタッチ](../mfc/reference/cimagelist-class.md#detach)メンバー関数を使用するに接続されているイメージ リストのハンドルを操作するため、`CImageList`オブジェクト、中に、[DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist)メンバー関数では、イメージ リストを削除を破棄せず、`CImageList`オブジェクト。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)
