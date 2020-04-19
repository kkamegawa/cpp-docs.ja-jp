---
title: コマンドラインからC++ Microsoft ツールセットを使用する
description: Visual Studio IDE の外にあるコマンド ラインから Microsoft C++ コンパイラ ツールチェーン (MSVC) を使用します。
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051492"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>コマンドラインからC++ Microsoft ツールセットを使用する

Visual Studio に含まれているツールを使用し、コマンド ラインで C と C++ のアプリケーションをビルドできます。 Microsoft C++ (MSVC) コンパイラツールセットは、VISUAL Studio IDE を含まないスタンドアロンパッケージとしてダウンロードすることもできます。

## <a name="download-and-install-the-tools"></a>ツールをダウンロードしてインストールする

Visual Studio とC++ワークロードがインストールされている場合は、すべてのコマンドラインツールを使用できます。 と Visual Studio をインストールC++する方法の詳細については、「 [visual studio でサポートをインストールC++ ](vscpp-step-0-installation.md)する」を参照してください。 コマンドラインツールセットのみが必要な場合は、 [Visual Studio のビルドツール](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)をダウンロードします。 ダウンロードした実行可能ファイルを実行すると、Visual Studio インストーラーが更新され、実行されます。 開発にC++必要なツールのみをインストールするには、 **[ C++ビルドツール]** ワークロードを選択します。 オプションのライブラリとツールセットを選択して、**インストールの詳細**を含めることができます。 Visual Studio 2015 または2017ツールセットを使用してコードをビルドするには、省略可能な MSVC v140 または MSVC v141 ビルドツールを選択します。 選択が終わったら、 **[インストール]** を選択します。

## <a name="how-to-use-the-command-line-tools"></a>コマンド ライン ツールの使用方法

Visual Studio インストーラーでいずれかの C++ ワークロードを選択すると、Visual Studio *プラットフォーム ツールセット*がインストールされます。 プラットフォームツールセットには、特定のC++ Visual Studio バージョンの C およびツールがすべて含まれています。 これらのツールには、C++ C/コンパイラ、リンカー、アセンブラー、およびその他のビルドツール、および一致するライブラリが含まれています。 これらのツールはすべてコマンドラインで使用できます。 また、Visual Studio IDE によって内部的に使用されます。 X86、x64、ARM、ARM64 の各ターゲット用のコードをビルドするための、x86 でホストされる、および x64 でホストされる個別のコンパイラとツールがあります。 特定のホストやターゲット ビルド アーキテクチャに対するそれぞれのツール セットは、その独自のディレクトリに保存されています。

ツールが正しく動作するには、特定の環境変数をいくつか設定する必要があります。 これらの変数は、ツールをパスに追加し、インクルードファイル、ライブラリファイル、および SDK の場所を設定するために使用されます。 このような環境変数をかん単に設定する目的で、インストーラーにより、インストール中、カスタマイズされた*コマンド ファイル*またはバッチ ファイルが作成されます。 次のいずれかのコマンドファイルを実行して、特定のホストとターゲットのビルドアーキテクチャ、Windows SDK バージョン、およびプラットフォームのツールセットを設定できます。 便宜上、インストーラーによってスタートメニューにショートカットも作成されます。 ショートカットでは、ホストとターゲットの特定の組み合わせに対して、これらのコマンドファイルを使用して開発者コマンドプロンプトウィンドウを開始します。 これらのショートカットによって、必要なすべての環境変数が設定され、使用できるようになります。

必要な環境変数は、インストールと選択したビルドアーキテクチャに固有です。 また、製品の更新プログラムまたはアップグレードによって変更される場合もあります。 そのため、環境変数を自分で設定するのではなく、インストールされているコマンドプロンプトのショートカットまたはコマンドファイルを使用することをお勧めします。 詳細については、「[コマンドラインビルドのパスと環境変数を設定](setting-the-path-and-environment-variables-for-command-line-builds.md)する」を参照してください。

