---
title: '方法: アイコンまたはその他のイメージを作成する'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 2605644533d55527a07904ac89fa937db1b2eec5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513752"
---
# <a name="how-to-create-an-icon-or-other-image"></a>方法: アイコンまたはその他のイメージを作成する

新しいイメージ、ビットマップ、アイコン、カーソル、またはツールバーを作成し、**イメージエディター**を使用してその外観をカスタマイズできます。 また、[リソーステンプレート](../windows/how-to-use-resource-templates.md)の後に新しいビットマップを作成することもできます。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>アイコンとカーソル:ディスプレイデバイスのイメージリソース

アイコンとカーソルは、グラフィカルなリソースで、表示デバイスの種類ごとに異なるサイズや色スキームの複数のイメージを含めることができます。 カーソルには、その位置を追跡するためにウィンドウで使用されるホットスポットもあります。 アイコンとカーソルはどちらも、ビットマップやその他のイメージと同様に、**イメージエディター**を使用して作成および編集されます。

新しいアイコンまたはカーソルを作成すると、**イメージエディター**はまず、標準の種類のイメージを作成します。 イメージは最初、画面の色 (透明) で塗られます。 画像がカーソルの場合、ホットスポットは最初に座標`0,0`を持つ左上隅にあります。

既定では、**イメージエディター**は、次の表に示すデバイス用の追加イメージの作成をサポートしています。 [**カスタムイメージ**] ダイアログボックスに幅、高さ、および色の数のパラメーターを入力して、他のデバイス用のイメージを作成できます。

|色|幅 (ピクセル単位)|高さ (ピクセル単位)|
|-----------|----------------------|-----------------------|
|白黒|16|16|
|白黒|32|32|
|白黒|48|48|
|白黒|64|64|
|白黒|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>デバイスイメージ (アイコンまたはカーソル) を作成する

新しいアイコンまたはカーソルリソースを作成すると、**イメージエディター**はまず、特定のスタイル (32 ×32、32 32 アイコンに16色、カーソルの場合はモノクロ) でイメージを作成します。 これにより、さまざまなサイズやスタイルのイメージを初期アイコンまたはカーソルに追加し、必要に応じて、各ディスプレイデバイスの追加イメージを編集できます。 また、既存のイメージの種類から、またはグラフィックスプログラムで作成されたビットマップから、切り取りと貼り付け操作を使用してイメージを編集することもできます。

[イメージエディター](../windows/image-editor-for-icons.md)でアイコンまたはカーソルリソースを開くと、現在のディスプレイデバイスに最も近いイメージが既定で開かれます。

