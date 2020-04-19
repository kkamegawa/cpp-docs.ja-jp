---
title: アクセラレータ キー (アイコン用イメージ エディターを C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 45afdf4b3b557b560d7597b1bb4330c36a1fc84d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204811"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>アクセラレータ キー (アイコン用イメージ エディターを C++)

既定では、キーにバインドされているイメージ エディターのコマンドをアクセラレータ キーを以下に示します。 アクセラレータ キーを変更するには、メニューに移動**ツール** > **オプション**選択**キーボード**下、**環境**フォルダー。 詳細については、「[Visual Studio でのキーボード ショートカットの識別とカスタマイズ](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)」をご覧ください。

> [!NOTE]
> 使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 設定を変更するには、メニューに移動**ツール** > **インポートおよびエクスポート設定**します。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

|コマンド|キー|説明|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl**  +  **A**|選択したサイズと色のエアブラシを使用して描画します。|
|Image.BrushTool|**Ctrl キーを押し** + **B**|選択した図形、サイズ、色とブラシを使用して描画します。|
|Image.CopyAndOutlineSelection|**Ctrl キーを押し** + **Shift** + **U**|現在の選択領域のコピーを作成し、その外枠を描画します。 背景色が、現在の選択範囲に含まれている、ことが含まれる場合がある[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)選択します。|
|Image.DrawOpaque|**Ctrl**  +  **J**|現在の選択範囲をいずれかにより、[非透過または透過](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)します。|
|Image.EllipseTool|**Ctrl**  +  **P**|選択した線の幅と色を使用して楕円を描画します。|
|Image.EraserTool|**Ctrl**  +  **Shift**  +  **I**|(現在の背景色) のイメージの一部を消去します。|
|Image.FilledEllipseTool|**Ctrl キーを押し** + **Shift** + **Alt** + **P**|塗りつぶされた楕円を描画します。|
|Image.FilledRectangleTool|**Ctrl キーを押し** + **Shift** + **Alt** + **R**|塗りつぶされた四角形を描画します。|
|Image.FilledRoundRectangleTool|**Ctrl キーを押し** + **Shift** + **Alt** + **W**|塗りつぶされた角の丸い四角形を描画します。|
|Image.FillTool|**Ctrl**  +  **F**|領域を塗りつぶします。|
|Image.FlipHorizontal|**Ctrl**  +  **H**|イメージまたは選択領域の上下を反転させます。|
|Image.FlipVertical|**Shift キーを押し**+ **Alt** + **H**|イメージまたは選択領域の左右を反転させます。|
|Image.LargerBrush|**Ctrl キー** + **=**|ブラシのサイズを各方向に 1 ピクセルずつ拡大します。 ブラシのサイズを小さくする方法については、この表の「Image.SmallerBrush」を参照してください。|
|Image.LineTool|**Ctrl**  +  **L**|選択した形、サイズ、および色で直線を描画します。|
|Image.MagnificationTool|**Ctrl キーを押し** + **M**|アクティブ化、**拡大**ツールで、イメージの特定のセクションを拡大することができます。|
|Image.Magnify|**Ctrl**  +  **Shift**  +  **M**|現在の拡大率と 1:1 の間で切り替えます。|
|Image.NewImageType|**[挿入]**|起動、[新規\<デバイス > イメージの種類 ダイアログ ボックス](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)で別のイメージ タイプのイメージを作成できます。|
|Image.NextColor|**Ctrl**  +  **]**<br /><br /> または<br /><br /> **Ctrl キーを押し** + **右向き矢印**|描画の前景色を次のパレット カラーに変更します。|
|Image.NextRightColor|**Ctrl**  +  **Shift**  +  **]**<br /><br /> または<br /><br /> **Shift キーを押し** + **Ctrl** + **右向き矢印**|描画の背景色を次のパレット カラーに変更します。|
|Image.OutlinedEllipseTool|**Shift キーを押し** + **Alt** + **P**|塗りつぶされた楕円を外枠付きで描画します。|
|Image.OutlinedRectangleTool|**Shift キーを押し** + **Alt** + **R**|塗りつぶされた四角形を外枠付きで描画します。|
|Image.OutlinedRoundRectangleTool|**Shift キーを押し** + **Alt** + **W**|塗りつぶされた角の丸い四角形を外枠付きで描画します。|
|Image.PencilTool|**Ctrl**  +  **I**|1 ピクセルのペンシルを使用して描画します。|
|Image.PreviousColor|**Ctrl**  +  **[**<br /><br /> または<br /><br /> **Ctrl キーを押し** + **左向き矢印**|描画の前景色を前のパレット カラーに変更します。|
|Image.PreviousRightColor|**Ctrl**  +  **Shift**  +  **[**<br /><br /> または<br /><br /> **Shift キーを押し** + **Ctrl** + **左向き矢印**|描画の背景色を前のパレット カラーに変更します。|
|Image.RectangleSelectionTool|**Shift キーを押し** + **Alt** + **S**|移動、コピー、または編集するイメージの四角形の部分を選択します。|
|Image.RectangleTool|ATL + R|選択した線の幅と色で四角形を描画します。|
|Image.Rotate90Degrees|**Ctrl**  +  **Shift**  +  **H**|イメージまたは選択領域を 90 度回転させます。|
|Image.RoundedRectangleTool|**Alt** + **W**|選択した線の幅と色で丸い四角形を描画します。|
|Image.ShowGrid|**Ctrl キーを押し** + **Alt** + **S**|ピクセル グリッドを切り替えます (オンまたはオフ、**ピクセル グリッド**オプション、[グリッドの設定 ダイアログ ボックス](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|
|Image.ShowTileGrid|**Ctrl キーを押し** + **Shift** + **Alt** + **S**|タイル グリッドを切り替えます (オンまたはオフ、**タイル グリッド**オプション、[グリッドの設定 ダイアログ ボックス](../windows/grid-settings-dialog-box-image-editor-for-icons.md))。|
|Image.SmallBrush|**Ctrl** + **.** (ピリオド)|削減、**ブラシ**サイズを 1 ピクセルです。 この表の「Image.LargerBrush」と「Image.SmallerBrush」も参照してください。|
|Image.SmallerBrush|**Ctrl キーを押し** +  **-** (負符号)|ブラシのサイズを各方向に 1 ピクセルずつ縮小します。 ブラシを元のサイズに戻す方法については、この表の「Image.LargerBrush」を参照してください。|
|Image.TextTool|**Ctrl**  +  **T**|開く、[テキスト ツール ダイアログ ボックス](../windows/text-tool-dialog-box-image-editor-for-icons.md)します。|
|Image.UseSelectionAsBrush|**Ctrl キーを押し** + **U**|現在の選択項目をブラシとして使用して描画します。|
|Image.ZoomIn|**Ctrl キーを押し** + **Shift** + **します。** (ピリオド)<br /><br /> または<br /><br /> **Ctrl キーを押し** + **上向きの矢印**|現在のビューの拡大率を上げます。|
|Image.ZoomOut|**Ctrl キーを押し** + **、** (コンマ)<br /><br /> または<br /><br /> **Ctrl キーを押し** + **下矢印をクリック**|現在のビューの拡大率を下げます。|

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
[方法: アイコンまたはその他の画像を作成する](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[方法: 画像を編集する](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[方法: 描画ツールを使用する](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[方法: 色を調整する](../windows/working-with-color-image-editor-for-icons.md)<br/>