インストールされているツールセット、コマンドファイル、およびショートカットは、コンピューターのプロセッサと、インストール時に選択したオプションによって異なります。 X86 および x64 コードをビルドする x86 でホストされるツールとクロスツールは、常にインストールされます。 64ビットの Windows を使用している場合は、x86 および x64 コードをビルドする x64 でホストされるツールとクロスツールもインストールされます。 オプションC++のユニバーサル Windows プラットフォームツールを選択した場合は、ARM と ARM64 コードをビルドする x86 および x64 ツールもインストールされます。 その他のワークロードによって追加のツールがインストールされることもあります。

## <a name="developer_command_prompt_shortcuts"></a> 開発者コマンド プロンプト ショートカット

コマンド プロンプト ショートカットは、[スタート] メニューのバージョン固有の Visual Studio フォルダーにインストールされます。 次は、基本的なコマンド プロンプト ショートカットとそれによりサポートされるビルド アーキテクチャを一覧にまとめたものです。

- **開発者コマンド プロンプト** - 32 ビット x86 ネイティブ ツールを使用して 32 ビット x86 ネイティブ コードをビルドするように環境を設定します。
- **x86 Native Tools コマンド プロンプト** - 32 ビット x86 ネイティブ ツールを使用して 32 ビット x86 ネイティブ コードをビルドするように環境を設定します。
- **x64 Native Tools コマンド プロンプト** - 64 ビット x64 ネイティブ ツールを使用して 64 ビット x64 ネイティブ コードをビルドするように環境を設定します。
- **x86_x64 Cross Tools コマンド プロンプト** - 32 ビット x86 ネイティブ ツールを使用して 64 ビット x64 ネイティブ コードをビルドするように環境を設定します。
- **x64_x86 Cross Tools コマンド プロンプト** - 64 ビット x64 ネイティブ ツールを使用して 32 ビット x86 ネイティブ コードをビルドするように環境を設定します。

::: moniker range=">= vs-2019"

[スタート] メニューのフォルダーとショートカット名は、インストールされている Visual Studio のバージョンによって異なります。 設定した場合は、インストールの**ニックネーム**にも依存します。 たとえば、Visual Studio 2019 をインストールし、それに*最新*のニックネームを付けたとします。 開発者コマンドプロンプトのショートカットの名前は、 **Visual Studio 2019**という名前のフォルダーで、 **VS 2019 (最新) の開発者コマンドプロンプト**という名前になっています。

::: moniker-end
::: moniker range="= vs-2017"

[スタート] メニューのフォルダーとショートカット名は、インストールされている Visual Studio のバージョンによって異なります。 設定した場合は、インストールの**ニックネーム**にも依存します。 たとえば、Visual Studio 2017 をインストールし、それに*最新*のニックネームを付けたとします。 開発者コマンドプロンプトのショートカットの名前は、 **Visual Studio 2017**という名前のフォルダーで、 **VS 2017 (最新) の開発者コマンドプロンプト**という名前になっています。

::: moniker-end
::: moniker range="< vs-2017"

[スタート] メニューのフォルダーとショートカット名は、インストールされている Visual Studio のバージョンによって異なります。 たとえば、Visual Studio 2015 をインストールしたとします。 開発者コマンドプロンプトのショートカットには、 **VS 2015 の開発者コマンドプロンプト**という名前が付けられています。

::: moniker-end

### <a name="developer_command_prompt"></a> 開発者コマンド プロンプト ウィンドウを開くには

1. デスクトップで、Windows の **[スタート]** メニューを開き、スクロールしてお使いのバージョンの Visual Studio (たとえば、**Visual Studio 2019**) のフォルダーを見つけて開きます。

1. フォルダーで、お使いのバージョンの Visual Studio の **[開発者コマンド プロンプト]** を選択します。 このショートカットにより、32 ビット x86 ネイティブ ツールの既定のビルド アーキテクチャを使用して 32 ビット x86 ネイティブ コードをビルドする開発者コマンド プロンプト ウィンドウが起動します。 既定以外のビルド アーキテクチャを使用する場合、いずれかのネイティブまたはクロス ツール コマンド プロンプトを選択し、ホストおよびターゲット アーキテクチャを指定します。

