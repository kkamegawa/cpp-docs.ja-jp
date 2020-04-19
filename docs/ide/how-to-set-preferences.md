---
title: Visual Studio C++でコーディング設定を設定する
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816559"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Visual Studio C++でコーディング設定を設定する

Visual Studio をカスタマイズC++することにより、コーディングエクスペリエンスをより使いやすく、生産性、pleasurable に高めることができます。 可能な代替手段としては以下の方法があります。

- メニューとツールバーをカスタマイズします。
- ウィンドウのレイアウトを調整します。
- 配色テーマを設定します。
- ClangFormat の複数のスタイルを含む書式設定規則を指定C++します。
- カスタムキーボードショートカットを作成します。

複数のコンピューター間で設定を同期し、複数の設定セットを作成して保存し、チームメイトと共有できます。 Visual Studio Marketplace から拡張機能をインストールして、動作をカスタマイズするための追加オプションを提供できます。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

## <a name="arrange-window-layout"></a>ウィンドウレイアウトの配置

Visual Studio ウィンドウ内では、領域はメインメニュー、ツールバー、コードエディター (またはドキュメントウィンドウ)、およびツールウィンドウ (ソリューションエクスプローラーやエラー一覧など) に分割されます。 一部のウィンドウは、同じ位置に重なっています。 たとえば、ソリューションエクスプローラー、クラスビュー、リソースビュー、ソース管理エクスプローラーはすべて同じ既定の位置を共有します。 これらを切り替えるには、フレームの下部にあるタブを選択します。 これらのウィンドウのうち2つ以上を同時に表示するには、そのうちの1つをタイトルバーで新しい位置にドラッグするだけです。 これは、Visual Studio のメインウィンドウの境界の1つに対してドッキングするか、フローティングすることができます。

次のスクリーンショットは、既定の位置からコードエディターの左側の新しいドッキング位置にドラッグされている**チームエクスプローラー**ウィンドウを示しています。 青い網掛け領域は、マウスボタンが離されたときにウィンドウが配置される場所を示しています。

![レイアウトの変更が強調表示されている Visual Studio チームエクスプローラーウィンドウのスクリーンショット](media/window-layout-move-team-explorer.png)

ドキュメントウィンドウでは、開いている各ファイルがタブ付きフレームに含まれています。 ツールウィンドウと同様に、これらのタブをフローティングまたはロックできます。 詳細については、「[Visual Studio のウィンドウ レイアウトをカスタマイズする](/visualstudio/ide/customizing-window-layouts-in-visual-studio)」を参照してください。

すべてのツールウィンドウを非表示にして、コードエディターウィンドウを最大化するには、 **Alt** + **Shift** + enter キーを押して、*全画面表示モード***を切り替え**ます。

## <a name="set-c-coding-styles-and-formatting"></a>コーディングC++スタイルと書式設定の設定

