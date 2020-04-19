---
title: Visual Studio での C++ 開発の概要
description: Visual Studio IDE は、コード エディター、デバッガー、テスト フレームワーク、静的アナライザー、その他のプログラミング ツールを利用した Windows、Linux、Android、iOS 上での C++ 開発をサポートしています。
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415713"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Visual Studio での C++ 開発の概要

Visual Studio 統合開発環境 (IDE) に属する Microsoft C++ (MSVC) では、他の言語と共通の多くのウィンドウやツールを共有します。 **ソリューション エクスプローラー**、コード エディター、デバッガーなどの多くは、「[Visual Studio IDE](/visualstudio/get-started/visual-studio-ide)」に記載されています。 共有ツールやウィンドウの一連の機能は、C++ 用と他の言語用のものでは若干異なることがよくあります。 一部のウィンドウやツールは、Visual Studio Professional 版または Visual Studio Enterprise 版でのみ使用できます。

Visual Studio IDE の共有ツールに加えて、MSVC には、ネイティブ コード開発に特化したいくつかのツールがあります。 この記事には、これらのツールの一覧も掲載します。 Visual Studio の各エディションで使用可能なツールの一覧については、「[C++ Tools and Features in Visual Studio Editions](visual-cpp-tools-and-features-in-visual-studio-editions.md)」 (さまざまな Visual Studio エディションの C++ ツールと機能) を参照してください。

## <a name="create-projects"></a>プロジェクトを作成する

*プロジェクト*は基本的に、実行可能プログラムやライブラリに組み込まれている、イメージやデータ ファイルなどの一連のソース コード ファイルとリソースです。

Visual Studio では、使用するすべてのプロジェクト システムやカスタム ビルド ツールがサポートされ、IntelliSense、参照、デバッグなどが完全にサポートされます。