開発者コマンドプロンプトを開くより高速な方法については、デスクトップの検索ボックスに「*開発者コマンドプロンプト*」と入力してください。 次に、必要な結果を選択します。

## <a name="developer_command_file_locations"></a> 開発者コマンド ファイルの場所

既存のコマンドプロンプトウィンドウでビルド環境を設定する場合は、インストーラーによって作成されたコマンドファイルの1つを使用できます。 新しいコマンドプロンプトウィンドウで環境を設定することをお勧めします。 後で同じコマンドウィンドウで環境を切り替えることはお勧めしません。

::: moniker range=">= vs-2019"

コマンドファイルの場所は、インストールした Visual Studio のバージョン、およびインストール時に選択した内容によって異なります。 Visual Studio 2019 では、64ビットシステムの通常のインストール場所は \\Program Files (x86)\\Microsoft Visual Studio\\2019\\*edition*にあります。 *エディション*は、Community、Professional、Enterprise、buildtools、または指定した別のニックネームです。

::: moniker-end
::: moniker range="= vs-2017"

コマンドファイルの場所は、インストールした Visual Studio のバージョン、およびインストール時に選択した内容によって異なります。 Visual Studio 2017 では、64ビットシステムの通常のインストール場所は \\Program Files (x86)\\Microsoft Visual Studio\\2017\\*edition*にあります。 *エディション*は、Community、Professional、Enterprise、buildtools、または指定した別のニックネームです。

::: moniker-end
::: moniker range="< vs-2017"

コマンドファイルの場所は、Visual Studio のバージョンとインストールディレクトリによって異なります。 Visual Studio 2015 では、通常のインストール場所は \\Program Files (x86)\\Microsoft Visual Studio 14.0 にあります。

::: moniker-end

主要な開発者コマンドプロンプトコマンドファイル VsDevCmd は、Common7\\Tools サブディレクトリにあります。 パラメーターが指定されていない場合は、x86 ネイティブツールを使用して32ビットの x86 コードをビルドするように環境を設定します。

::: moniker range=">= vs-2017"

特定のビルドアーキテクチャを設定するために、さらに多くのコマンドファイルを使用できます。 使用できるコマンドファイルは、インストールした Visual Studio のワークロードとオプションによって異なります。 Visual Studio 2017 および Visual Studio 2019 では、VC\\の補助\\ビルドサブディレクトリにあります。

::: moniker-end
::: moniker range="< vs-2017"

特定のビルドアーキテクチャを設定するために、さらに多くのコマンドファイルを使用できます。 使用できるコマンドファイルは、インストールした Visual Studio のワークロードとオプションによって異なります。 Visual Studio 2015 では、これらは VC、VC\\bin、VC\\bin\\*アーキテクチャ*サブディレクトリにあります。*アーキテクチャ*は、ネイティブまたはクロスコンパイラオプションの1つです。

::: moniker-end

これらのコマンド ファイルにより既定のパラメーターが設定され、VsDevCmd.bat が呼び出されて指定のビルド アーキテクチャ環境が設定されます。 一般的なインストールに含まれるコマンド ファイル:

|コマンド ファイル|ホストおよびターゲット アーキテクチャ|
|---|---|
|**vcvars32.bat**| 32 ビット x86 ネイティブ ツールを使用し、32 ビット x86 コードをビルドします。|
|**vcvars64.bat**| 64 ビット x64 ネイティブ ツールを使用し、64 ビット x64 コードをビルドします。|
|**vcvarsx86_amd64.bat**| 32 ビット x86 ネイティブ クロス ツールを使用し、64 ビット x64 コードをビルドします。|
|**vcvarsamd64_x86.bat**| 64 ビット x64 ネイティブ クロス ツールを使用し、32 ビット x86 コードをビルドします。|
|**vcvarsx86_arm.bat**| 32 ビット x86 ネイティブ クロス ツールを使用し、ARM コードをビルドします。|
|**vcvarsamd64_arm.bat**| 64 ビット x64 ネイティブ クロス ツールを使用し、ARM コードをビルドします。|
|**vcvarsall.bat**| パラメーターを使用して、ホストとターゲットのアーキテクチャ、Windows SDK、およびプラットフォームの選択肢を指定します。 サポートされているオプションの一覧が必要な場合、 **/help** パラメーターを使用して呼び出します。|