インデントや中かっこの位置など、多くの個別のコード書式設定オプションを指定できます。 これを行うには、 **[ツール**] > [**テキストエディター** **]**  > [ **C/C++**  > の**書式設定**] の順に > ます (または、 **Ctrl キーを押しながら Q キーを押し**、[書式設定] を検索します)。 また、 [Clangformat](https://clang.llvm.org/docs/ClangFormat.html)スタイル (または独自のカスタム clangformat スタイル) のいずれかを指定することもできます。

![ClangFormat オプションのスクリーンショット](media/clang-format-ide.png)

すべての書式設定オプションの詳細については、「[[オプション]、C++[テキストエディター]、[C/]、[書式設定](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)]」を参照してください。

## <a name="set-the-color-theme"></a>配色テーマの設定

明るい背景または暗い背景を設定するには、 **Ctrl + Q キーを押し**て、"配色テーマ" を検索します。 また、[ > **ツール**]、[**オプション]**  >  **[環境]** の順に移動し、 **[配色テーマ]** を選択して見つけることもできます。

![配色テーマのスクリーンショット](media/tools-options-color-theme.png)

次に、ダークテーマを示します。

![濃い色のテーマを使用した Visual Studio のスクリーンショット](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>コードの色付けをカスタマイズする

Visual Studio 2019 では、3つの定義済みの*配色*を選択できます。 これは、エディターでコード要素を色付けする方法を指定します。 テーマを選択するには、 **[ツール]**  > [**オプション]** 、[ **C++ C/**  > **ビュー**]、 **[配色]** の選択 の順に ** >  > ます**。

![強調表示C++されている配色オプションのスクリーンショット](media/color-schemes.png)

**Visual Studio 2017**という配色では、ほとんどのコード要素は単に黒です。 **強化**された配色では、関数、ローカル変数、マクロ、およびその他の要素が色分けされています。 **Enhanced (Globals と Members)** スキームでは、クラスメンバーと比較してグローバル関数と変数が色分けされています。 既定のモードは " **Enhanced**" で、次のようになります。

![拡張配色のスクリーンショット](media/color-scheme-enhanced.png)

アクティブになっているテーマや配色に関係なく、個々のコード要素のフォントと色をカスタマイズできます。 これを行うには、 **[ツール]**  > [**オプション]**  >  **[環境]**  > **フォントおよび色**を選択します (または、 **Ctrl + Q キーを押し**て "fonts" を検索します)。 オプションがC++表示されるまで、表示項目の一覧を下にスクロールします。

![フォントおよびC++色のオプションのスクリーンショット](media/tools-options-cpp-colors.png)

ここで設定した色は、配色に対して定義されている値よりも優先されます。 配色の既定の色に戻す場合は、[**既定値**に戻す] を選択します。

## <a name="customize-the-toolbars"></a>ツールバーのカスタマイズ

ツールバーには、メニューやキーボードショートカットを使用するのではなく、1回のクリックでコマンドを発行する便利な方法が用意されています。 Visual Studio には、ツールバーの標準セットが含まれています。 標準的C++な開発では、最も役に立つツールバーは、通常、標準、テキストエディター、ビルド、デバッグ、ソース管理、および比較ファイルです。 Windows 開発の場合、ダイアログボックスや編集アイコンをレイアウトするときに、ダイアログエディターとイメージエディターが役立ちます。

ツールバーのアイコンの上にマウスを移動すると、表示されるコマンドが表示されます。

![ホバー時に使用可能なコマンド情報の例を含むツールバーアイコンのスクリーンショット](media/toolbar-mouse-hover.png)

下矢印を選択すると、コマンドを追加または削除したり、カスタムツールバーを作成したりできます。 ツールバーを新しい場所に移動するには、左側の点線のバーでドラッグします。

![下矢印と点線バーが強調表示されているツールバーのスクリーンショット](media/toolbar-move-edit.png)。

詳細については、「[方法: Visual Studio でメニューおよびツールバーをカスタマイズする](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio)」を参照してください。

## <a name="show-or-hide-line-numbers"></a>行番号の表示と非表示を切り替えます

エディターウィンドウの左側に行番号を表示するかどうかを指定できます。 **[オプション]** の **[CC++/]** で、 **[全般]** を選択します。 **[設定]** セクションで、好みに応じて**行番号**を選択またはクリアします。

![行番号が強調表示されている [全般] オプションのスクリーンショット](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>ショートカットキーの作成

Visual Studio の多くのコマンドには、*キーボードショートカット*、Ctrl キー、Alt キー、および Shift キーを使用したキーの組み合わせがあります。 これらのキーボードショートカットを変更することも、Visual Studio で独自のショートカットキーを作成することもできます。 **[ツール]**  >  **[オプション]**  > **環境** > **キーボード**(または**Ctrl + Q キーを押し**て、[ショートカット] を検索します) にアクセスします。 詳細については、「 [Visual Studio でのキーボードショートカットの識別とカスタマイズ](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)」を参照してください。
