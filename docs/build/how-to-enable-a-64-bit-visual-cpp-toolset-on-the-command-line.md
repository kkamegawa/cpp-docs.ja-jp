---
title: '方法: コマンドラインで64ビットの MSVC ツールセットを有効にする'
ms.date: 07/24/2019
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: 9e8a671a7fe67150e1b867c62231173429f7b6ed
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415927"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>方法: コマンドラインで64ビット、x64 でホストされる MSVC ツールセットを有効にする

Visual Studio には C++ コンパイラ、リンカー、その他のツールが含まれており、それらを使って、32 ビット、64 ビット、または ARM ベースの Windows オペレーティング システムで実行できるプラットフォーム固有バージョンのアプリを作成できます。 他のオプションの Visual Studio ワークロードを利用すると、C++ ツールを使って iOS、Android、Linux などの他のプラットフォームをターゲットにできます。 既定のビルド アーキテクチャでは、32 ビットの x86 でホストされるツールを使って、32 ビットの x86 ネイティブな Windows コードがビルドされます。 ただし、64 ビットのコンピューターをお持ちでしょう。 Visual Studio が 64 ビットの Windows オペレーティング システムにインストールされている場合は、64 ビットの x64 でホストされるネイティブ コンパイラとクロス コンパイラ用の開発者コマンド プロンプト ショートカットを追加で使用できます。 x86、x64、または ARM プロセッサ用のコードをビルドするときは、64 ビットの x64 でホストされるツールセットを使うことにより、64 ビットのコードで使用可能なプロセッサとメモリ空間を利点できます。

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>64 ビットでホストされる開発者コマンド プロンプト ショートカットを使用する

Windows 10 でこれらのコマンド プロンプトにアクセスするには、 **[スタート]** メニューでお使いのバージョンの Visual Studio (**Visual Studio 2019** など) のフォルダーを開き、x64 のネイティブ ツールまたはクロス ツールの開発者コマンド プロンプトを選択します。 

![x64 Native Tools コマンド プロンプト](media/x64-native-tools-command-prompt.png "[スタート] メニューの x64 ネイティブツール")

Windows 8 でこれらのコマンド プロンプトにアクセスするには、 **[スタート]** 画面で **[すべてのアプリ]** を開きます。 インストールされているバージョンの Visual Studio の見出しで、 **[Visual Studio]** フォルダーを開きます (古いバージョンの Visual Studio では、 **[Visual Studio Tools]** という名前になっている場合があります)。 さらに前のバージョンの Windows では、 **[スタート]** を選択し、 **[すべてのプログラム]** を展開して、お使いのバージョンの **[Visual Studio]** フォルダーを開きます (古いバージョンの Visual Studio では **[Visual Studio Tools]** )。 詳細については、[開発者コマンド プロンプトのショートカット](building-on-the-command-line.md#developer_command_prompt_shortcuts)に関するトピックを参照してください。

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Vcvarsall.bat を使用して 64 ビットでホストされるビルド アーキテクチャを設定する

vcvarsall.bat コマンド ファイルを実行することにより、任意のネイティブ コンパイラ ツールまたはクロス コンパイラ ツールのビルド構成を、コマンド ラインで使用できます。 このコマンド ファイルでは、既存のコマンド プロンプト ウィンドウで特定のビルド アーキテクチャを有効にするパスと環境変数が構成されます。 具体的な手順については、「[開発者コマンド ファイルの場所](building-on-the-command-line.md#developer_command_file_locations)」をご覧ください。

## <a name="remarks"></a>解説

> [!NOTE]
> Visual Studio の各エディションに含まれる具体的なツールについては、「[さまざまな Visual Studio エディションの Visual C++ ツールおよび機能](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md)」をご覧ください。
>
> Visual Studio IDE を使用して64ビットアプリケーションを作成する方法については、「[方法: visual C++プロジェクトを構成して、64ビット、X64 プラットフォームを対象とする](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)」を参照してください。

Visual Studio インストーラーで C++ ワークロードをインストールすると、x86 と x64 のコードをビルドするため、32 ビットの x86 でホストされるネイティブ コンパイラ ツールとクロス コンパイラ ツールが常にインストールされます。 ユニバーサル Windows プラットフォームのワークロードを含めた場合は、ARM コードをビルドするために x86 でホストされるクロス コンパイラ ツールもインストールされます。 これらのワークロードを 64 ビットの x64 プロセッサにインストールした場合は、x86、x64、ARM のコードをビルドするため、64 ビットのネイティブ コンパイラ ツールとクロス コンパイラ ツールもインストールされます。 32 ビット ツールと 64 ビット ツールでは同じコードが生成されますが、64 ビット ツールでは、プリコンパイル済みヘッダーのシンボルと、プログラム全体の最適化 ([/GL](reference/gl-whole-program-optimization.md) および [/LTCG](reference/ltcg-link-time-code-generation.md)) オプションに対して、より多くのメモリがサポートされます。 32 ビット ツールを使うとメモリ制限に達する場合は、64 ビット ツールを試してください。

## <a name="see-also"></a>参照

[64 ビットの x64 ターゲット用に C++ プロジェクトを構成する](configuring-programs-for-64-bit-visual-cpp.md)<br/>