> [!CAUTION]
> vcvarsall.bat ファイルとその他の Visual Studio コマンド ファイルはコンピューターによって異なります。 vcvarsall.bat ファイルが見つからない場合や破損している場合でも、別のコンピューターのファイルを使用して置き換えないでください。 Visual Studio インストーラーを再実行し、不足しているファイルを置換します。
>
> vcvarsall.bat ファイルは、バージョンによっても異なります。 以前のバージョンの Visual Studio も入っているコンピューターに現行版の Visual Studio をインストールする場合、同じコマンド プロンプト ウィンドウで異なるバージョンの vcvarsall.bat または別の Visual Studio コマンド ファイルを実行しないでください。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>既存のコマンド ウィンドウで開発者ツールを使用する

既存のコマンド ウィンドウで特定のビルド アーキテクチャを指定する最も簡単な方法は、vcvarsall.bat ファイルを使用することです。 環境変数を設定するには、vcvarsall を使用して、ネイティブの32ビットまたは64ビットのコンパイルのコマンドラインを構成します。 引数を使用すると、x86、x64、ARM、または ARM64 プロセッサへのクロスコンパイルを指定できます。 Microsoft Store、ユニバーサル Windows プラットフォーム、または Windows デスクトップのプラットフォームを対象にすることができます。 使用する Windows SDK を指定し、プラットフォームツールセットのバージョンを選択することもできます。

引数を指定せずに使用する場合、vcvarsall は、32ビットの Windows デスクトップターゲットで現在の x86 ネイティブコンパイラを使用するように環境変数を構成します。 引数を追加して、ネイティブまたはクロスコンパイラツールを使用するように環境を構成することができます。 コンピューターにインストールされていない構成または使用できない構成を指定すると、vcvarsall によってエラーメッセージが表示されます。

### <a name="vcvarsall-syntax"></a>vcvarsall 構文

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*アーキテクチャ*<br/>
この任意の引数では、使用するホストおよびターゲット アーキテクチャが指定されます。 *アーキテクチャ*が指定されていない場合は、既定のビルド環境が使用されます。 以下の引数がサポートされています。

|*アーキテクチャ*|コンパイラ|ホスト コンピューターのアーキテクチャ|ビルド出力 (ターゲット) のアーキテクチャ|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 ビット ネイティブ|x86、x64|x86|
|**x86\_amd64** または **x86\_x64**|x64 on x86 クロス|x86、x64|X64|
|**x86_arm**|ARM on x86 クロス|x86、x64|ARM|
|**x86_arm64**|ARM64 on x86 クロス|x86、x64|ARM64|
|**amd64** または **x64**|x64 64 ビット ネイティブ|X64|X64|
|**amd64\_x86** または **x64\_x86**|x86 on x64 クロス|X64|x86|
|**amd64\_arm** または **x64\_arm**|ARM on x64 クロス|X64|ARM|
|**amd64\_arm64** または **x64\_arm64**|ARM64 on x64 クロス|X64|ARM64|

*platform_type*<br/>
この任意の引数では、プラットフォームの種類として **[ストア]** または **[uwp]** を指定できます。 既定では、デスクトップまたはコンソール アプリをビルドするように環境が設定されます。

*winsdk_version*<br/>
任意で、使用する Windows SDK のバージョンが指定されます。 既定では、インストールされた日付が最も新しい Windows SDK が使用されます。 Windows SDK のバージョンを指定するには、**10.0.10240.0** など、完全な Windows 10 SDK 番号を使用するか、**8.1** と指定して Windows 8.1 SDK を使用します。

