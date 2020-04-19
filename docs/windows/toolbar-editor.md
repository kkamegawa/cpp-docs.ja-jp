---
title: ツールバーエディターC++()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69514694"
---
# <a name="toolbar-editor-c"></a>ツールバーエディターC++()

ツール**バーエディター**を使用すると、ツールバーリソースを作成し、ビットマップをツールバーリソースに変換できます。 **ツールバーエディター**は、グラフィカルな表示を使用して、完成したアプリケーションでの表示方法によく似たツールバーとボタンを表示します。

**ツールバーエディター**ウィンドウには、ボタンイメージの2つのビューが表示されます。これは**イメージエディター**ウィンドウと同じです。 分割バーは2つのペインを分割し、分割バーを左右にドラッグして、ペインの相対的なサイズを変更できます。 アクティブなペインには、選択境界線が表示されます。イメージの2つのビューの上には、[サブジェクト] ツールバーが表示されます。

![ツールバーエディター](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**ツール バー エディター**

**ツールバーエディター**は、**イメージエディター**の機能に似ており、メニュー項目、グラフィックツール、およびビットマップグリッドは同じです。 **[イメージ]** メニューには、**ツールバーエディター**と**イメージエディター**を切り替えるためのメニューコマンドがあります。 **グラフィックス**ツールバー、**カラー**パレット、または**イメージ**メニューの使用の詳細については、「[イメージエディター](../windows/image-editor-for-icons.md)」を参照してください。

ビットマップを変換することによってC++ 、新しいツールバーをプロジェクトに作成できます。 ビットマップのグラフィックは、ツールバーのボタンイメージに変換されます。 通常、ビットマップには、ボタンごとに1つのイメージがある1つのビットマップに複数のボタンイメージが含まれています。 イメージのサイズは、既定の幅が16ピクセル、イメージの高さになります。 **イメージエディター**で **[イメージ]** メニューの **[ツールバーエディター]** をクリックすると、 **[新しいツールバーリソース]** ダイアログボックスでボタンイメージのサイズを指定できます。

**[新しいツールバーリソース]** ダイアログボックスでは、 C++プロジェクトのツールバーリソースに追加するボタンの幅と高さを指定できます。 既定値は16×15ピクセルです。

ツールバーの作成に使用されるビットマップの最大幅は2048であるため、**ボタンの幅**を*512*に設定した場合は、ボタンを4つしか使用できません。 幅を*513*に設定した場合は、3つのボタンのみを使用できます。

**[新しいツールバーリソース]** ダイアログボックスには、次のプロパティがあります。

|プロパティ|説明|
|---|---------------|
|**ボタンの幅**|ビットマップリソースからツールバーリソースに変換するツールバーボタンの幅を入力する場所です。|
|**ボタンの高さ**|ビットマップリソースからツールバーリソースに変換するツールバーボタンの高さを入力する場所です。|

> [!NOTE]
> 画像は、指定された幅と高さにトリミングされ、色は標準のツールバーの色 (16 色) を使用するように調整されます。

既定では、新規または空白のボタンがツールバーの右端に表示されます。 このボタンは、編集する前に移動できます。 新しいボタンを作成すると、編集したボタンの右側に別の空白のボタンが表示されます。 ツールバーを保存しても、空白のボタンは保存されません。

ツールバーのボタンには、次のプロパティがあります。

|プロパティ|説明|
|--------------|-----------------|
|**ID**|ボタンの ID を定義します。 ドロップダウンリストには、共通の**ID**名が表示されます。|
|**Width**|ボタンの幅を設定します。 16ピクセルをお勧めします。|
|**Height**|ボタンの高さを設定します。 1つのボタンの高さによって、ツールバーのすべてのボタンの高さが変わります。 15ピクセルをお勧めします。|
|**プロンプト**|ステータスバーに表示されるメッセージを定義します。 追加 *\n* 名を追加し、**ツールヒント**ツールバーのボタンを。 詳細については、「[ツールヒントの作成](../windows/creating-a-tool-tip-for-a-toolbar-button.md)」を参照してください。|

**幅**と**高さ**はすべてのボタンに適用されます。 ツールバーの作成に使用されるビットマップの最大幅は2048です。そのため、ボタンの幅を*512*に設定した場合は、4つのボタンしか使用できません。また、幅を*513*に設定すると、3つのボタンのみを使用できます。

## <a name="how-to"></a>方法

**ツールバーエディター**では、次のことが可能です。

### <a name="to-create-new-toolbars"></a>新しいツールバーを作成するには

1. **リソースビュー**で、 *.rc*ファイルを右クリックし、 **[リソースの追加]** を選択します。 *.Rc*ファイルに既存のツールバーがある場合は、**ツールバー**フォルダーを右クリックして **[ツールバーの挿入]** を選択できます。

1. **[リソースの追加]** ダイアログボックスで、 **[リソースの種類]** ボックスの一覧の **[ツールバー]** を選択し、 **[新規作成]** を選択します。

   **ツールバー**のリソースの種類の横にプラス記号 ( **+** ) が表示されている場合は、ツールバーテンプレートが使用可能であることを意味します。 プラス記号を選択してテンプレートの一覧を展開し、テンプレートを選択して **[新規作成]** を選択します。

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>ビットマップをツールバーリソースに変換するには

1. [イメージエディター](../windows/image-editor-for-icons.md)で既存のビットマップリソースを開きます。 ビットマップが *.rc*ファイル内に存在しない場合は、 *.rc*ファイルを右クリックし、 **[インポート]** をクリックし*ます。* 次に、.rc ファイルに追加するビットマップに移動し、 **[開く]** を選択します。

1. メニュー**イメージ** > **ツールバーエディター**にジャンプします。

   **[新しいツールバーリソース]** ダイアログボックスが表示されます。 アイコンイメージの幅と高さは、ビットマップに合わせて変更できます。 ツールバーのイメージが**ツールバーエディター**に表示されます。

1. 変換を完了するには、[プロパティウィンドウ](/visualstudio/ide/reference/properties-window)を使用して、ボタンのコマンド**ID**を変更します。 新しい*id*を入力するか、ドロップダウンリストから**id**を選択します。

   > [!TIP]
   > **プロパティ** ウィンドウには、タイトルバーに 画鋲 ボタンがあり、これを選択すると、ウィンドウの**自動的に隠す**が有効または無効になります。 個々のプロパティウィンドウを再度開くことなく、すべてのツールバーボタンのプロパティを切り替えるには、 **[プロパティ]** ウィンドウが静止したままになるように**自動的に隠す**オフにします。

   [プロパティウィンドウ](/visualstudio/ide/reference/properties-window)を使用して、新しいツールバーのボタンのコマンド id を変更することもできます。

### <a name="to-manage-toolbar-buttons"></a>ツールバーのボタンを管理するには

#### <a name="to-create-a-new-toolbar-button"></a>ツールバーの新しいボタンを作成するには

1. で、リソースフォルダー (たとえば、 *Project1. rc*) を展開[リソースビュー](how-to-create-a-resource-script-file.md#create-resources)ます。

1. **ツールバー**のフォルダーを展開し、編集するツールバーを選択して、次のいずれかの操作を行います。

   - ツールバーの右端にある空白のボタンに ID を割り当てます。 これを行うには、[[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で**ID**プロパティを編集します。 たとえば、メニューオプションと同じ ID をツールバーボタンに付けることができます。 この場合は、ドロップダウンリストボックスを使用して、メニューオプションの**ID**を選択します。

   - ツールバー**ビュー**ペインのツールバーの右端にある空白のボタンを選択し、描画を開始します。 既定のボタンコマンド ID が割り当てられています (ID_BUTTON\<n >)。

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>ボタンとして画像をツールバーに追加するには

1. [リソースビュー](how-to-create-a-resource-script-file.md#create-resources)で、ツールバーをダブルクリックして開きます。

1. 次に、ツールバーに追加するイメージを開きます。

   > [!NOTE]
   > Visual Studio でイメージを開くと、イメージ**エディター**に表示されます。 画像は、他のグラフィックスプログラムで開くこともできます。

1. メニューにアクセスして、[ > **コピー**] を**編集**します。

1. ソースウィンドウの上部にあるタブを選択して、ツールバーに切り替えます。

1. メニューの [**編集** > **貼り付け**] を開きます。

   イメージは、新しいボタンとしてツールバーに表示されます。

#### <a name="to-move-a-toolbar-button"></a>ツールバーボタンを移動するには

ツールバー**ビュー**ペインで、ツールバーの新しい場所に移動するボタンをドラッグします。

- ツールバーからボタンをコピーするには、 **Ctrl**キーを押したまま**ツールバービュー**ペインに移動し、ボタンをツールバーの新しい場所にドラッグするか、別のツールバー上の場所にドラッグします。

- ツールバーボタンを削除するには、ツールバーボタンをクリックし、ツールバーのボタンをドラッグします。

- ツールバー上のボタンの間にスペースを挿入または削除するには、ツールバーのボタン間をドラッグします。

|操作|手順|
|------|------|
|スペースが続かないボタンの前にスペースを挿入するには|ボタンを右または下にドラッグして、[次へ] ボタンが半分に重なるようにします。|
|ボタンの前にスペースを挿入し、末尾のスペースを保持するには|ボタンをドラッグして、右端または下端が [次へ] ボタンに触れるか、重なっていることを示します。|
|ボタンの前にスペースを挿入し、次のスペースを閉じるには|ボタンを右または下にドラッグして、[次へ] ボタンが半分に重なるようにします。|
|ツールバーのボタン間のスペースを削除するには|スペースの一方の辺にあるボタンを、スペースのもう一方の側のボタンの近くにドラッグして、[次へ] ボタンが半分に重なるようにします。|

> [!NOTE]
> ドラッグしているボタンの横にスペースがなく、ボタンを隣接するボタンの半分を越えてドラッグすると、**ツールバーエディター**によって、ドラッグしているボタンの反対側にスペースが挿入されます。

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>ツールバーボタンのプロパティを変更するには

1. C++プロジェクトで、ツールバーボタンを選択します。

1. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で、 **id**プロパティに新しい id を入力するか、ドロップダウンリストを使用して新しい**id**を選択します。

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>ツールバーボタンのツールヒントを作成するには

1. ツールバーボタンを選択します。

1. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)の **[プロンプト]** フィールドに、ステータスバーのボタンの説明とメッセージの後に、`\n` とツールヒントの名前を追加します。

たとえば、**ワードパッド**の **[印刷]** ボタンのツールヒントを表示するには、次のようにします。

1. **ワードパッド**を開きます。

1. マウスポインターを **[印刷]** ツールバーボタンの上に置くと、マウスポインターの下に `Print` "という単語が表示されます。

1. **ワードパッド**ウィンドウの下部にあるステータスバーを見て、`Prints the active document`というテキストが表示されていることを確認します。

`Print` はツールヒントの名前、`Prints the active document` はステータスバーのボタンの説明です。

**ツールバーエディター**を使用してこの効果を適用する場合は、 **Prompt**プロパティを `Prints the active document\nPrint`に設定します。

## <a name="requirements"></a>要件

MFC または ATL

## <a name="see-also"></a>参照

[リソースエディター](../windows/resource-editors.md)
[メニューとその他のリソース](/windows/win32/menurc/resources)<br/>
[ツール バー ボタンのプロパティ](../windows/toolbar-button-properties.md)<br/>
