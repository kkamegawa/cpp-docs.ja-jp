---
title: '方法: イメージを編集します。'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387961"
---
# <a name="how-to-edit-an-image"></a>方法: イメージを編集します。

選択内容 ツールを使用すると、切り取り、コピー、クリア、サイズを変更、反転、または移動するイメージの領域を定義します。 **矩形選択**ツールを定義し、イメージの四角形の領域を選択します。 **不規則選択**ツール、切り取り、コピー、またはその他の操作を選択する領域のフリーハンドのアウトラインを描画できます。

> [!NOTE]
> 参照してください、**矩形選択**と**不規則選択**ツールには描か[イメージ エディターのツールバー](../windows/toolbar-image-editor-for-icons.md) の各ボタンに関連付けられたツールヒントを表示または**イメージ エディター**ツールバー。

選択範囲からカスタム ブラシを作成することもできます。 詳細については、次を参照してください。[カスタム ブラシの作成](../windows/creating-a-custom-brush-image-editor-for-icons.md)です。

## <a name="how-to"></a>方法

イメージを編集するを参照してください。 どのように。

### <a name="to-select-an-image"></a>イメージを選択するには

1. 使用して、**イメージ エディター**ツールバーまたはメニューに移動して**イメージ** > **ツール**選択ツールを必要とします。

1. 選択したいイメージ領域の 1 つ上の隅にカーソルを移動します。 十字線は、カーソルが画像の上にあると表示されます。

1. 挿入ポイントを選択する領域の反対側の隅にドラッグします。 四角形に表示するピクセルが選択されます。 四角形の下にあるものを含む四角形内のすべてのピクセルは、選択範囲に含まれます。

1. マウスのボタンを離します。 選択範囲の境界線は、選択した領域を囲みます。

#### <a name="to-select-an-entire-image"></a>イメージ全体を選択するには

現在の選択範囲の外部でイメージを選択します。 選択範囲の境界線は、フォーカスを変更し、もう一度画像全体が含まれます。

### <a name="to-edit-parts-of-an-image"></a>イメージの一部を編集するには

標準の編集操作を行うことができます: 切り取り、コピー、消去、および移動-で、[選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)選択範囲がイメージ全体またはその一部だけであるかどうか、です。 **イメージ エディター**を使用して、 **Windows クリップボード**、間でのイメージを転送することができます、**イメージ エディター**と Windows の他のアプリケーション。

さらに、画像全体またはその一部だけが含まれて かどうか、選択範囲のサイズを変更できます。

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>現在の選択範囲を切り取ってクリップボードに移動するには

メニューに移動して**編集** > **切り取り**します。

#### <a name="to-copy-the-selection"></a>選択範囲をコピーするには

1. サイズ変更ハンドルを除く上または任意の場所の選択範囲の枠線内でポインターを置きます。

1. 押しながら、 **Ctrl**キーの選択範囲を新しい場所にドラッグするとします。 元の選択範囲の領域は変更されません。

1. 選択範囲の現在の場所にあるイメージをコピーするには、選択範囲のカーソルの外部を選択します。

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>イメージにクリップボードの内容を貼り付ける

1. メニューに移動して**編集** > **貼り付け**します。

   選択範囲の境界線で囲まれた、クリップボードの内容は、ウィンドウの左上隅に表示されます。

1. 選択範囲の境界線内でポインターを配置し、イメージに目的の場所にイメージをドラッグします。

1. 新しい場所にあるイメージを固定するには、選択範囲の境界線の外部でを選択します。

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>クリップボードに移動することがなく現在の選択範囲を削除するには

メニューに移動して**編集** > **削除**します。

   選択範囲の元の領域を現在の背景色で塗りつぶします。

> [!NOTE]
> アクセスできる、**切り取り**、**コピー**、**貼り付け**、および**削除**コマンド内で右クリック、**リソース ビュー**ウィンドウ。

#### <a name="to-move-the-selection"></a>選択範囲を移動するには

1. サイズ変更ハンドルを除く上または任意の場所の選択範囲の枠線内でポインターを置きます。

1. 新しい位置にドラッグします。

