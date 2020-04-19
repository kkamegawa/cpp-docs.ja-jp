---
title: '方法: 色の調整'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
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
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: c424d2e613c51f901def13c4bf42a066797cc65c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387767"
---
# <a name="how-to-work-with-color"></a>方法: 色の調整

**イメージ エディター**具体的には、処理し、色をカスタマイズする多くの機能が含まれています。 前景色または背景色を設定する、境界付けられた領域を塗りつぶす色、または現在の前景色または背景色として使用するイメージの色を選択できます。 ツールを使用することができます、[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)のカラー パレットをと共に、**色**イメージを作成するウィンドウ。

モノクロと 16 色のイメージのすべての色に表示されます、**色**パレットで、**色**ウィンドウ。 標準の 16 色と共に独自のカスタム色を作成できます。 パレットの色を変更すると、イメージ内の対応する色がすぐに変更します。

256 色のアイコンやカーソルのイメージを使用する場合、**色**プロパティ、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)使用されます。 詳細については、次を参照してください。 [256 色のアイコンまたはカーソルの作成](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)です。

True-カラー イメージを作成することもできます。 完全なパレットに色のサンプルは表示されませんただし、**色**ウィンドウには、フォア グラウンドまたはバック グラウンドのカラー インジケーター領域にのみ出現します。 True の色を使用して作成、**カスタム カラー セレクター**  ダイアログ ボックス。

ディスク上のカスタマイズされたカラー パレットを保存し、必要に応じて再読み込みできます。 最も最近使用したカラー パレットがレジストリに保存し、次回 Visual Studio を起動したときを自動的に読み込まれます。

**色**ウィンドウが 2 つの部分。

- **色パレット**、使用できる色を表すカラー サンプルの配列です。 グラフィックス ツールを使用しているときに、前景色と背景色を選択するサンプルを選択できます。

