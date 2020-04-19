---
title: グラフィック オブジェクトをデバイス コンテキストに選択する
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: 7fb1507c1200da4cdf44627557ff6993e927d51e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308531"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>グラフィック オブジェクトをデバイス コンテキストに選択する

このトピックでは、ウィンドウのデバイス コンテキストでグラフィック オブジェクトの使用に適用されます。 したら[描画オブジェクトを作成](../mfc/one-stage-and-two-stage-construction-of-objects.md)、格納されている既定のオブジェクトの代わりに、デバイス コンテキストに選択する必要があります。

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>グラフィック オブジェクトの有効期間

によって返されるグラフィック オブジェクト[SelectObject](../mfc/reference/cdc-class.md#selectobject)は「一時的なものです」。 つまりも削除して、 [OnIdle](../mfc/reference/cwinapp-class.md#onidle)クラスのメンバー関数`CWinApp`次回プログラム取得アイドル時間します。 によって返されるオブジェクトを使用する限り`SelectObject`コントロールをメイン メッセージ ループを返さずに 1 つの関数、するは問題ありません。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [グラフィック オブジェクト](../mfc/graphic-objects.md)

- [グラフィック オブジェクトの 1 つのステージと 2 段階の構築](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [デバイス コンテキスト](../mfc/device-contexts.md)

- [ビューの描画](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>関連項目

[グラフィック オブジェクト](../mfc/graphic-objects.md)