1. 新しい場所にある画像の選択範囲を固定するには、選択範囲の境界線の外側を選択します。

選択した場合、描画の詳細については、次を参照してください。[カスタム ブラシの作成](../windows/creating-a-custom-brush-image-editor-for-icons.md)です。

### <a name="to-flip-an-image"></a>イメージを反転するには

反転または元のミラー イメージを作成する、イメージを上下逆に、有効にするか、右側にイメージを一度に 90 度回転イメージを回転させることができます。

- イメージを水平方向に反転させる (ミラー イメージ) メニューに移動して**イメージ** > **水平方向に反転**します。

- イメージを垂直方向に反転させる (に上下逆に) メニューに移動して**イメージ** > **垂直方向に反転**します。

- イメージを 90 度回転するには、メニューに移動**イメージ** > **90 度回転**します。

   > [!NOTE]
   > 使用することも、[アクセラレータ (ショートカット) キー](../windows/accelerator-keys-image-editor-for-icons.md)これらのコマンドのショートカット メニューから、コマンドにアクセスまたは (の中にイメージの外部選択、**イメージ エディター**)。

### <a name="to-resize-an-image"></a>イメージのサイズを変更するには

動作、**イメージ エディター**したかどうかに依存するイメージのサイズ変更中に[選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)イメージ全体または一部だけです。

選択範囲には、イメージの一部のみが含まれている場合、**イメージ エディター**ピクセルの行または列を削除して、現在の背景色で領域で、選択範囲を縮小します。 ピクセルの行または列を複製することにより、選択範囲に拡大または縮小できますも。

選択範囲には、全体のイメージが含まれている場合、**イメージ エディター**縮小いると、イメージを拡大またはトリミングおよび拡張されています。

