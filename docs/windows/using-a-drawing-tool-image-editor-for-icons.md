---
title: '方法: 描画ツールを使用して、'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: 7b362749c9a5cb1c7ec77e5cac8625aa7eb260f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387839"
---
# <a name="how-to-use-a-drawing-tool"></a>方法: 描画ツールを使用して、

**イメージ エディター**フリーハンドでの描画と消去のツールがすべて同じ方法で機能します。 ツールを選択して、必要に応じて、[前景色と背景色を選択します。](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)とサイズおよび図形オプション。 イメージにポインターを移動し、クリックしてまたはドラッグした描画、消去します。

## <a name="drawing-tools"></a>描画ツール

いずれかの描画ツールを選択することができます、**イメージ エディター**ツールバーまたは**イメージ**メニュー。 選択すると、**消しゴム**ツール、**ブラシ**ツール、または**エアブラシ**ツール オプション セレクターがそのツールのオプションが表示されます。

> [!TIP]
>  上のボタンの上にカーソルを置くと、ツール ヒントが表示されます、[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)します。 これらのヒントを使用すると、ここで説明する特定のボタンを識別できます。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>選択して、イメージ エディターのツールバーから描画ツールを使用するには

1. ボタンを選択、**イメージ エディター**ツールバー。

   - **消しゴム**ツール、マウスの左ボタンを押すと現在の背景色とイメージを描画します。

      > [!TIP]
      > 使用する代わりに、**消しゴム**ツール、かもしれません描画ツールのいずれかの背景色で描画する方が便利です。

   - **鉛筆**ツールが 1 つのピクセルの固定幅でフリーハンドを描画します。

   - **ブラシ**ツールにはさまざまな形態とサイズ。

   - **エアブラシ**ツールは、ブラシの中心の色ピクセルをランダムに分散させます。

1. 必要に応じて、色とブラシを選択します。

   - [色パレット](../windows/colors-window-image-editor-for-icons.md)前景の色を選択するマウスの左ボタンまたは背景色を選択するマウスの右ボタンを選択します。

   - [オプション セレクター](../windows/toolbar-image-editor-for-icons.md)、使用するブラシを表す図形を選択します。

1. 描画を開始するイメージまたは描画上の場所をポイントします。 ポインターは、選択したツールに応じて図形を変更します。

1. (の前景色) マウスの左ボタンまたは (の背景色) で、マウスの右ボタンを押して、押したままにする描画します。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>選択し、[イメージ] メニューから描画ツールを使用するには

1. メニューに移動して**イメージ** > **ツール**します。

1. カスケード型のサブメニューを使用するツールを選択します。

## <a name="lines-or-closed-figures"></a>線または閉じた図形

**イメージ エディター**と同じ方法で作業できる線と閉じた図形を描画するためのツール: 1 つのポイントにカーソルを配置し、別にドラッグします。 線、これらのポイントは、エンドポイントが。 閉じた図形は、これらのポイントは、図を囲む四角形の反対側の角です。

現在のブラシの選択によって決定幅で線が描画され、枠付きの図形が幅の現在の選択範囲によって決まります幅で描画されます。 マウスの右ボタンを押した場合、行およびとフレームの両方でいっぱいになったすべての図形が現在の前景の色をマウスの左ボタンを押した場合のまたは現在の背景色でを描画します。

### <a name="to-draw-a-line"></a>線を描画するには

1. 使用して、[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)  メニューに移動または**イメージ**> **ツール**を選択し、**行**ツール。

1. 必要に応じて、色とブラシを選択します。

   - [色パレット](../windows/colors-window-image-editor-for-icons.md)前景の色を選択するマウスの左ボタンまたは背景色を選択するマウスの右ボタンを選択します。

   - [オプション セレクター](../windows/toolbar-image-editor-for-icons.md)、使用するブラシを表す図形を選択します。

1. 線の開始位置にポインターを置きます。

1. 線の終点をドラッグします。

### <a name="to-draw-a-closed-figure"></a>閉じた図を描画するには

1. 使用して、**イメージ エディター**ツールバーまたはメニューに移動して**イメージ** > **ツール**を選択し、**図形**ツール。

   **図形**ツールは、各ボタンに記載のとおりに図形を作成します。

1. 必要に応じて、色と線の幅を選択します。

1. 図を描画する四角形の領域の 1 つ上の隅にポインターを移動します。

1. 対角にポインターをドラッグします。

## <a name="custom-brushes"></a>カスタム ブラシ

カスタム ブラシは四角形の部分を取得しのいずれかのように使用するイメージの**イメージ エディター**の既製のブラシ。 選択範囲に対して実行できるすべての操作、カスタム ブラシも実行できます。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>イメージの一部からカスタム ブラシを作成するには

1. ブラシに使用するイメージの一部を選択します。

1. 保持、 **Shift**キー、選択範囲の選択し、イメージをドラッグまたはメニューに移動**イメージ** > **ブラシとして使用して選択**します。

   選択内容では、画像の選択範囲の色を分散するカスタム ブラシになります。 ドラッグするパスに沿った選択範囲のコピーが残されます。 緩やかに変化をドラッグする、複数のコピーを作成します。

   > [!NOTE]
   > 選択すると、**選択範囲をブラシとして使用**をブラシとして全体のイメージを使用するイメージの一部をまず選択なし。 カスタム ブラシを使用しての結果は選択したかどうかに依存しても、[透明または不透明な背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)します。

現在の背景色に一致するカスタム ブラシのピクセルが透明な通常: 既存のイメージをペイントがありません。 背景色のピクセルが既存のイメージを描画できるように、この動作を変更できます。

スタンプまたはステンシルなどのカスタム ブラシを使用すると、さまざまな特殊効果を作成します。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>背景色でカスタム ブラシの形状を描画するには

1. 非透過または透過の背景を選択します。

1. 背景色を描画する色に設定します。

1. 描画する位置にカスタム ブラシ。

1. マウスの右ボタンを選択します。 カスタム ブラシの不透明な領域は、背景色で描画されます。

### <a name="to-double-or-halve-the-custom-brush-size"></a>ダブルクリックまたはカスタム ブラシのサイズの半分

キーを押して、**プラス**(**+**) ブラシのサイズを 2 倍にキーまたは**マイナス記号**(**-**) キーが半分にする.

### <a name="to-cancel-the-custom-brush"></a>カスタム ブラシをキャンセルするには

キーを押して**Esc**または別の描画ツールを選択します。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
[方法: アイコンまたはその他の画像を作成する](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[方法: 画像を編集する](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[方法: 色を調整する](../windows/working-with-color-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>