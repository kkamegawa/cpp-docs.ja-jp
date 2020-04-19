---
title: TN029:分割ウィンドウ
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: 6c2f619d9cd619ca598c66ca657faa1b9dccaaa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305711"
---
# <a name="tn029-splitter-windows"></a>TN029:分割ウィンドウ

この注の説明、MFC [CSplitterWnd クラス](../mfc/reference/csplitterwnd-class.md)ウィンドウを分割し、他のウィンドウのウィンドウのサイズ変更の管理を提供します。

## <a name="splitter-styles"></a>分割線のスタイル

A`CSplitterWnd`ウィンドウの分割の 2 つの異なるスタイルをサポートしています。

「静的分割ウィンドウ」では、分割ウィンドウは、作成時に、ウィンドウを作成します。 ペインの数、順序を変更ことはありません。 分割バーを使用して、異なるペインのサイズを変更します。 このスタイルを使用すると、各ウィンドウに別のビュー クラスを表示します。 Visual C のグラフィックス エディターと Windows ファイル マネージャーは、この分割線のスタイルを使用するプログラムの例を示します。 このスタイルの分割ウィンドウでは、分割ボックスは使用しません。

「動的分割ウィンドウ」の他のウィンドウが作成され、ユーザーの分割と解除分割の新しいビューとして破棄します。 このスプリッターは、まず、1 つのビューと、分割するためのユーザーの分割ボックスを提供します。 分割ウィンドウは、ビューは、1 つの方向に分割されるときに、新しいビュー オブジェクトを動的に作成します。 この新しいビュー オブジェクトは、新しいウィンドウを表します。 ビューは、キーボード インターフェイスを使用して 2 つの方向に分割される、分割ウィンドウは 3 つの新しいウィンドウの 3 つの新しいビュー オブジェクトを作成します。 分割がアクティブな間は、Windows が分割ボックス、ペイン間を分割バーとして表示されます。 Windows は、ユーザーに分割するが削除されますが、分割ウィンドウ自体までビューは、元のままですが破棄されるときに、追加のビュー オブジェクトを破棄します。 Microsoft Excel や Microsoft Word は、動的な分割線のスタイルを使用するアプリケーションの例を示します。

スプリッター ウィンドウのいずれかの種類を作成するときに、スプリッターを管理する行と列の最大数を指定する必要があります。 静的分割ウィンドウでは、すべての行と列を入力するウィンドウを作成します。 動的分割は、最初のウィンドウのみを作成時に、`CSplitterWnd`が作成されます。

静的分割ウィンドウに指定できるウィンドウの最大数は 16 個の列が 16 の行です。 推奨される構成は次のとおりです。

- 1 行 x 2 列: 異種ペインで、通常は

- 2 行 x 1 列: 異種ペインで、通常は

- 2 行 x 2 列: のようなウィンドウを持つ通常

動的分割ウィンドウで指定できるウィンドウの最大数は、2 つの列での 2 行です。 推奨される構成は次のとおりです。

- 1 行 x 2 列: 単票形式データ

- 2 行 x 1 列: テキストまたはその他のデータ

- 2 行 x 2 列: 表形式のデータ

## <a name="splitter-examples"></a>分割ウィンドウの例

分割ウィンドウは、直接または間接的に MFC のサンプル プログラムの多く使用します。 MFC 標準サンプル[VIEWEX](../overview/visual-cpp-samples.md)静的分割ウィンドウ、分割ウィンドウでスプリッターを配置する方法などのいくつかの使用を示しています。

複数ドキュメント インターフェイス (MDI) 子フレーム ウィンドウ クラスを含む分割ウィンドウを新しく作成するのに ClassWizard を使用することもできます。 分割ウィンドウの詳細については、次を参照してください。[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../mfc/multiple-document-types-views-and-frame-windows.md)します。

## <a name="terminology-used-by-implementation"></a>実装で使用される用語集

分割ウィンドウに固有の用語の一覧を次に示します。

`CSplitterWnd`:ペイン分割コントロールと上の行または列のすべてのペイン間で共有されるスクロール バーを提供するウィンドウです。 0 から始まる番号を持つ行と列を指定する (最初のウィンドウは、行 = 0 and 列 = 0)。

ウィンドウ:特定のアプリケーション ウィンドウを`CSplitterWnd`を管理します。 ペインがから派生したオブジェクトでは通常、 [CView クラス](../mfc/reference/cview-class.md)、いずれかを指定できますが、 [CWnd](../mfc/reference/cwnd-class.md)適切な子ウィンドウ ID を持つオブジェクト