> [!NOTE]
> プロジェクトに .rc ファイルがまだ含まれていない場合は、「[新しいリソーススクリプトファイルの作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

[**新しい&lt;デバイス&gt;イメージの種類**] ダイアログボックスでは、指定した種類の新しいデバイスイメージを作成できます。 [**新しい\<デバイス > イメージ**] ダイアログボックスを開くには、メニュー**イメージ** > の [**新しいイメージの種類**] を選択します。 次のプロパティが含まれているのは、**ターゲットイメージの種類**と**カスタム**です。

[**ターゲットイメージの種類**] プロパティには、表示するイメージの種類を選択できるイメージの種類が表示されます。

||||
|-|-|-|
|-16 x 16、16色|-48 x 48、16色|-96 x 96、16色|
|-16 x 16、256色|-48 x 48、256色|-96 x 96、256色|
|-16 x 16、モノクロ|-48 x 48、モノクロ|-96 x 96、モノクロ|
|-32 x 32、16色|-64 x 64、16色||
|-32 x 32、256色|-64 x 64、256色||
|-32 x 32、モノクロ|-64 x 64、モノクロ||

> [!NOTE]
> 既存のイメージは、この一覧に表示されません。

カスタムプロパティを使用すると、[**カスタムイメージ**] ダイアログボックスが開き、カスタムのサイズと色の数を指定して新しいイメージを作成できます。

[**カスタムイメージ**] ダイアログボックスを使用すると、カスタムサイズと色の数を指定して新しいイメージを作成できます。 次のプロパティが含まれています。

|プロパティ|説明|
|---|---|
|**Width**|カスタムイメージの幅をピクセル単位で入力するための領域を提供します (1-512、上限は 2048)。|
|**Height**|カスタムイメージの高さをピクセル単位で入力します (1-512、上限は 2048)。|
|**色**|カスタムイメージの色の数を選択する場所です。2、16、または256。|

[**デバイス&lt;を&gt;開く**] ダイアログボックスを使用すると、 C++プロジェクトのデバイスイメージを開くことができます。 現在のリソース (現在のリソースに含まれるイメージ) 内の既存のデバイスイメージが一覧表示されます。 次のプロパティが含まれています。

|プロパティ|説明|
|---|---|
|**現在のイメージ**|リソースに含まれているイメージを一覧表示します。 開くイメージの種類を選択します。|

#### <a name="to-create-a-new-icon-or-cursor"></a>新しいアイコンまたはカーソルを作成するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、 *.rc*ファイルを右クリックし、[リソースの**挿入**] を選択します。 既存のイメージリソースが既に *.rc*ファイル (カーソルなど) にある場合は、**カーソル**フォルダーを右クリックし、[**カーソルの挿入**] を選択します。

1. [[リソースの挿入] ダイアログボックス](../windows/add-resource-dialog-box.md)で、[**アイコン**] または [**カーソル**] を選択し、[**新規作成**] をクリックします。 アイコンの場合、この操作により、32×32、16色のアイコンを持つアイコンリソースが作成されます。 カーソルの場合は、32×32、モノクロ (2 色) のイメージが作成されます。

   [**リソースの挿入**] **+** ダイアログボックスで、イメージリソースの種類の横にプラス記号 () が表示されている場合は、ツールバーテンプレートが使用可能であることを意味します。 プラス記号を選択してテンプレートの一覧を展開し、テンプレートを選択して [**新規作成**] を選択します。

### <a name="to-add-an-image-for-a-different-display-device"></a>別のディスプレイデバイスのイメージを追加するには

1. [メニュー**イメージ** > ] [**新しいデバイスイメージ**] の順に選択するか、**イメージエディター**ペイン内を右クリックして [**新しいデバイスイメージ**] を選択します。

1. 追加するイメージの種類を選択します。 また、[**カスタム**] を選択して、既定の一覧で使用できないサイズのアイコンを作成することもできます。

### <a name="to-copy-a-device-image"></a>デバイスイメージをコピーするには

1. [メニュー**イメージ** > ] [**デバイスイメージを開く**] の順に選択し、[現在のイメージ] の一覧からイメージを選択します。 たとえば、アイコンの32×32、16色のバージョンを選択します。

1. 現在表示されているアイコンイメージをコピーします (**Ctrl**+**C**)。

1. 別の**イメージエディター**ウィンドウで、アイコンの別のイメージを開きます。 たとえば、アイコンの16×16、16色のバージョンを開きます。

1. アイコンイメージ (**Ctrl**+**V**) を1つの**イメージエディター**ウィンドウからもう一方のウィンドウに貼り付けます。 大きいサイズのサイズを小さいサイズに貼り付ける場合は、アイコンハンドルを使用して画像のサイズを変更できます。

### <a name="to-delete-a-device-image"></a>デバイスイメージを削除するには

アイコンイメージが**イメージエディター**に表示されている間に、[メニュー**イメージ** > ] [**デバイスイメージの削除**] にアクセスします。 リソース内の最後のアイコンのイメージを削除すると、リソースも削除されます。

> [!NOTE]
> **Del**キーを押すと、アイコン上に描画した画像と色は削除されますが、アイコンはそのままで、再設計できます。 誤って**del**キーを押した場合は、 **Ctrl**+**Z**キーを押して操作を元に戻します。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>デバイスイメージに透明または逆の領域を作成するには

[イメージエディター](../windows/image-editor-for-icons.md)では、最初のアイコンまたはカーソルのイメージに透過的な属性があります。 アイコンとカーソルの画像は四角形ですが、画像の一部が透明で、画面上の基になる画像がアイコンまたはカーソルを通じて表示されるため、多くは表示されません。 アイコンをドラッグすると、画像の一部が反転色で表示されることがあります。 この効果を作成するには、[[色] ウィンドウ](../windows/colors-window-image-editor-for-icons.md)で画面の色と反転色を設定します。

アイコンおよびカーソルに適用する画面と反転色は、派生イメージの形状と色を設定するか、逆の領域を割り当てます。 色は、これらの属性を持つイメージの一部を示します。 編集中に、画面の色と反転色の属性を表す色を変更できます。 これらの変更は、アプリケーション内のアイコンやカーソルの外観には影響しません。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、**ヘルプ**の説明と異なる場合があります。 設定を変更するには、[メニュー**ツール** > ] [**設定のインポートとエクスポート**] に移動します。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

#### <a name="to-create-transparent-or-inverse-regions"></a>透明または逆の領域を作成するには

1. [**色**] ウィンドウで、セレクター**画面の色**または**反転色**を選択します。

1. 描画ツールを使用して、画面または反転色をイメージに適用します。 描画ツールの詳細については、「[描画ツールの使用](using-a-drawing-tool-image-editor-for-icons.md)」を参照してください。

#### <a name="to-change-the-screen-or-inverse-color"></a>画面または反転色を変更するには

1. **画面カラー**セレクターまたは**反転色**セレクターを選択します。

1. [色] ウィンドウの [色パレット]から色を選択します。

   補完的な色は、他のセレクターに自動的に割り当てられます。

   > [!TIP]
   > **画面の色**または**反転色**のセレクターをダブルクリックすると、[[カスタムカラーセレクター] ダイアログボックス](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)が表示されます。

### <a name="use-the-256-color-palette"></a>256-カラーパレットを使用する

**イメージエディター**を使用すると、アイコンとカーソルをサイズ変更できます (64 × 64)。256カラーパレットを選択できます。 リソースを作成すると、デバイスイメージのスタイルが選択されます。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>256色のアイコンまたはカーソルを作成するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、 *.rc*ファイルを右クリックし、[リソースの**挿入**] を選択します。 既存のイメージリソースが既に *.rc*ファイル (カーソルなど) にある場合は、**カーソル**フォルダーを右クリックし、[**カーソルの挿入**] を選択します。

1. [[リソースの挿入] ダイアログボックス](../windows/add-resource-dialog-box.md)で、[**アイコン**] または [**カーソル**] を選択し、[**新規作成**] をクリックします。

1. メニュー**イメージ** > [**新しいデバイスイメージ**] にアクセスし、必要な256色のイメージスタイルを選択します。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>大きいアイコンの256カラーパレットから色を選択するには

256カラーパレットから選択して描画するには、[色[] ウィンドウ](../windows/colors-window-image-editor-for-icons.md)の [色]パレットから色を選択する必要があります。

1. 大きいアイコンまたはカーソルを選択するか、大きいアイコンまたはカーソルを新しく作成します。

1. [色] ウィンドウの [**色**] パレットに表示される 256色から色を選択します。

   選択した色は、[**色**] ウィンドウの [**色**パレット] の現在の色になります。

   > [!NOTE]
   > 256カラーのイメージに使用される最初のパレットは、 `CreateHalftonePalette` Windows API によって返されるパレットと一致します。 Windows シェル用のすべてのアイコンは、パレットの実現中にちらつきを防ぐために、このパレットを使用する必要があります。

### <a name="to-set-a-cursors-hot-spot"></a>カーソルのホットスポットを設定するには

カーソルのホットスポットは、カーソルの位置を追跡するときに Windows が参照するポイントです。 既定では、ホットスポットは、カーソルの左上隅に座標`0,0`付きで設定されます。 [プロパティウィンドウ](/visualstudio/ide/reference/properties-window)の**Hotspot**プロパティには、ホットスポット座標が表示されます。

1. [[イメージエディター] ツールバー](../windows/toolbar-image-editor-for-icons.md)で、[**ホットスポットの設定**] ツールを選択します。

1. カーソルのホットスポットとして割り当てるピクセルを選択します。

   [**プロパティ**] ウィンドウの [**ホットスポット**] プロパティに新しい座標が表示されます。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>ビットマップを作成して .gif または .jpeg として保存するには

ビットマップを作成すると、イメージはビットマップ形式 (.bmp) で作成されます。 ただし、画像は GIF または JPEG または他のグラフィック形式で保存できます。

> [!NOTE]
> このプロセスは、アイコンおよびカーソルには適用されません。

1. [メニュー**ファイル** > を**開く**] にアクセスし、[**ファイル**] を選択します。

1. [**新しいファイル] ダイアログボックス**で、  **C++ビジュアル**フォルダーを選択し、[**テンプレート**] ボックスで [**ビットマップファイル (.bmp)** ] を選択し、[**開く**] を選択します。

   **イメージエディター**にビットマップが表示されます。

1. 必要に応じて、新しいビットマップに変更を加えます。

1. **イメージエディター**でビットマップを開いたまま、[メニュー**ファイル** > ] [名前を**付けて .bmp を保存**] にアクセスします。

1. [ファイル名を**付けて保存**] ダイアログボックスで、ファイルの名前と拡張子を [**ファイル名**] ボックスに入力します。 たとえば、 *myfile.txt*のようになります。

   > [!NOTE]
   > 別のファイル形式で保存するには、プロジェクトの外部でビットマップを作成するか、開いておく必要があります。 プロジェクト内で作成または開く場合、[**名前を付けて保存**] コマンドは使用できません。 詳細については、「[プロジェクト外のリソーススクリプトファイル内のリソースの表示 (スタンドアロン)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)」を参照してください。

1. **[保存]** を選択します。

### <a name="to-convert-an-image-from-one-format-to-another"></a>画像をある形式から別の形式に変換するには

**イメージエディター**で GIF または JPEG イメージを開き、ビットマップとして保存できます。 また、ビットマップファイルを開いて、GIF または JPEG として保存することもできます。 作業するイメージは、開発環境で編集するためにプロジェクトの一部である必要はありません (「[スタンドアロンイメージの編集](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)」を参照してください)。

1. イメージ**エディター**でイメージを開きます。

1. メニュー**ファイル** > に名前を**付けて保存** します。

1. [名前を**付けてファイルを保存**] ダイアログボックスの [**ファイル名**] ボックスに、ファイル名と、必要な形式を示す拡張子を入力します。

1. **[保存]** を選択します。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>新しいイメージリソースをアンマネージC++プロジェクトに追加するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、 *.rc*ファイルを右クリックし、[リソースの**挿入**] を選択します。 既存のイメージリソースが既に *.rc*ファイルにある場合 (カーソルなど)、カーソルフォルダーを右クリックして [カーソルの**挿入**] を選択するだけです。

1. [[リソースの挿入] ダイアログボックス](../windows/add-resource-dialog-box.md)で、作成するイメージリソースの種類 (**ビットマップ**など) を選択し、[**新規**] を選択します。

   [**リソースの挿入**] **+** ダイアログボックスで、イメージリソースの種類の横にプラス記号 () が表示されている場合は、ツールバーテンプレートが使用可能であることを意味します。 プラス記号を選択してテンプレートの一覧を展開し、テンプレートを選択して [**新規作成**] を選択します。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>.NET プログラミング言語でプロジェクトに新しいイメージリソースを追加するには

1. **ソリューションエクスプローラー**で、プロジェクトフォルダー (たとえば、 *[windowsapplication1]* ) を右クリックします。

1. ショートカットメニューから [**追加**] を選択し、[**新しい項目の追加**] を選択します。

1. [**カテゴリ**] ペインで、[**ローカルプロジェクト項目**] フォルダーを展開し、[**リソース**] を選択します。

1. [**テンプレート**] ウィンドウで、プロジェクトに追加するリソースの種類を選択します。

   リソースが**ソリューションエクスプローラー**でプロジェクトに追加され、[イメージエディター](../windows/image-editor-for-icons.md)でリソースが開きます。 イメージ**エディター**で使用できるすべてのツールを使用して、イメージを変更できるようになりました。 マネージプロジェクトにイメージを追加する方法の詳細については、「[デザイン時の画像の読み込み](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)」を参照してください。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
[方法: 画像を編集する](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[方法: 描画ツールを使用する](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[方法: 色を調整する](../windows/working-with-color-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->