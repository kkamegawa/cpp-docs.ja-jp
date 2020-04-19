---
title: Visual Studio での C++ コードの編集とリファクター
description: Visual Studio の C++ コード エディターを使用して、コードの書式設定、移動、理解、リファクタリングを行います。
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: 2da1b38d2f5bb61edb473e5909b76225f214a116
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274773"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Visual Studio での C++ コードの編集とリファクター

Visual Studio には、コードの作成、編集、リファクターに役立つ複数のツールが用意されています。

##  <a name="intellisense"></a>IntelliSense

IntelliSense は、入力時にシンボルとコード スニペットの候補を示す強力なコード補完ツールです。 Visual Studio では C++ IntelliSense はリアルタイムで実行され、コードベースの更新時に分析を行い、レコメンデーションを提供します。 文字を多く入力するほど、推奨される結果のリストが絞り込まれます。

![C&#43;&#43; のメンバー リスト ドロップダウン](../ide/media/cpp-statement-completion.png)

シンボルの中には、結果を絞り込むために自動的に省略されるものもあります。 たとえば、クラスの外部からクラス オブジェクトのメンバーにアクセスすると、既定ではプライベート メンバーを表示したり、子クラスのコンテキストではない場合は、保護されたメンバーを表示することができなくなります。 下部にあるボタンを使用してフィルター処理を調整することができます。

ドロップダウン リストからシンボルを選択すると、**Tab** キー、**Enter** キー、または他のコミット文字 (既定: {}[]().,:;+-*/%&|^!=?@#\)) のいずれかでオートコンプリートできます。 このリストから文字を追加または削除するには、**クイック起動** (Ctrl + Q) で "IntelliSense" を検索し、 **[テキスト エディター] > [C/C++] > [詳細設定]** オプションを選択します。 **[メンバー一覧のコミット文字]** オプションを使用すると、好きなように変更してリストをカスタマイズすることができます。

**[メンバー一覧のフィルター モード]** オプションは、表示される IntelliSense オートコンプリートの候補の種類を制御します。 既定では **[あいまい]** に設定されています。 あいまい検索では、*MyAwesomeClass* と呼ばれるシンボルがある場合、「MAC」と入力して、オートコンプリートの候補の中からクラスを検索できます。 あいまいアルゴリズムにより、リストに表示するシンボルが満たす必要がある最小しきい値が設定されます。 **スマート** フィルター処理では、入力内容に一致する部分文字列を含むすべてのシンボルが表示されます。 **プレフィックス** フィルター処理では、入力内容で始まる文字列が検索されます。

C++ IntelliSense の詳細については、「[Visual C++ IntelliSense の機能](/visualstudio/ide/visual-cpp-intellisense)」と「[IntelliSense の C++ プロジェクトを構成する](/visualstudio/ide/visual-cpp-intellisense-configuration)」を参照してください。

## <a name="intellicode"></a>IntelliCode

IntelliCode は、AI 支援 IntelliSense です。 入力候補一覧の先頭に最も可能性が高い候補が配置されます。 IntelliCode レコメンデーションは、GitHub に存在する、それぞれ 100 個以上の星が付いた数千のオープンソース プロジェクトに基づいています。 ご使用のコードのコンテキストと組み合わせると、よくある方法を促進するように入力候補一覧が調整されます。

C++ を記述するときに、IntelliCode は C++ 標準ライブラリのような一般的なライブラリの使用に際して支援を行います。 コードのコンテキストは、最初に最も役に立つレコメンデーションを提供するために使用されます。 次の例では、`size` メンバー関数は `sort` 関数とよく併用されるため、結果リストの先頭に提示されます。

![C&#43;&#43; IntelliCode](../ide/media/intellicode-cpp.png "C++ IntelliCode")

::: moniker range="vs-2019"

Visual Studio 2019 では、IntelliCode は省略可能なコンポーネントとして **C++ によるデスクトップ開発**ワークロードで使用できます。 IntelliCode を C++ に対してアクティブにするには、 **[ツール]**  >  **[オプション]**  >  **[IntelliCode]**  >  **[全般]** の順に移動して、 **[C++ 基本モデル]** を **[有効]** に設定します。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 では、IntelliCode は Visual Studio Marketplace で拡張機能として利用できます。

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>予測 IntelliSense (試験段階)

**予測 IntelliSense** は、コンテキストの認識を使用して IntelliSense ドロップダウン リストに表示される結果の数を制限する試験段階の機能です。 このアルゴリズムは、予測される入力に一致する結果のみが表示されるように、一致する入力に適用されます。 最も簡単なケースでは、「`int x =`」と入力して IntelliSense ドロップダウン リストを呼び出すと、整数または整数を返す関数のみが表示されます。 この機能はまだ開発段階のため、既定でオフになっています。 これはグローバル シンボルで最適に機能します。メンバー関数はまだサポートされていません。 オンにするには、**クイック起動**で「予測」と入力するか、 **[ツール]**  >  **[オプション]**  >  **[テキスト エディター]**  >  **[C/C++]**  >  **[試験的]**  >  **[予測 IntelliSense]** の順に移動します。

**予測 IntelliSense** をオーバーライドして長いリストを表示するには、**Ctrl + J** を押します。**予測 IntelliSense** がオンになっている場合に、**Ctrl + J** を呼び出すと、予測フィルターが削除されます。 **Ctrl + J** をもう一度押すと、該当するメンバー一覧の結果からアクセシビリティ フィルターが削除されます。 IntelliSense ドリップダウン リストの下にある [+] ボタンは、**Ctrl + J** と同じことを行います。ボタンをポイントすると、表示されている内容についてのツールヒント情報が表示されます。

![C&#43;&#43; 予測 IntelliSense](../ide/media/predictive-intellisense-cpp.png "予測 IntelliSense")

上のスクリーンショットには、ドロップダウン リストの下にいくつかのボタンが表示されています。 これらは、さまざまな種類の結果に対して IntelliSense フィルターを有効にします。

- 変数と定数
- 関数
- 型
- [マクロ]
- 列挙体
- 名前空間

ボタンは、現在の IntelliSense セッションに関連がある場合にのみ表示されます。 通常は同時にすべてのボタンは表示されません。

## <a name="template-intellisense"></a>テンプレート IntelliSense

キャレットがテンプレート定義内にある場合は、**テンプレート バー**が表示され、ここで IntelliSense 用のサンプル テンプレート引数を指定できます。 

![既存のインスタンス化を示す C&#43;&#43;テンプレート IntelliSense](../ide/media/template-intellisense-cpp-1.png "既存のインスタンス化を示すテンプレート IntelliSense")

**テンプレート バー**を展開/折りたたむには、 **<T>** アイコンをクリックします。 **[編集]** ウィンドウを開くには、鉛筆アイコンをクリックするか、**テンプレート バー**をダブルクリックします。 

![C&#43;&#43; テンプレート IntelliSense](../ide/media/template-intellisense-cpp-3.png "テンプレート IntelliSense")

ウィンドウで行った編集は、効果をリアルタイムで確認できるように、ソース コードに直接適用されます。 

テンプレート バーは、コードでのインスタンス化に基づいて候補を自動設定します。 **[既存のインスタンス化をすべて追加する]** をクリックして、コード ベース全体でテンプレートのインスタンス化に使用されているすべての具体的な引数のリストを表示します。

![C&#43;&#43; テンプレート IntelliSense の結果リスト](../ide/media/template-intellisense-cpp-2.png "テンプレート IntelliSense の結果リスト")

エディターの下部にあるウィンドウには、各インスタンスが検出された場所とその引数が何であったかが表示されます。

![C&#43;&#43; テンプレート IntelliSense インスタンス化マップ](../ide/media/template-intellisense-cpp-4.png "テンプレート IntelliSense インスタンス化マップ")

**テンプレート バー**情報は、ユーザー固有として扱われます。 これは .vs フォルダーに格納され、ソース管理にはコミットされません。

##  <a name="error-squiggles-and-quick-fixes"></a>エラーの波線とクイック修正

エディターでコードの問題が検出されると、問題の下に色付きの波線が追加されます。 赤い波線はコードがコンパイルされないことを示します。 緑の波線は、重大な影響を及ぼす可能性があるその他の問題の種類を示します。 **[エラー一覧]** ウィンドウを開いて問題に関する詳細情報を得ることができます。

一部のエラーの種類と、一般的なコーディング パターンに対しては、エディターで**クイック修正**が提供されます。これは波線をポイントしたときに表示される電球の形で提供されます。 解決策を表示するには、下矢印をクリックします。 

次の例では、`vector` が宣言されましたが、定義が見つからなかったため、エディターによって含める必要があるヘッダー ファイルが提供されます。

![C&#43;&#43; クイック修正](../ide/media/quick-fix-for-header-cpp.png "C++ クイック修正")

エディターでは、いくつかのリファクタリングの機会のためのクイック修正も提供されます。 たとえば、ヘッダー ファイルでクラスを宣言すると、Visual Studio により別の .cpp ファイルでその定義を作成することが提案されます。 

![C&#43;&#43; クイック修正](../ide/media/quick-fix.png "C++ クイック修正")

## <a name="change-tracking"></a>Change tracking

ファイルに変更を加えると、左側に黄色のバーが表示され、未保存の変更が行われたことが示されます。 ファイルを保存すると、バーが緑色に変わります。 ドキュメントがエディターで開かれている限り、緑色と黄色のバーは保持されます。 これらは、ドキュメントを最後に開いてから加えられた変更を表します。

![C&#43;&#43; 変更の追跡](../ide/media/change-tracking-cpp.png "変更の追跡")

## <a name="move-code"></a>コードの移動

コード行を上下に移動するには、そのコード行を選択し、Alt キーを押しながら、**上方向/下方向**キーを押します。

##  <a name="insert-snippets"></a>スニペットの挿入

スニペットは、定義済みのソース コードです。 単一のポイント、選択したテキストの上で右クリックすると、スニペットを挿入するか、選択したテキストをスニペットで囲みます。 次の図は、for ループで選択したステートメントを囲む 3 つの手順を示します。 最終的なイメージの黄色のハイライトは、Tab キーでアクセスできる編集可能なフィールドです。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。

![C&#43;&#43; スニペットの挿入ドロップダウン](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>クラスの追加

**[プロジェクト]** メニューから、または**ソリューション エクスプローラー**のコンテキスト メニューから新しいクラスを追加します。

![C&#43;&#43; での新しいクラスの追加](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

クラス ウィザードを使用して、既存のクラスを変更したり、調べたりすることもできます。

![C&#43;&#43; クラス ウィザード](../ide/media/vs2017-class-wizard.png)

詳細については、「[コード ウィザードを使用した機能の追加 (C++)](../ide/adding-functionality-with-code-wizards-cpp.md)」を参照してください。

##  <a name="refactoring"></a>リファクタリング

クイック操作のコンテキスト メニューから、またはエディターの[電球](/visualstudio/ide/perform-quick-actions-with-light-bulbs)をクリックすることで、リファクタリングが利用できます。  **[編集]、[リファクター]** メニューから利用できるものもあります。  これには次の機能があります。

* [名前の変更](refactoring/rename.md)
* [Extract 関数](refactoring/extract-function.md)
* [純粋仮想の実装](refactoring/implement-pure-virtuals.md)
* [宣言/定義の作成](refactoring/create-declaration-definition.md)
* [Move 関数の定義](refactoring/move-definition-location.md)
* [未加工の文字列リテラルに変換](refactoring/convert-to-raw-string-literal.md)
* [署名の変更](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>ClangFormat と EditorConfig を使用したコード スタイルの適用

Visual Studio 2017 以降では、[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (Clang/LLVM に基づいた C++ 用の一般的なコード書式設定ユーティリティ) の組み込みサポートが付属しています。 [クイック起動](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box)に「ClangFormat」と入力して、次の一般的な形式のいずれかを使用するように設定します。

- LLVM
- Google
- Chromium
- Mozilla
- WebKit
- Visual Studio

独自の .clang-format または _clang-format ファイルを指定して、同じレベル以下のすべてのコード ファイルにカスタム ルールを適用することもできます。

ファイルは、ソース管理を通じて簡単に共有できるため、開発チーム全体にコーディング規則を適用することができます。

![C&#43;&#43; Clang Format](../ide/media/clang-format-cpp.png "Clang Format")

Visual Studio 2017 以降では、同様の方法で機能する [EditorConfig](https://editorconfig.org/) もサポートしています。 ただし、ClangFormat には、C++ 固有のルールなど、EditorConfig よりも多くのスタイル オプションがあります。 **EditorConfig** を使用して、 **.editorconfig** ファイルを作成し、それをご使用のコードベースとは別のフォルダーに配置して、これらのフォルダーとそのサブフォルダーにコード スタイルを指定します。 **.editorconfig** ファイルは、親フォルダー内の他の **.editorconfig** ファイルよりも優先され、 **[ツール]**  >  **[オプション]** から構成されたすべての書式設定を上書きします。 タブと空白、インデントのサイズなどにルールを設定することができます。 詳細については、「[EditorConfig で移植可能なカスタム エディター設定を作成する](/visualstudio/ide/create-portable-custom-editor-options)」を参照してください。

## <a name="other-formatting-options"></a>その他の書式設定オプション

**クイック起動**検索ボックスには、設定やツールを検索する最も簡単な方法が用意されています。 これはメイン メニューにあります。 入力を開始するだけで、オートコンプリート リストにより結果がフィルター処理されます。

![Visual Studio のクイック起動](../ide/media/vs2015_cpp_quick_launch.png "クイック起動")

インデント、中かっこの補完、色付けなどの書式設定オプションを設定するには、 **[クイック起動]** ウィンドウに「C++ Formatting」と入力します。

![C++ 書式設定オプション](media/cpp-formatting-options.png)

他の書式設定オプションは、メイン メニューの **[編集]**  >  **[詳細設定]** で見つかります。

![C++ の高度な編集オプション](media/edit-advanced-cpp.png)

C++ 固有の編集機能の有効化と構成のオプションは、 **[ツール]**  >  **[オプション]**  >  **[テキスト エディター]**  >  **[C/C++]** にあります。 設定するオプションを選択した後、ダイアログにフォーカスがあるときに **F1** キーを押すと、詳細なヘルプを表示できます。 コードの一般的な書式設定オプションを確認するには、 **[クイック起動]** に「`Editor C++`」と入力します。

![Visual Studio Tools > オプション](../ide/media/tools-options.png "エディター オプション")

将来のバージョンの Visual Studio に含まれる場合とそうでない場合がある実験用の機能は、[[テキスト エディター]、[C++]、[実験用]](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) ダイアログにあります。 Visual Studio 2017 以降では、このダイアログで**予測 IntelliSense** を有効にすることができます。

## <a name="see-also"></a>関連項目

[C++ コードの読み取りと理解](read-and-understand-code-cpp.md)</br>
[Visual Studio で C++コード ベース内を移動する](navigate-code-cpp.md)</br>
[Live Share for C++ による共同作業](live-share-cpp.md)