---
title: イメージ リストのイメージのドラッグ
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 3035e6f21d38568b364fce02358c3baed4870bc3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508644"
---
# <a name="dragging-images-from-an-image-list"></a>イメージ リストのイメージのドラッグ

[CImageList](../mfc/reference/cimagelist-class.md)には、画面上のイメージをドラッグするための関数が含まれています。 ドラッグ関数は、画像を滑らかに色で移動し、カーソルを点滅させずに移動します。 マスクされた画像とマスクされていない画像は、どちらもドラッグできます。

[Begindrag](../mfc/reference/cimagelist-class.md#begindrag)メンバー関数は、ドラッグ操作を開始します。 パラメーターには、ドラッグするイメージのインデックス、およびイメージ内のホットスポットの位置が含まれます。 ホットスポットは、ドラッグ関数が画像の正確な画面位置として認識する1つのピクセルです。 通常、アプリケーションは、マウスカーソルのホットスポットと一致するようにホットスポットを設定します。 [Dragmove](../mfc/reference/cimagelist-class.md#dragmove)メンバー関数は、イメージを新しい場所に移動します。

[DragEnter](../mfc/reference/cimagelist-class.md#dragenter)メンバー関数は、ウィンドウ内のドラッグイメージの初期位置を設定し、その位置にイメージを描画します。 パラメーターには、イメージを描画するウィンドウへのポインターと、ウィンドウ内の初期位置の座標を指定するポイントが含まれます。 座標は、クライアント領域ではなく、ウィンドウの左上隅を基準としています。 これは、座標をパラメーターとして使用するすべてのイメージドラッグ関数にも当てはまります。 これは、座標を指定するときに、境界線、タイトルバー、メニューバーなどのウィンドウ要素の幅を補正する必要があることを意味します。 を呼び出す`DragEnter`ときに**NULL**ウィンドウハンドルを指定した場合、ドラッグ関数はデスクトップウィンドウに関連付けられたデバイスコンテキストでイメージを描画し、座標は画面の左上隅を基準とします。

`DragEnter`ドラッグ操作中に、指定されたウィンドウに対する他のすべての更新をロックします。 ドラッグアンドドロップ操作の対象を強調表示するなど、ドラッグ操作中に描画を行う必要がある場合は、 [system.windows.dragdrop.dragleave>](../mfc/reference/cimagelist-class.md#dragleave)メンバー関数を使用して、ドラッグしたイメージを一時的に非表示にすることができます。 [Dragshownolock](../mfc/reference/cimagelist-class.md#dragshownolock)メンバー関数を使用することもできます。

画像のドラッグが終了したら、 [Enddrag](../mfc/reference/cimagelist-class.md#enddrag)を呼び出します。

[Setdragcursor イメージ](../mfc/reference/cimagelist-class.md#setdragcursorimage)メンバー関数は、指定されたイメージ (通常はマウスカーソルイメージ) と現在のドラッグイメージを組み合わせて、新しいドラッグイメージを作成します。 ドラッグ関数ではドラッグ操作中に新しいイメージが使用されるため、`SetDragCursorImage` を呼び出した後、Windows の [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) 関数を使用して、実際のマウスカーソルを非表示にする必要があります。 それ以外の場合、ドラッグ操作の間、システムには2つのマウスカーソルが表示されることがあります。

アプリケーションがを呼び`BeginDrag`出すと、システムは一時的な内部イメージリストを作成し、指定されたドラッグイメージを内部リストにコピーします。 [Getdragimage](../mfc/reference/cimagelist-class.md#getdragimage)メンバー関数を使用すると、一時ドラッグイメージリストへのポインターを取得できます。 また、この関数は、ドラッグ位置に対して相対的に、現在のドラッグ位置とドラッグイメージのオフセットを取得します。

## <a name="see-also"></a>関連項目

[CImageList の使い方](../mfc/using-cimagelist.md)<br/>
[コントロール](../mfc/controls-mfc.md)
