---
title: 色のカスタマイズまたは変更 (アイコン用イメージ エディター)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560284"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>色のカスタマイズまたは変更 (アイコン用イメージ エディター)

**イメージ**エディターの[色パレット](../windows/colors-window-image-editor-for-icons.md)16 の標準色を最初に表示されます。 表示されている色は、独自のカスタム色を作成することもできます。 できます[を保存し、カスタマイズした色パレットを読み込む](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)します。

**カスタム カラー セレクター**  ダイアログ ボックスでは、イメージを使用する色をカスタマイズすることができます。 次のプロパティは次のとおりです。

|プロパティ|説明|
|---|---|
|**グラデーションの色の表示**|選択した色の値を変更します。 位置、十字線、色を変更します。 スライダーを上下の変更、明るさや色の RGB 値。|
|**光度バー**|選択した色の明るさを設定、**グラデーション色の表示**ボックス。 選択し、大きい明るさのバーの白い矢印をドラッグします。 または、以下の一覧。 **色**ボックスは、選択した色と設定する光度の効果が表示されます。|
|**色**|定義する色の色合い (色相値) を一覧表示します。 値の範囲は、0 から 240、0 が赤、60 は黄色、120 が緑、180 はシアン、200、マゼンタ、240 は青色です。|
|**Hue**|定義する色の色合い (色相値) を一覧表示します。 値の範囲は、0 から 240、0 が赤、60 は黄色、120 が緑、180 はシアン、200、マゼンタ、240 は青色です。|
|**Sat**|定義する色の鮮やかさの値を指定します。 鮮やかさは、指定された色合いの色の量です。 値の範囲は 0 ~ 240 です。|
|**明るさ**|定義する色の光度 (明るさ) の一覧を表示します。 値の範囲は 0 ~ 240 です。|
|**赤**|定義する色の赤の値を指定します。 値の範囲は 0 から 255 です。|
|**緑**|定義する色の緑の値を指定します。 値の範囲は 0 から 255 です。|
|**青**|定義する色の青の値を指定します。 値の範囲は 0 から 255 です。|

## <a name="to-change-colors-on-the-colors-palette"></a>色パレットで色を変更するには

1. **イメージ**] メニューの [選択**色の調整**します。

1. **カスタム カラー セレクター**  ダイアログ ボックスで、RGB または HSL 値を適切なテキスト ボックスに入力して、色を定義するかで使用する色の選択、**グラデーション色の表示**ボックス。

1. スライダーを移動して、輝度を設定、**光度**バー。

1. 作成した色の多くは、ディザリングされます。 ダブルクリックして、単色をディザリングされた色に最も近いする場合、**色**ボックス。

   後で、ディザリングされた色をする場合、スライダーを移動、**光度**バーまたは十字カーソルを移動、**グラデーション色の表示**ボックスに、ディザリングを復元します。

1. 選択**OK**新しい色を追加します。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[カラーを使用します。](../windows/working-with-color-image-editor-for-icons.md)<br/>
[[イメージ] メニュー](../windows/image-menu-image-editor-for-icons.md)<br/>
[[色] ウィンドウ](../windows/colors-window-image-editor-for-icons.md)