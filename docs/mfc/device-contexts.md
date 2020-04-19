---
title: デバイス コンテキスト
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508659"
---
# <a name="device-contexts"></a>デバイス コンテキスト

デバイスコンテキストは、ディスプレイやプリンターなどのデバイスの描画属性に関する情報を含む Windows データ構造です。 すべての描画呼び出しはデバイスコンテキストオブジェクトを使用して行われます。これにより、線、図形、テキストを描画するための Windows Api がカプセル化されます。 デバイスコンテキストでは、Windows でデバイスに依存しない描画を実行できます。 デバイスコンテキストは、画面、プリンター、またはメタファイルに描画するために使用できます。

[CPaintDC](../mfc/reference/cpaintdc-class.md)オブジェクトは、Windows の共通表現をカプセル化`BeginPaint`し、関数を呼び出した後、デバイスコンテキストで描画`EndPaint`した後、関数を呼び出します。 コンストラクター `CPaintDC`はを`BeginPaint`呼び出し、デストラクターはを呼び出し`EndPaint`ます。 簡略化されたプロセスは、 [CDC](../mfc/reference/cdc-class.md)オブジェクトを作成して描画し、 `CDC`オブジェクトを破棄することです。 フレームワークでは、このプロセスの多くが自動化されています。 特に、 `OnDraw`関数には既に`CPaintDC`準備された`OnPrepareDC`(経由で) が渡され、それに単に描画するだけです。 これはフレームワークによって破棄され、基になるデバイスコンテキストは、 `OnDraw`関数の呼び出しから戻った時点で Windows に解放されます。

[Cclientdc](../mfc/reference/cclientdc-class.md)オブジェクトは、ウィンドウのクライアント領域のみを表すデバイスコンテキストの操作をカプセル化します。 コンストラクター `CClientDC`は`GetDC`関数を呼び出し、デストラクターは`ReleaseDC`関数を呼び出します。 [CWindowDC](../mfc/reference/cwindowdc-class.md)オブジェクトは、フレームを含む、ウィンドウ全体を表すデバイスコンテキストをカプセル化します。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)オブジェクトは、描画を Windows メタファイルにカプセル化します。 に`CPaintDC` 渡さ`OnDraw`れるとは対照的に、この場合は自分で[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)を呼び出す必要があります。

## <a name="mouse-drawing"></a>マウスの描画

フレームワークプログラムにおけるほとんどの描画 (つまり、ほとんどのデバイスコンテキストの作業) は、ビューの`OnDraw`メンバー関数で実行されます。 ただし、他の目的でデバイスコンテキストオブジェクトを使用することもできます。 たとえば、ビューでのマウスの動きに関するフィードバックを追跡するには、が呼び出されるの`OnDraw`を待たずに、ビューに直接描画する必要があります。

このような場合は、 [Cclientdc](../mfc/reference/cclientdc-class.md)デバイスコンテキストオブジェクトを使用して、ビューに直接描画できます。

### <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [デバイスコンテキスト (定義)](/windows/win32/gdi/device-contexts)

- [ビューの描画](../mfc/drawing-in-a-view.md)

- [ビューを経由したユーザー入力の解釈](../mfc/interpreting-user-input-through-a-view.md)

- [線と曲線](/windows/win32/gdi/lines-and-curves)

- [塗りつぶされた図形](/windows/win32/gdi/filled-shapes)

- [フォントとテキスト](/windows/win32/gdi/fonts-and-text)

- [色](/windows/win32/gdi/colors)

- [座標空間と変換](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>関連項目

[Window オブジェクト](../mfc/window-objects.md)