*vcversion*<br/>
任意で、使用する Visual Studio コンパイラ ツールセットを指定します。 既定では、現在の Visual Studio コンパイラ ツールセットを使用するように環境が設定されます。

::: moniker range=">= vs-2019"

Visual Studio 2019 コンパイラツールセットの特定のバージョンを指定するには **、-vcvars_ver = 14.2; yyyyy**を使用します。

Visual Studio 2017 コンパイラツールセットの最新バージョンを指定するには、 **-vcvars_ver = 14.16**を使用します。

::: moniker-end
::: moniker range="= vs-2017"

Visual Studio 2017 コンパイラツールセットの最新バージョンを指定するには、 **-vcvars_ver = 14.16**を使用します。

Visual Studio 2017 コンパイラツールセットの特定のバージョンを指定するには **、-vcvars_ver = 14.1 x yyyyy**を使用します。

::: moniker-end

Visual Studio 2015 コンパイラツールセットを指定するには **、-vcvars_ver = 14.0**を使用します。

#### <a name="vcvarsall"></a>既存のコマンドプロンプトウィンドウでビルド環境を設定するには

1. コマンド プロンプトで、CD コマンドを使用し、Visual Studio インストール ディレクトリに作業ディレクトリを変更します。 次に、CD をもう一度使用し、構成固有のコマンド ファイルが含まれるサブディレクトリに作業ディレクトリを変更します。 Visual Studio 2019 および Visual Studio 2017 の場合は、 *VC\\補助\\ビルド*サブディレクトリを使用します。 Visual Studio 2015 の場合は、 *VC*サブディレクトリを使用します。

1. 優先開発者環境のコマンドを入力します。 たとえば、最新の Windows SDK と Visual Studio コンパイラツールセットを使用して、64ビットプラットフォームで UWP の ARM コードをビルドするには、次のコマンドラインを使用します。

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>独自のコマンド プロンプト ショートカットを作成する

::: moniker range=">= vs-2019"

開発者コマンドプロンプトのショートカットの [プロパティ] ダイアログを開き、使用するコマンドターゲットを確認します。 たとえば、**x64 Native Tools Command Prompt for VS 2019** ショートカットのターゲットは次のようになります。

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

開発者コマンドプロンプトのショートカットの [プロパティ] ダイアログを開き、使用するコマンドターゲットを確認します。 たとえば、 **VS 2017 の x64 Native Tools コマンドプロンプト**ショートカットのターゲットは次のようになります。

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

開発者コマンドプロンプトのショートカットの [プロパティ] ダイアログを開き、使用するコマンドターゲットを確認します。 たとえば、 **VS2015 x64 Native Tools コマンドプロンプト**ショートカットのターゲットは次のようになります。

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

このアーキテクチャ固有のバッチ ファイルにより *architecture* パラメーターが設定され、vcvarsall.bat が呼び出されます。 これらのバッチファイルには、vcvarsall .bat に渡すのと同じオプションを渡すことができます。または、vcvarsall を直接呼び出すこともできます。 独自のコマンド ショートカットのパラメーターを指定するには、それを二重引用符でコマンドの終わりに追加します。 たとえば、最新の Windows SDK を使用して、64ビットプラットフォームで UWP の ARM コードをビルドするショートカットを次に示します。 以前のコンパイラツールセットを使用するには、バージョン番号を指定します。 ショートカットで次のようなコマンド ターゲットを使用します。

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Visual Studio のインストールディレクトリを反映するようにパスを調整します。 vcvarsall.bat ファイルには、特定のバージョン番号に関する追加情報があります。

## <a name="command-line-tools"></a>コマンド ライン ツール

コマンドプロンプトで C/C++プロジェクトをビルドするために、Visual Studio には次のコマンドラインツールが用意されています。

[CL](reference/compiling-a-c-cpp-program.md)<br/>
コンパイラ (cl.exe) は、ソース コード ファイルをアプリ、ライブラリ、および DLL にコンパイルおよびリンクするために使用します。

[リンク](reference/linking.md)<br/>
リンカー (link.exe) は、コンパイルされたオブジェクト ファイルおよびライブラリをアプリおよび DLL にリンクするために使用します。

