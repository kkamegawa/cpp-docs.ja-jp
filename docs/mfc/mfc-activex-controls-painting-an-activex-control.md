---
title: MFC ActiveX コントロール:ActiveX コントロールの描画
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: b90aa331c289caf827785af2eeba037e70f686ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186880"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールの描画

この記事では、ActiveX コントロールの描画プロセスとプロセスを最適化する描画コードを変更する方法について説明します。 (を参照してください[コントロールの描画の最適化](../mfc/optimizing-control-drawing.md)ないコントロールを個別に描画を最適化する方法の手法が以前に選択した GDI オブジェクトを復元します。 すべてのコントロールが描画されたコンテナーが自動的に復元元のオブジェクトです。)

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

この記事の例では既定の設定では、MFC ActiveX コントロール ウィザードによって作成されたコントロールです。 MFC ActiveX コントロール ウィザードを使用してアプリケーションのスケルトンのコントロールを作成する方法の詳細については、この記事を参照してください。 [MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)します。

次のトピックについて説明します。

- [描画コントロールと描画をサポートするために、ActiveX コントロール ウィザードで作成したコードの全体的なプロセス](#_core_the_painting_process_of_an_activex_control)

- [描画プロセスを最適化する方法](#_core_optimizing_your_paint_code)

- [メタファイルを使ってコントロールを描画する方法](#_core_painting_your_control_using_metafiles)

##  <a name="_core_the_painting_process_of_an_activex_control"></a> ActiveX コントロールの描画プロセス

ActiveX コントロールは、最初に表示されるまたは再描画されると、これらの重要な違いと、MFC を使用して開発された他のアプリケーションのような描画プロセスに従います。ActiveX コントロールは、アクティブまたは非アクティブな状態にできます。

アクティブなコントロールは、子ウィンドウによって ActiveX コントロール コンテナーで表されます。 など、他のウィンドウを担当 WM_PAINT メッセージが受信したときに自身を描画します。 コントロールの基底クラス、 [COleControl](../mfc/reference/colecontrol-class.md)でメッセージを処理、`OnPaint`関数。 この既定の実装、`OnDraw`コントロールの関数。

異なる方法で、非アクティブなコントロールが描画されます。 コントロールがアクティブでない場合は、そのウィンドウは非表示、または存在しない場合は、あるため、描画メッセージを受け取ることができません。 コントロールのコンテナーを直接呼び出す代わりに、`OnDraw`コントロールの機能です。 一方、アクティブなコントロールの描画プロセス、`OnPaint`メンバー関数を呼び出すことはありません。

上記のようは、ActiveX コントロールを更新する方法、コントロールの状態に依存します。 ただし、フレームワークが呼び出すため、`OnDraw`メンバー関数はどちらの場合も、このメンバー関数で描画コードの大部分を追加します。

`OnDraw`メンバー関数は、コントロールの描画を処理します。 コントロールがアクティブでない場合は、コントロールのコンテナーを呼び出す`OnDraw`、コントロール コンテナーのデバイス コンテキストと、コントロールによって占有されている四角形領域の座標。

四角形のためにフレームワークによって渡される、`OnDraw`メンバー関数には、コントロールによって占有される領域が含まれています。 左上隅には、コントロールがアクティブな場合は、(0, 0) とコントロールを含む子ウィンドウは、渡されたデバイス コンテキスト。 コントロールがアクティブでない場合、左上隅の座標が必ずしも (0, 0) とコントロールを含むコントロールのコンテナーは、渡されたデバイス コンテキスト。

> [!NOTE]
>  重要ですが変更内容を適用`OnDraw`四角形の左上の点に等しくないに依存しない (0, 0) に渡される四角形の内部でのみ描画して`OnDraw`します。 予期しない結果は、四角形の領域外に描画する場合に発生することができます。

MFC ActiveX コントロール ウィザード、コントロール実装ファイルによって提供される既定の実装 (します。CPP)、表示される以下では、白のブラシを含む四角形を描画し、現在の背景色で楕円を塗りつぶします。

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
>  コントロールを描画するときにする必要がありますいないとして渡されるデバイス コンテキストの状態に関する前提条件、 *pdc*パラメーターを`OnDraw`関数。 場合によってはデバイス コンテキストでは、コンテナーのアプリケーションによって提供され、既定の状態には必ずしも初期化されません。 ペン、ブラシ、色、フォント、および描画コードが依存するその他のリソースを明示的に選択具体的には、します。

##  <a name="_core_optimizing_your_paint_code"></a> 描画コードの最適化

次の手順を最適化するためには、コントロールが自身を正常に描画は、後に、`OnDraw`関数。

ActiveX コントロールの描画の既定の実装では、コントロール全体の領域を描画します。 これは単純なコントロールのための十分なも多くの場合、コントロールを再描画は高速コントロール全体ではなく更新が必要な部分が再描画だけの場合。

`OnDraw`関数を渡すことによって最適化の簡単な方法を提供する*rcInvalid*、再描画が必要なコントロールの四角形の領域。 描画プロセスを効率化、コントロール全体の領域より小さく、通常、この領域を使用します。

##  <a name="_core_painting_your_control_using_metafiles"></a> メタファイルを使用して、コントロールの描画

ほとんどの場合、 *pdc*パラメーターを`OnDraw`関数は、画面のデバイス コンテキスト (DC) を指します。 ただし、または印刷プレビュー セッション中に、コントロールのイメージを印刷する場合は、レンダリングの受信 DC は「メタファイル DC」と呼ばれる特殊な種類には。 送信された要求をすぐに処理するには、画面の DC の場合とは異なりは、メタファイル DC は、後で再生する要求を格納します。 一部のコンテナー アプリケーションは、メタファイル デザイン モードで DC を使用してコントロールのイメージをレンダリングすることもできます。

インターフェイスの 2 つの関数を使用して、コンテナーによって要求を描画するメタファイルを行んだことができます: `IViewObject::Draw` (この関数は呼び出すことも非メタファイル描画の) と`IDataObject::GetData`します。 MFC フレームワークへの呼び出しは、ときに DC がいずれかのパラメーターとして渡されるメタファイル、 [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile)します。 これは、仮想メンバー関数であるため、特別な処理を実行するコントロール クラスのこの関数をオーバーライドします。 既定の動作呼び出し`COleControl::OnDraw`します。

画面とメタファイルの両方のデバイス コンテキストではをコントロールを描画できるようにするには、画面とメタファイルの DC の両方でサポートされているメンバー関数のみを使用する必要があります。 座標系をピクセル単位で計測いない可能性がありますに注意します。

の既定の実装`OnDrawMetafile`コントロールの呼び出す`OnDraw`関数を上書きしない限り、メタファイルと、画面のデバイス コンテキストの両方に適しているメンバー関数のみを使用して`OnDrawMetafile`します。 サブセットを次に示します`CDC`メタファイルと画面のデバイス コンテキストの両方で使用できるメンバー関数。 これらの関数の詳細については、クラスを参照してください。 [CDC](../mfc/reference/cdc-class.md)で、 *MFC リファレンス*します。

|円弧|BibBlt|コード|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

加え`CDC`メンバー関数は、メタファイル DC で互換性のあるその他のいくつかの関数があります。 以下の[CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette)、 [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)、および 3 つのメンバー関数の`CBrush`:[CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect)、[構築](../mfc/reference/cbrush-class.md#createdibpatternbrush)、および[とき](../mfc/reference/cbrush-class.md#createpatternbrush)します。

メタファイルには記録されません関数は次のとおりです。[消去](../mfc/reference/cdc-class.md#drawfocusrect)、 [DrawIcon](../mfc/reference/cdc-class.md#drawicon)、 [DrawText](../mfc/reference/cdc-class.md#drawtext)、 [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn)、 [FillRect](../mfc/reference/cdc-class.md#fillrect)、 [FrameRect](../mfc/reference/cdc-class.md#framerect)、[とき](../mfc/reference/cdc-class.md#graystring)、 [InvertRect](../mfc/reference/cdc-class.md#invertrect)、 [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)、および[TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout)します。 メタファイル DC が実際には、デバイスに関連付けられていないためには、メタファイル DC で SetDIBits、GetDIBits、および CreateDIBitmap を使用できません。 コピー先として、メタファイル DC で SetDIBitsToDevice と StretchDIBits を使用できます。 [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc)、[ビットマップ](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)、および[CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap)はメタファイル DC で意味がありません。

メタファイルの DC を使用する際に別のポイントは、座標系をピクセル単位で計測いない可能性があります。 このため、四角形に収まるように、描画のコードを調整する必要がすべて成功する`OnDraw`で、 *rcBounds*パラメーター。 これにより、コントロール外の描画、ため*rcBounds*コントロールのウィンドウのサイズを表します。

コントロールのレンダリングをメタファイルを実装した後は、メタファイルをテストするのにテスト コンテナーを使用します。 Test Container にアクセスする方法について詳しくは、「 [テスト コンテナーでのプロパティとイベントのテスト](../mfc/testing-properties-and-events-with-test-container.md) 」をご覧ください。

#### <a name="to-test-the-controls-metafile-using-test-container"></a>テスト コンテナーを使用して、コントロールのメタファイルをテストするには

1. テスト コンテナーの**編集** メニューのをクリックして**新しいコントロールを挿入**します。

1. **新しいコントロールを挿入**ボックスで、コントロールを選択し、をクリックして**OK**します。

   コントロールは、テスト コンテナーに表示されます。

1. **コントロール** メニューのをクリックして**を描画するメタファイル**します。

   メタファイルを表示する別のウィンドウが表示されます。 スケーリングがコントロールのメタファイルに与える影響を確認するには、このウィンドウのサイズを変更することができます。 このウィンドウは、いつでも閉じることができます。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