イメージのサイズ変更の 2 つのメカニズムがある: サイズ変更ハンドルと[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。 イメージの一部またはすべてのサイズを変更するサイズ変更ハンドルをドラッグするとします。 サイズ変更ハンドルをドラッグすることは、solid です。 白抜きのハンドルをドラッグすることはできません。 使用して、**プロパティ**全体のサイズを変更するにはウィンドウのイメージのみ、選択したパーツではありません。

![サイズ変更ハンドルをビットマップに](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
サイズ変更ハンドル

> [!NOTE]
> ある場合、**タイル グリッド**で選択したオプション、[グリッドの設定 ダイアログ ボックス](../windows/grid-settings-dialog-box-image-editor-for-icons.md)、[次へ] のタイル グリッド線にスナップのサイズを変更します。 だけの場合、**ピクセル グリッド**オプションは、(既定の設定) を選択するには、次のピクセルにスナップのサイズを変更します。

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>[プロパティ] ウィンドウを使用してイメージ全体のサイズを変更するには

1. イメージを変更するプロパティを開きます。

1. **幅**と**高さ**ボックス、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)、目的のサイズを入力します。

   イメージのサイズを増加している場合、**イメージ エディター**下方右側にイメージまたはその両方を拡張し、新しいリージョンを現在の背景色で塗りつぶします。 イメージが伸縮されていません。

   イメージのサイズを短縮する場合、**イメージ エディター**右端または下端またはその両方でイメージをトリミングします。

   > [!NOTE]
   > 使用することができます、**幅**と**高さ**部分的な選択範囲のサイズを変更しないように、のみ全体イメージのサイズを変更するプロパティ。

#### <a name="to-crop-or-extend-an-entire-image"></a>トリミングまたはイメージ全体の拡張

1. イメージ全体を選択します。

   イメージの一部が現在選択されているイメージ全体を選択する場合は、任意の場所、現在の選択範囲の境界線の外側にあるイメージを選択します。

1. イメージが適切なサイズまでは、サイズ変更ハンドルをドラッグします。

通常、**イメージ エディター**トリミングまたはサイズ変更ハンドルを移動してサイズを変更するときに、イメージを拡張します。 押しながら場合、 **Shift**キーのサイズ変更ハンドルを移動すると、**イメージ エディター**縮小または拡大イメージ。

#### <a name="to-shrink-or-stretch-an-entire-image"></a>イメージ全体を拡大または縮小するには

1. イメージ全体を選択します。

   イメージの一部が現在選択されているイメージ全体を選択する場合は、任意の場所、現在の選択範囲の境界線の外側にあるイメージを選択します。

1. 押しながら、 **Shift**キーし、イメージが適切なサイズになるまで、サイズ変更ハンドルをドラッグします。

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>イメージの一部を拡大または縮小するには

1. サイズを変更するイメージの一部を選択します。 詳細については、次を参照してください。[領域のイメージの選択](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)します。

1. 選択範囲が適切なサイズになるまでは、サイズ変更ハンドルのいずれかをドラッグします。

### <a name="to-edit-an-image-outside-of-a-project"></a>プロジェクトの外側でイメージを編集するには

開くでき、たとえばスタンドアロンを編集するためのビットマップを開いて、グラフィックス アプリケーションと同様に、開発環境でイメージを編集できます。 使用するイメージに必要な Visual Studio プロジェクトの一部はありません。

1. メニューに移動して**ファイル** > **オープン**します。

1. **ファイルの種類**ボックスで、**すべてのファイル**します。

1. 編集しイメージを開きます。

### <a name="to-change-image-properties"></a>画像のプロパティを変更するには

設定またはを使用して、イメージのプロパティを変更することができます、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。

1. 内のイメージを開く、**イメージ エディター**します。

1. **プロパティ**ウィンドウで、イメージのいずれかまたはすべてのプロパティを変更します。

   |プロパティ|説明|
   |--------------|-----------------|
   |**色**|イメージのカラー スキームを指定します。 選択**モノクロ**、 **16**、または**256**、または**True Color**します。<br/><br/>選択する場合、既に 16 色パレットを使用してイメージを描画した、**モノクロ**イメージで色を黒と白の置換が発生します。 コントラストは常に維持されません。 変換など、赤、緑の隣接する領域は両方を黒にします。|
   |**ファイル名**|イメージ ファイルの名前を指定します。<br/><br/>既定では、Visual Studio には、既定のリソース識別子 (IDB_BITMAP1) して、適切な拡張機能を追加すること ("IDB_") の最初の 4 つの文字を削除して作成された基本ファイル名が割り当てられます。 この例では、イメージのファイル名になります*BITMAP1.bmp*します。 その名前を変更することが*MYBITMAP1.bmp*します。|
   |**Height**|イメージの高さをピクセル単位で設定します。 既定値には 48 です。<br/><br/>イメージをトリミングまたは既存のイメージの下の空白領域に追加します。|
   |**ID**|リソースの識別子を設定します。<br/><br/>イメージの Microsoft Visual Studio では、既定では、識別子を割り当てます、[次へ] 使用可能な一連の。IDB_BITMAP1、IDB_BITMAP2 など。 類似した名前は、アイコンとカーソルに使用されます。|
   |**パレット**|色のプロパティを変更します。<br/><br/>色を選択して表示 をダブルクリック、[カスタム カラー セレクター ダイアログ ボックス](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)します。 RGB または HSL 値を適切なテキスト ボックスに入力して、色を定義します。|
   |**SaveCompressed**|イメージが圧縮された形式かどうかを示します。 このプロパティは読み取り専用です。<br/><br/>Visual Studio には、圧縮された形式で画像を保存することはできませんので、Visual Studio で作成された任意のイメージのこのプロパティは**False**します。 このプロパティになります (他のプログラムで作成された) 圧縮されたイメージを開くには、Visual Studio で場合、 **True**します。 Visual Studio を使用して、圧縮されたイメージを保存する場合に圧縮されずにこのプロパティは元に戻す**False**します。|
   |**Width**|イメージの幅をピクセル単位で設定します。 ビットマップの既定値には 48 です。<br/><br/>イメージをトリミングまたは既存のイメージの右側に空白領域を追加します。|

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[アイコン用イメージ エディター](../windows/image-editor-for-icons.md)<br/>
[方法: アイコンまたはその他の画像を作成する](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[方法: 描画ツールを使用する](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[方法: 色を調整する](../windows/working-with-color-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>