[MSBuild](msbuild-visual-cpp.md)<br/>
MSBuild (msbuild.exe) とプロジェクト ファイル (.vcxproj) を使用し、ビルドを構成し、ツールセットを間接的に呼び出します。 これは、Visual Studio IDE で プロジェクトの **[ビルド]** または **[ソリューションのビルド]** コマンドを実行するのと同じです。 コマンドラインから MSBuild を実行することは高度なシナリオであり、一般的には推奨されません。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
**/Build**や **/Clean**などのコマンドラインスイッチと組み合わせて devenv (devenv.exe) を使用して、Visual Studio IDE を表示せずに特定のビルドコマンドを実行します。 一般的に、msbuild を直接使用することをお勧めします。これは、Visual Studio が MSBuild の複雑さを処理できるようにするためです。

[NMAKE](reference/nmake-reference.md)<br/>
Windows で NMAKE (nmake.exe) を使用し、従来のメイクファイルに基づいて C++ プロジェクトをビルドします。

コマンドラインを使用してビルドする場合、F1 キーを使用してインスタントヘルプを表示することはできません。 代わりに、検索エンジンを使用して警告、エラー、メッセージに関する情報を取得できます。あるいは、オフラインのヘルプ ファイルを使用できます。 [Docs.microsoft.com](https://docs.microsoft.com/cpp/)で検索を使用するには、ページの上部にある検索ボックスを使用します。

## <a name="in-this-section"></a>このセクションの内容

これらの記事では、コマンドラインでアプリを作成する方法と、コマンドラインビルド環境をカスタマイズする方法を説明します。 64ビットツールセットを使用する方法と、x86、x64、ARM、ARM64 の各プラットフォームを対象とする方法を紹介します。 また、コマンドラインビルドツール MSBuild と NMAKE の使用方法についても説明します。

[チュートリアル: コマンドラインでC++のネイティブプログラムのコンパイル](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
コマンドラインでプログラムをC++作成してコンパイルする方法を示す例を示します。

[チュートリアル: コマンド ラインでの C プログラムのコンパイル](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
C プログラミング言語で書かれたプログラムをコンパイルする方法について説明します。

[チュートリアル: コマンドラインC++での/cli プログラムのコンパイル](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
.NET Framework を使用する C++/CLI プログラムを作成およびコンパイルする方法について説明します。

[チュートリアル: コマンドラインC++での/cx プログラムのコンパイル](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Windows ランタイムを使用する C++/CX プログラムを作成およびコンパイルする方法について説明します。

[コマンドラインビルドのパスと環境変数を設定する](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
32ビットまたは64ビットのツールセットを使用して、x86、x64、ARM、ARM64 の各プラットフォームを対象とするように環境変数を設定する方法について説明します。

[NMAKE リファレンス](reference/nmake-reference.md)<br/>
NMAKE.EXE (Microsoft Program Maintenance Utility) について説明する記事へのリンクがあります。

[コマンド ラインでの MSBuild - C++](msbuild-visual-cpp.md)<br/>
コマンド ラインから msbuild.exe を使用する方法について説明する記事へのリンクがあります。

## <a name="related-sections"></a>関連項目

[/MD、/MT、/LD (ランタイムライブラリの使用)](reference/md-mt-ld-use-run-time-library.md)<br/>
デバッグ バージョンまたはリリース バージョンのランタイム ライブラリを使用するための、コンパイラ オプションの使用方法について説明します。

[C/C++コンパイラオプション](reference/compiler-options.md)<br/>
C と C++ のコンパイラ オプションおよび CL.exe に関する記事へのリンクがあります。

[MSVC リンカーオプション](reference/linker-options.md)<br/>
リンカー オプションおよび LINK.exe に関する記事へのリンクがあります。

[追加の MSVC ビルド ツール](reference/c-cpp-build-tools.md)<br/>
Visual Studio に含まれている C/C++ ビルド ツールへのリンクがあります。

## <a name="see-also"></a>関連項目

[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)