使用する、 `CWnd`-派生オブジェクトを渡すオブジェクトの対象となる、`CreateView`関数を使用していた場合と同様、 `CView`-クラスを派生します。 クラスは、フレームワークは、実行時に動的な作成を使用するため DECLARE_DYNCREATE と IMPLEMENT_DYNCREATE を使用する必要があります。 大量のコードが`CSplitterWnd`に固有です、`CView`クラス、[使うため](../mfc/reference/cobject-class.md#iskindof)はこれらのアクションを実行する前に常に使用します。

分割バー:ペインの行と列の間に配置されるコントロール。 これを使用して、行のサイズまたはウィンドウの列を調整できます。

分割ボックス:動的コントロール`CSplitterWnd`ペインの新しい行または列の作成を行えます。 または、水平スクロール バーの左側に垂直スクロール バーの上部になります。

スプリッターの積集合:垂直方向の分割バーと水平方向の分割バーの交差部分。 同時にウィンドウの列や行のサイズを調整するドラッグすることができます。

## <a name="shared-scroll-bars"></a>共有のスクロール バー

`CSplitterWnd`クラスには、共有のスクロール バーもサポートしています。 これらのスクロール バー コントロールの子である、`CSplitterWnd`と分割ウィンドウの各ペインと共有されます。

たとえば、x 2 は 1 行の列 ウィンドウで指定できます WS_VSCROLL を作成するとき、`CSplitterWnd`します。 Windows では、2 つのペイン間で共有される特殊なスクロール バー コントロールを作成します。

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

ユーザーは、スクロール バーを移動したときは WM_VSCROLL メッセージを送信して両方のビュー。 いずれかのビューがスクロール バーの位置を設定すると、共有のスクロール バーが設定されます。

共有のスクロール バーが同様のビュー オブジェクトで最も役に立つことに注意してください。 分割ウィンドウ内のさまざまな種類のビューが混在する場合のスクロール位置を調整するための特別なコードを記述する必要があります。 すべて`CView`-派生クラスを使用する、`CWnd`スクロール バーが存在する場合は、Api を共有のスクロール バーを委任します。 `CScrollView`実装は 1 つの例を`CView`をサポートするクラスは、スクロール バーを共有します。 クラスから派生していない`CView`、非コントロールのスクロール バーに依存するクラスまたは標準の Windows 実装を使用するクラス (たとえば、 `CEditView`) の共有のスクロール バーの機能では動作しません`CSplitterWnd`します。

## <a name="minimum-sizes"></a>最小サイズ

行ごとには、各行の高さと幅の最小値がある各列に対して。 この最小値は、ウィンドウが小さすぎて完全な詳細に表示をしないことを保証します。

静的分割ウィンドウで、最初の行の最小の高さと列の幅は 0 です。 動的分割ウィンドウで、最初の行の最小の高さと列の幅を設定して、、 *sizeMin*のパラメーター、`CSplitterWnd::Create`関数。

使用してこれらの最小サイズを変更することができます、 [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo)と[CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo)関数。

## <a name="actual-vs-ideal-sizes"></a>実際のサイズと理想的なサイズ

スプリッター ウィンドウのペインのレイアウトは、それらを含むフレームのサイズによって異なります。 ユーザーは、フレームをサイズ変更時に、`CSplitterWnd`位置を変更して、ウィンドウのサイズを変更できるだけ効率よくに収まるようにします。

ユーザーに手動で設定行の高さと列の幅のサイズ、またはプログラムを使用して適切なサイズを設定することができます、`CSplitterWnd`クラス。 実際のサイズは、理想より小さいか大きいできます。 適切なサイズを表示する十分な空き領域がない場合、または右端またはスプリッター ウィンドウの下部に空の領域が多すぎる場合、Windows は実際のサイズを調整します。

## <a name="custom-controls"></a>カスタム コントロール

カスタマイズされた動作とカスタマイズされたインターフェイスを提供する多くの関数をオーバーライドすることができます。 スプリッター ウィンドウのさまざまなグラフィカル要素の外観を提供するこの最初のセットを上書きできます。

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

共有のスクロール バー コントロールを作成するには、この関数を呼び出します。 スクロール バーの横にある余分なコントロールを作成する上書きすることができます。

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

これらの関数は、動的分割ウィンドウのロジックを実装します。 高度な分割ロジックを提供するこれらをオーバーライドできます。

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView 機能

`CView`クラスに委任する高レベルの次のコマンドを使用して、`CSplitterWnd`実装します。 これらのコマンドは、仮想であるため、標準`CView`実装は、全体を必要としない`CSplitterWnd`にリンクされている実装。 使用するアプリケーションの`CView`なく`CSplitterWnd`、`CSplitterWnd`実装は、アプリケーションにリンクされません。

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   ID_NEXT_PANE または ID_PREV_PANE が現在可能かどうかを確認します。

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   「次のウィンドウ」または「前のペイン」コマンドを実行します。

- `virtual BOOL DoKeyboardSplit();`

   キーボード分割コマンドでは、通常は「ウィンドウ分割」を実行します。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
