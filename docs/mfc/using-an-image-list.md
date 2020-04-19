---
title: イメージ リストの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180467"
---
# <a name="using-an-image-list"></a>イメージ リストの使い方

イメージ リストの一般的な使用方法では、次のパターンに従います。

- 構築、 [CImageList](../mfc/reference/cimagelist-class.md)オブジェクトし、のオーバー ロードの 1 つを呼び出してその[作成](../mfc/reference/cimagelist-class.md#create)をイメージ リストを作成し、アタッチ先、`CImageList`オブジェクト。

- イメージ リストの作成時にイメージを追加しなかった場合に、イメージを追加、イメージ リストを呼び出して、[追加](../mfc/reference/cimagelist-class.md#add)または[読み取り](../mfc/reference/cimagelist-class.md#read)メンバー関数。

- コントロールに、そのコントロールの適切なメンバー関数を呼び出すことによって、イメージ リストを関連付けるまたはのイメージ リストを使用して自分でイメージ リストからイメージを描画[描画](../mfc/reference/cimagelist-class.md#draw)メンバー関数。

- おそらくをドラッグするイメージ リストの組み込みサポートを使用して、イメージをドラッグするユーザーを許可します。

> [!NOTE]
>  イメージ リストの作成に使用された場合、**新しい**破棄する必要があります、演算子、`CImageList`オブジェクトとそれが済んだらします。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)
