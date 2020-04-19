---
title: 描画コードの変更 (ATL チュートリアル、パート 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: df89837e8f453443dc092a1b96e9c3f395fa2353
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127381"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>描画コードの変更 (ATL チュートリアル、パート 4)

既定では、コントロールの描画コードに四角形とテキスト**polyctl.htm**が表示されます。 この手順では、さらに興味深いものを表示するようにコードを変更します。 次のタスクが関係します。

- ヘッダーファイルの変更

- `OnDraw` 関数の変更

- 多角形のポイントを計算するメソッドの追加

- 塗りつぶしの色を初期化しています

## <a name="modifying-the-header-file"></a>ヘッダーファイルの変更

まず、数値演算関数 `sin` と `cos`のサポートを追加します。これは、多角形のポイントの計算と、位置を格納する配列の作成に使用されます。

### <a name="to-modify-the-header-file"></a>ヘッダーファイルを変更するには

1. Polyctl.htm の先頭に `#include <math.h>` 行を追加します。 ファイルの先頭は次のようになります。

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Polyctl.htm に次のコードを追加して、コントロールのメソッド情報を提供する `IProvideClassInfo` インターフェイスを実装します。 `CPolyCtl` クラスで、次の行を置き換えます。

    ```cpp
    public CComControl<CPolyCtl>
    ```

    with

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    `BEGIN_COM_MAP(CPolyCtl)`で、次の行を追加します。

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. 多角形の点を計算した後は `POINT`型の配列に格納されます。そのため、Polyctl.htm の定義ステートメント `short m_nSides;` の後に配列を追加します。

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>OnDraw メソッドの変更

ここで、Polyctl.htm の `OnDraw` メソッドを変更する必要があります。 追加するコードでは、多角形を描画するために使用する新しいペンとブラシを作成し、`Ellipse` を呼び出して、実際の描画を実行するための Win32 API 関数を `Polygon` します。

### <a name="to-modify-the-ondraw-function"></a>OnDraw 関数を変更するには

1. Polyctl.htm の既存の `OnDraw` メソッドを次のコードに置き換えます。

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>多角形のポイントを計算するメソッドの追加

多角形の境界を構成する点の座標を計算する、`CalcPoints`と呼ばれるメソッドを追加します。 これらの計算は、関数に渡される RECT 変数に基づいて行われます。

### <a name="to-add-the-calcpoints-method"></a>CalcPoints メソッドを追加するには

1. Polyctl.htm の `CPolyCtl` クラスの `IPolyCtl` パブリックセクションに `CalcPoints` の宣言を追加します。

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    `CPolyCtl` クラスのパブリックセクションの最後の部分は次のようになります。

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. この `CalcPoints` 関数の実装を Polyctl.htm の末尾に追加します。

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>塗りつぶしの色を初期化しています

既定の色を使用して `m_clrFillColor` を初期化します。

### <a name="to-initialize-the-fill-color"></a>塗りつぶしの色を初期化するには

1. Polyctl.htm の `CPolyCtl` コンストラクターに次の行を追加して、既定の色として green を使用します。

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

コンストラクターは次のようになります。

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>コントロールのビルドとテスト

コントロールをリビルドします。 Polyctl.htm ファイルが開いている場合は閉じていることを確認し、[**ビルド**] メニューの [**多角形のビルド**] をクリックします。 Polyctl.htm ページからもう一度コントロールを表示できますが、今度は ActiveX コントロールテストコンテナーを使用します。

### <a name="to-use-the-activex-control-test-container"></a>ActiveX コントロールテストコンテナーを使用するには

1. ActiveX コントロールテストコンテナーをビルドして開始します。 [TSTCON サンプル: ActiveX コントロールテストコンテナー](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon)は GitHub にあります。

    > [!NOTE]
    > `ATL::CW2AEX`関連のエラーについては、スクリプト .Cpp で、行 `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` を `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`に、行 `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` を `TRACE( "Source Text: %s\n", bstrSourceLineText );`に置き換えます。<br/>
    > `HMONITOR`関連のエラーについては、`TCProps` プロジェクトで Stdafx.h を開き、次のように置き換えます。
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    > with
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. **テストコンテナー**で、[**編集**] メニューの [**新しいコントロールの挿入**] をクリックします。

1. `PolyCtl class`という名前のコントロールを見つけて、[ **OK]** をクリックします。 丸の中に緑色の三角形が表示されます。

次の手順に従って、辺の数を変更してみてください。 **テストコンテナー**内からデュアルインターフェイスのプロパティを変更するには、 **Invoke メソッド**を使用します。

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>テストコンテナー内からコントロールのプロパティを変更するには

1. [**テストコンテナー**] で、[**コントロール**] メニューの [**メソッドの呼び出し**] をクリックします。

    [**メソッドの呼び出し**] ダイアログボックスが表示されます。

1. [**メソッド名**] ボックスの一覧から、[ **PropPut** version of the**両辺**] プロパティを選択します。

1. [**パラメーター値**] ボックスに「`5`」と入力し、[**値の設定**] をクリックして、[**呼び出し**] をクリックします。

コントロールは変更されないことに注意してください。 `m_nSides` 変数を設定して内部の辺の数を変更しても、コントロールは再描画されませんでした。 別のアプリケーションに切り替えてから**テストコンテナー**に戻すと、コントロールが再描画され、正しい数の辺があることがわかります。

この問題を解決するには、辺の数を設定した後、`IViewObjectExImpl`で定義されている `FireViewChange` 関数の呼び出しを追加します。 コントロールが独自のウィンドウで実行されている場合、`FireViewChange` は `InvalidateRect` メソッドを直接呼び出します。 コントロールがウィンドウなしで実行されている場合は、コンテナーのサイトインターフェイスで `InvalidateRect` メソッドが呼び出されます。 これにより、コントロール自体が強制的に再描画されます。

### <a name="to-add-a-call-to-fireviewchange"></a>FireViewChange への呼び出しを追加するには

1. `FireViewChange` の呼び出しを `put_Sides` メソッドに追加して、Polyctl.htm を更新します。 完了すると、`put_Sides` メソッドは次のようになります。

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

`FireViewChange`を追加した後、ActiveX コントロールテストコンテナーでもう一度コントロールをリビルドして、もう一度試してみてください。 今度は、辺の数を変更して [`Invoke`] をクリックすると、コントロールが直ちに変更されます。

次の手順では、イベントを追加します。

手順[3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [. に](../atl/adding-an-event-atl-tutorial-part-5.md)戻ります。

## <a name="see-also"></a>参照

[チュートリアル](../atl/active-template-library-atl-tutorial.md)<br/>
[テスト コンテナーでのプロパティとイベントのテスト](../mfc/testing-properties-and-events-with-test-container.md)