- **MSBuild** は、Visual Studio 用のネイティブ プロジェクト システムです。 メイン メニューから **[ファイル]** 、 **[新規]** 、 **[プロジェクト]** の順に選択すると、さまざまな種類の MSBuild *プロジェクト テンプレート*が表示されます。これを利用すると、さまざまな種類の C++ アプリケーションの開発を簡単に始められます。

   ::: moniker range="vs-2019"

   ![新しいプロジェクト テンプレート](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 の [新しいプロジェクト] ダイアログ")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![プロジェクト テンプレート](media/vs2017-new-project.png "Visual Studio 2017 の [新しいプロジェクト] ダイアログ")

   ::: moniker-end

   一般的に、既存の CMake プロジェクトを使用したり、別のプロジェクト システムを使用したりしている場合を除き、新しいプロジェクトにはこれらのテンプレートを使用する必要があります。 詳細については、[MSBuild ベースのプロジェクトを作成し、管理する](../build/creating-and-managing-visual-cpp-projects.md)方法に関するページを参照してください。

- **CMake** はクロスプラットフォームのビルド システムであり、C++ によるデスクトップ開発のワークロードをインストールする際に Visual Studio IDE に統合されます。 新しいプロジェクトに CMake プロジェクト テンプレートを使用するか、CMakeLists.txt ファイルを含むフォルダーを開きます。 詳細については、「[CMake projects in Visual Studio](../build/cmake-projects-in-visual-studio.md)」 (Visual Studio の CMake プロジェクト) をご覧ください。

- ファイルの緩やかな集合を含む、その他の C++ ビルド システムは、 **[フォルダーを開く]** 機能を通じてサポートされます。 単純な JSON ファイルを作成して、ビルド プログラムを呼び出し、デバッグ セッションを構成します。 詳細については、「[Open Folder projects for C++](../build/open-folder-projects-cpp.md)」 (C++ の [フォルダーを開く] プロジェクト) をご覧ください。

## <a name="add-to-source-control"></a>ソース管理に追加

ソース管理では、複数の開発者間で作業を調整したり、開発中の作業を運用コードから分離したり、ソース コードをバックアップしたりすることができます。 Visual Studio は、Git と [Team Foundation バージョン管理 \(TFVC\)](/azure/devops/repos/tfvc/) をその**チーム エクスプローラー** ウィンドウをサポートしています。

::: moniker range="vs-2019"

![チーム エクスプローラー](media/vs2019-team-explorer.png "Visual Studio 2017 のチーム エクスプローラー")

::: moniker-end

::: moniker range="<=vs-2017"

![チーム エクスプローラー](media/vs2017-team-explorer.png "Visual Studio 2017 のチーム エクスプローラー")

::: moniker-end

Git と Azure のリポジトリの統合については、「[Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)」 (Visual Studio 2017 と Azure Repos Git でコードを共有する) を参照してください。 Git と GitHub の統合については、「[GitHub Extension for Visual Studio](https://visualstudio.github.com/)」 (Visual Studio 向けの GitHub 拡張) を参照してください。

## <a name="obtain-libraries"></a>ライブラリを取得する

サードパーティ製のライブラリを取得してインストールするには、[vcpkg](../build/vcpkg.md) パッケージ マネージャーを使います。 現在、900 個を超えるオープンソース ライブラリをカタログで使用できます。

## <a name="create-user-interfaces-with-designers"></a>デザイナーでユーザー インターフェイスを作成する

プログラムにユーザー インターフェイスがある場合、デザイナーを使用し、ボタンやリスト ボックスなどのコントロールをユーザー インターフェイスに簡単に入力できます。 ツールボックス ウィンドウからコントロールをドラッグし、デザイン サーフェイスにドロップすると、Visual Studio によって、それを動かすために必要なリソースとコードが生成されます。 その後、外観と動作をカスタマイズするコードを記述します。

![デザイナーとツールボックス](media/vs2017-toolbox-designer.png "Visual Studio 2017 のツールボックスとデザイナー")

ユニバーサル Windows プラットフォーム アプリのユーザー インターフェイスの設計方法について詳しくは、[デザインと UI](https://developer.microsoft.com/windows/design) に関するページを参照してください。

MFC アプリケーションのユーザー インターフェイスの作成方法については、「[MFC デスクトップ アプリケーション](../mfc/mfc-desktop-applications.md)」を参照してください。 Win32 Windows プログラムについては、「[Windows デスクトップ アプリケーション](../windows/windows-desktop-applications-cpp.md)」を参照してください。

## <a name="write-code"></a>コードの記述

プロジェクトを作成すると、すべてのプロジェクト ファイルが**ソリューション エクスプローラー** ウィンドウに表示されます。 (*ソリューション*は、1 つまたは複数の関連プロジェクトのための論理コンテナーです。)**ソリューション エクスプローラー**で .h または .cpp ファイルをクリックすると、ファイルがコード エディターで開きます。

![ソリューション エクスプローラーとコード エディター](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 のソリューション エクスプローラーとコード エディター")

コード エディターは、C++ ソース コード専用のワード プロセッサです。 このエディターでは、コードを読みやすく理解しやすいものにするために、言語のキーワード、メソッド名と変数名、およびその他のコードの要素が色分けされます。 また、コードをリファクタリングしたり、異なるファイル間で移動したり、コードの構造を認識したりするためのツールも提供されます。 詳細については、[コードの作成とリファクタリング](../ide/writing-and-refactoring-code-cpp.md)に関するページを参照してください。

## <a name="add-and-edit-resources"></a>リソースの追加と編集

通常、Windows プログラムや DLL には、ダイアログ、アイコン、画像、ローカライズ可能な文字列、スプラッシュ画面、データベースの接続文字列、または任意のデータなど、いくつかの "*リソース*" が含まれます。 Visual Studio には、リソースの追加や編集を行うためのツールが含まれています。 詳細については、「[リソース ファイルの操作](../windows/working-with-resource-files.md)」をご覧ください。

## <a name="build-compile-and-link"></a>ビルド (コンパイルおよびリンク)

メニュー バーの **[ビルド]**  >  **[ソリューションのビルド]** を選択するか、**Ctrl + Shift + B** キーの組み合わせを押して、プロジェクトのコンパイルおよびリンクを行います。 ビルド エラーと警告は、[エラー一覧] (**Ctrl + \\、E**) に報告されます。 **[出力]** ウィンドウ (**Alt + 2**) にビルド プロセスに関する情報が表示されます。

![[出力] ウィンドウと [エラー一覧]](media/vs2017-output-error-list.png "Visual Studio 2017 の [出力] ウィンドウと [エラー一覧]")

ビルドの構成の詳細については、[プロジェクト プロパティの操作](../build/working-with-project-properties.md)に関するページと[プロジェクトとビルド システム](../build/projects-and-build-systems-cpp.md)に関するページを参照してください。

コンパイラ (cl.exe) や、その他多くのビルド関連のスタンドアロン ツール (コマンド ラインから直接入力する NMAKE や LIB など) も使用できます。 詳細については、「[コマンドラインでの C/C++ コードのビルド](../build/building-on-the-command-line.md)」と「[C/C++ ビルドのリファレンス](../build/reference/c-cpp-building-reference.md)」を参照してください。

## <a name="debug"></a>デバッグ

**[F5]** を押すことでデバッグを開始できます。 (**F9** キーを押して) 設定した任意のブレークポイントで、実行を一時停止することができます。 また、コードを一度に 1 行ずつステップ実行したり (**F10** キー)、変数やレジスタの値を表示したり、場合によってはコードに変更を加え、再コンパイルせずにデバッグを続行したりできます。 次の図は、ブレークポイントで実行が停止したデバッグ セッションを示しています。 データ構造体メンバーの値は**ウォッチ ウィンドウ**に表示されます。

![デバッグ セッション](media/vs2017-debug-watch.png "Visual Studio 2017 のデバッグ セッション")

詳しくは、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」をご覧ください。

## <a name="test"></a>テスト

Visual Studio には、C++ 用の Microsoft 単体テスト フレームワークおよび Boost.Test、Google Test、CTest のサポートが含まれます。 **テスト エクスプローラー** ウィンドウからテストを実行します。

![テスト エクスプローラー](media/cpp-test-explorer-passed.png "Visual Studio 2017 のテスト エクスプローラー")

詳細については、[単体テストを使用してコードを検証する](/visualstudio/test/unit-test-your-code)方法に関するページと「[Visual Studio で C/C++ 用の単体テストを作成する](/visualstudio/test/writing-unit-tests-for-c-cpp)」を参照してください。

## <a name="analyze"></a>解析

Visual Studio には、ソース コードの潜在的な問題を検出できる静的コード分析ツールが含まれています。 それらのツールには、[C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) ルール チェッカーの実装が含まれています。 詳細については、「[C/C++ のコード分析の概要](/cpp/code-quality/code-analysis-for-c-cpp-overview)」を参照してください。

## <a name="deploy-completed-applications"></a>完成したアプリケーションの配置

Microsoft Store から従来のデスクトップ アプリケーションと UWP アプリの両方を展開できます。 CRT の配置は、水面下で自動的に処理されます。 詳細については、「[Publish Windows apps and games](/windows/uwp/publish/)」(Windows のアプリとゲームを公開する) を参照してください。

また、ネイティブ C++ デスクトップを別のコンピューターに配置することもできます。 詳細については、「[デスクトップ アプリケーションの配置](../windows/deploying-native-desktop-applications-visual-cpp.md)」を参照してください。

C++/CLI プログラムの配置について詳しくは、「[配置ガイド (開発者向け)](/dotnet/framework/deployment/deployment-guide-for-developers)」を参照してください。

## <a name="next-steps"></a>次の手順

以下の入力記事のいずれかに従って、Visual Studio をさらに詳しく調べます。

> [!div class="nextstepaction"]
> [コード エディターの使用方法について学習する](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [プロジェクトとソリューションについて学習する](/visualstudio/get-started/tutorial-projects-solutions)
