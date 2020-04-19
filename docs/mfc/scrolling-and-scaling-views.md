---
title: ビューのスクロールと拡大/縮小
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511232"
---
# <a name="scrolling-and-scaling-views"></a>ビューのスクロールと拡大/縮小

MFC では、スクロールとビューを表示するフレームウィンドウのサイズに自動的に拡大縮小するビューがサポートされています。 クラス`CScrollView`では、両方の種類のビューがサポートされています。

スクロールとスケーリングの詳細については、 *MFC リファレンス*の「クラス[CScrollView](../mfc/reference/cscrollview-class.md) 」を参照してください。 スクロールの例については、 [Scribble サンプル](../overview/visual-cpp-samples.md)を参照してください。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- スクロール (ビューを)

- ビューのスケーリング

- [座標の表示](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>スクロール (ビューを)

多くの場合、ドキュメントのサイズが、ビューに表示できるサイズを超えています。 これは、ドキュメントのデータが増加したり、ユーザーがビューをフレームするウィンドウを縮小したりした場合に発生する可能性があります。 このような場合は、ビューがスクロールをサポートしている必要があります。

ビューでは、 `OnHScroll`および`OnVScroll`メンバー関数内のスクロールバーメッセージを処理できます。 これらの関数では、スクロールバーのメッセージ処理を実装して、すべての作業を自分で実行する`CScrollView`か、クラスを使用してスクロール処理を行うことができます。

`CScrollView` では次の処理が行われます。

- ウィンドウおよびビューポートのサイズとマッピングモードを管理します

- スクロールバーのメッセージに応じて自動的にスクロールする

"ページ" のスクロール間隔 (ユーザーがスクロールバーのシャフトをクリックしたとき) と "線" (スクロールバーの矢印ボタンをクリックしたとき) を指定できます。 ビューの特性に合わせて、これらの値を計画します。 たとえば、グラフィックスビューでは1ピクセル単位でスクロールできますが、テキストドキュメントの行の高さに応じて徐々にスクロールすることができます。

##  <a name="_core_scaling_a_view"></a>ビューのスケーリング

ビューがフレームウィンドウのサイズに合わせて自動的に調整されるようにするに`CScrollView`は、スクロールではなく、を使用して拡大縮小を行うことができます。 論理ビューは、ウィンドウのクライアント領域に正確に合わせるために拡大または縮小されます。 スケールされたビューにはスクロールバーがありません。

## <a name="see-also"></a>関連項目

[ビューの使い方](../mfc/using-views.md)