- **カラー インジケーター**、前景色と背景の色と画面と反転色のセレクターを示しています。

   ![[色] ウィンドウ](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **色**ウィンドウ

> [!NOTE]
> **画面の色**と**反転色**ツールは、アイコンとカーソルの使用のみ。

使用することができます、**色**ウィンドウで、[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md)します。

- 表示する、**色** ウィンドウで右クリックして、**イメージ エディター**ウィンドウ選択 **[色] ウィンドウの表示**、メニューに移動または[イメージ](../windows/image-menu-image-editor-for-icons.md) > **[色] ウィンドウを表示する**します。

- 非表示にする、**色**ウィンドウで、(この操作により、自動的に隠すウィンドウ使用中でない場合)、ウィンドウのピン留めを外すかを選択、**閉じる**ボタンをクリックします。

**色**パレットは、標準の 16 色を最初に表示されます。 表示されている色は、独自のカスタム色を作成することもできます。 保存して、カスタマイズした色パレットを読み込むことができます。

**カスタム カラー セレクター**  ダイアログ ボックスでは、次のプロパティを使用してイメージを使用する色をカスタマイズすることができます。

|プロパティ|説明|
|--------------------------|--------------------------|
|**グラデーションの色の表示**|選択した色の値を変更します。<br/><br/>色を変更し、明るさや色の RGB 値を変更するスライダーを上下に移動するでは、十字線を配置します。|
|**光度バー**|選択した色の明るさを設定、**グラデーション色の表示**ボックス。<br/><br/>選択し、大きい明るさのバーの白い矢印をドラッグします。 または、以下の一覧。 **色**ボックスは、選択した色と設定する光度の効果が表示されます。|
|**色**|定義する色の色合い (色相値) を一覧表示します。 値の範囲は、0 から 240、0 が赤、60 は黄色、120 が緑、180 はシアン、200、マゼンタ、240 は青色です。|
|**Hue**|定義する色の色合い (色相値) を一覧表示します。 値の範囲は、0 から 240、0 が赤、60 は黄色、120 が緑、180 はシアン、200、マゼンタ、240 は青色です。|
|**Sat**|定義する色の鮮やかさの値を指定します。 鮮やかさは、指定された色合いの色の量です。 値の範囲は 0 ~ 240 です。|
|**明るさ**|定義する色の光度 (明るさ) の一覧を表示します。 値の範囲は 0 ~ 240 です。|
|**赤**|定義する色の赤の値を指定します。 値の範囲は 0 から 255 です。|
|**緑**|定義する色の緑の値を指定します。 値の範囲は 0 から 255 です。|
|**青**|定義する色の青の値を指定します。 値の範囲は 0 から 255 です。|

保存して読み込む、**色**パレットをカスタマイズした色が含まれています。 既定で、**色**Visual Studio を起動すると、最も最近使用したパレットが自動的に読み込まれます。

> [!TIP]
> 以降、**イメージ エディター**既定値を復元する手段を持たない**色**パレットで、既定値を保存する必要があります**色**パレットなどの名前で *"standard.pal"* または *"default.pal"* 既定の設定を簡単に復元できるようにします。

使用して、**読み込むパレットの色** ダイアログ ボックスを次のプロパティで C++ プロジェクトで使用する特殊なカラー パレットを読み込めません。

|プロパティ|説明|
|-----------------|-----------------|
|**ファイルの場所します。**|ファイルまたはフォルダーを検索する場所を指定します。<br/><br/>別の場所を選択するには、矢印を選択するか、レベルに移動 ツールバーでフォルダー アイコンを選択します。|
|**[ファイル名]**|開くファイルの名前を入力する場所を提供します。<br/><br/>以前開いたファイルをすばやく検索するには、使用可能な場合に、ボックスの一覧でファイル名を選択します。<br/><br/>ファイルを検索する場合は、ワイルドカードとしてアスタリスク (*) を使用できます。 たとえば、「 \*。\*すべてファイル一覧を表示します。 たとえば、ファイルの完全なパスを入力することもできます。 *C:\My Documents\MyColorPalette.pal*または *\\\NetworkServer\MyFolder\MyColorPalette.pal*します。|
|**ファイルの種類**|表示するファイルの種類を示します。<br/><br/>パレット (\*.pal) のカラー パレットの既定のファイルの種類します。|

## <a name="how-to"></a>方法

### <a name="to-select-foreground-or-background-colors"></a>前景色または背景色の選択

を除き、**消しゴム**、ツールを**イメージ エディター**それぞれ、左または右マウス ボタンを押したときに現在前景色または背景色で描画をツールバー。

- マウスの左ボタンで、前景色の色を選択するで使用色を選択します。、**色**パレット。

- 使用色を選択するとマウスの右ボタンの背景色、**色**パレット。

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>イメージの境界付けられた領域を塗りつぶすには

**イメージ エディター**提供、**入力**いずれかの情報を入力するためのツールは、現在の描画の色または現在の背景色とイメージの領域を囲みます。

### <a name="to-use-the-fill-tool"></a>塗りつぶしツールを使用するには

1. 使用して、**イメージ エディター**ツールバーまたはメニューに移動して**イメージ** > **ツール**を選択し、**入力**ツール。

1. 必要に応じて、色の描画を選択します。 [色パレット](../windows/colors-window-image-editor-for-icons.md)前景の色を選択するマウスの左ボタンまたは背景色を選択するマウスの右ボタンを選択します。

1. 移動、**塗りつぶし**ツールを格納する領域。

1. 前景色または背景色をそれぞれに入力を左または右マウス ボタンを選択します。

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>別の場所を使用する画像から色を取得するには

**色の選択**、または色 pickup、ツールを使用するイメージの色、現在前景色または背景色、左右のマウスの右ボタンを押すかどうかに応じて。 キャンセル、**色の選択**ツールで別のツールを選択します。

1. 使用して、**イメージ エディター**ツールバーまたはメニューに移動して**イメージ** > **ツール**を選択し、**色の選択**ツール。

1. イメージから選択する色を選択します。

   > [!NOTE]
   > 色を選択した後、**イメージ エディター**最も最近使用した復旧ツール。

1. マウスの左ボタンを使用して、前景色または背景色のマウスの右ボタンを描画します。

### <a name="to-choose-the-background"></a>背景を選択するには

移動またはイメージから選択範囲をコピーするときは、現在の背景色に一致するような選択範囲のピクセルは、既定で透過的なとターゲットの場所にピクセルを不明瞭です。

透明な背景 (既定値) から、不透明な背景に切り替えるし、再びことができます。 選択ツールを使用するときに、**透明な背景**と**不透明な背景**オプションに表示されます、**オプション**セレクター、**イメージ エディター**ツールバー。

![オプションをバック グラウンド&#45;非透過または透過](../windows/media/vcimageeditoropaqtranspback.gif "オプションをバック グラウンド&#45;非透過または透過")<br/>
**透過的かつ非透過オプション**上、**イメージ エディターのツールバー**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>透過的なと不透明な背景を切り替える

**イメージ エディター**ツールバーで、**オプション**セレクターで、適切な背景を選択します。

- **不透明な背景 (O)**:既存のイメージは、選択範囲のすべての部分によって隠されています。

- **透明な背景 (T)**:既存のイメージは、選択範囲の現在の背景色に一致する部分を示します。

> [!TIP]
> ショートカット、上、**イメージ** を選択またはクリア**描画の不透明な**します。

選択範囲が既にイメージのどの部分は透明を変更する有効なときに、背景色を変更できます。

### <a name="to-invert-the-colors-in-a-selection"></a>選択範囲の色を反転するには

**イメージ エディター**イメージは反転色で表示する方法がわかるように、イメージの選択した部分の色の反転する便利な手段を提供します。

メニューに現在選択されている色の反転、**イメージ** > **色の反転**します。

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>カスタマイズまたはカラー パレットに色を変更します。

1. メニューに移動して**イメージ** > **色の調整**します。

1. **カスタム カラー セレクター**  ダイアログ ボックスで、RGB または HSL 値を適切なテキスト ボックスに入力して、色を定義するかで使用する色の選択、**グラデーション色の表示**ボックス。

1. スライダーを移動して、輝度を設定、**光度**バー。

1. 作成した色の多くは、ディザリングされます。 ダブルクリックして、単色をディザリングされた色に最も近いする場合、**色**ボックス。

   後で、ディザリングされた色をする場合、スライダーを移動、**光度**バーまたは十字カーソルを移動、**グラデーション色の表示**ボックスに、ディザリングを復元します。

1. 選択**OK**新しい色を追加します。

### <a name="to-save-a-custom-colors-palette"></a>カスタム カラー パレットを保存するには

1. メニューに移動して**イメージ** > **パレットの保存**します。

1. パレットを保存するディレクトリに移動し、パレット名を入力します。

1. **[保存]** を選択します。

### <a name="to-load-a-custom-colors-palette"></a>カスタム カラー パレットを読み込むには

1. メニューに移動して**イメージ** > **パレットの読み込み**します。

1. **カラー パレットの読み込み** ダイアログ ボックス、適切なディレクトリに移動し、読み込むパレットを選択します。 **色**パレットは、拡張子 .pal と共に保存されます。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
[方法: アイコンまたはその他の画像を作成する](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[方法: 画像を編集する](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[方法: 描画ツールを使用する](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
