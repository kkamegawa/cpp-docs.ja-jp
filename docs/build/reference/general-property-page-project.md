---
title: '[全般] プロパティ ページ (プロジェクト)'
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: eb172e7bd76816458a0efff7b053d136f52076ab
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166759"
---
# <a name="general-property-page-project"></a>[全般] プロパティ ページ (プロジェクト)

::: moniker range=">=vs-2019"

このトピックは、Windows の Visual Studio プロジェクトに適用されます。 Linux プロジェクトについては、 [linux C++のプロパティページのリファレンス](../../linux/prop-pages-linux.md)を参照してください。 CMake プロジェクトについては、「 [Visual Studio での Cmake プロジェクト](../cmake-projects-in-visual-studio.md)」を参照してください。 Android プロジェクトについては、「[一般的なC++プロジェクトのプロパティ (android)](/cpp/cross-platform/general-android-prop-page)」を参照してください。 Android メイクファイルプロジェクトについては、「[一般的C++なプロジェクトのプロパティ (android メイクファイル)](/cpp/cross-platform/general-makefile-android-prop-page) 」を参照してください。

ソリューションエクスプローラーでプロジェクトノードを右クリックし、 **[プロパティ]** を選択すると、左側のウィンドウの **[構成プロパティ]** ノードの下の **[全般]** プロパティページに、次のプロパティが表示されます。

- **出力ディレクトリ**

   リンカーなどのツールが、ビルド処理で作成されるすべての最終出力ファイルを置くディレクトリを指定します。 通常は、リンカー、ライブラリアン、BSCMake などのツールの出力があります。 既定では、このプロパティはマクロ $(SolutionDir)$(Configuration)\ によって指定されるディレクトリです。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>」を参照してください。

- **中間ディレクトリ**

   コンパイラなどのツールが、ビルド処理で作成されるすべての中間ファイルを置くディレクトリを指定します。 通常は、C/C++ コンパイラ、MIDL、リソース コンパイラなどのツールの出力があります。 既定では、このプロパティはマクロ $(Configuration)\ によって指定されるディレクトリです。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>」を参照してください。

- **ターゲット名**

   このプロジェクトで生成されるファイル名を指定します。 既定では、このプロパティはマクロ $(ProjectName) によって指定されるファイル名です。

- **[構成の種類]**

  選択できる構成ファイルの種類は以下のとおりです。

  - **アプリケーション (.exe)**

     リンカーのツールセット (C/C++ コンパイラ、MIDL、リソース コンパイラ、リンカー、BSCMake、XML Web サービス プロキシ ジェネレーター、カスタム ビルド、ビルド前のイベント、リンク前のイベント、ビルド後のイベント) を表示します。

  - **ダイナミック ライブラリ (.dll)**

     リンカーのツールセットを表示し、/DLL リンカー オプションを指定し、_WINDLL 定義を CL に追加します。

  - **メイクファイル**

     メイクファイルのツールセット (NMake) を表示します。

  - **スタティック ライブラリ (.lib)**

     ライブラリアンのツールセット (リンカーの代わりにライブラリアンを使用し、XML Web サービス プロキシ ジェネレーターがないこと以外はリンカーのツールセットと同じ) を表示します。

  - **Utility**

     ユーティリティのツールセット (MIDL、カスタム ビルド、ビルド前のイベント、ビルド後のイベント) を表示します。

  プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>」を参照してください。

- **Windows SDK バージョン**

   Windows ターゲット プラットフォームに対して、プロジェクトで必要な Windows SDK のバージョンを指定します。 Visual Studio インストーラーを使用して C++ のワークロードをインストールすると、Windows SDK の必要な部分もインストールされます。 コンピューターに他の Windows SDK バージョンがある場合は、インストールされている SDK ツールの各バージョンがドロップダウン リストに表示されます。

   Windows 7 または Windows Vista を対象とするには、値 **8.1** を使用します。Windows SDK 8.1 はこれらのプラットフォームと下位互換性があるためです。 さらに、targetver.h に **_WIN32_WINNT** の適切な値を定義する必要があります。 Windows 7 では、これは 0x0601 になります。 「[WINVER および _WIN32_WINNT の変更](../../porting/modifying-winver-and-win32-winnt.md)」を参照してください。

   Visual Studio に含まれている Windows XP プラットフォーム ツールセットをインストールすれば、ライブラリの現在のバージョンを使用して Windows XP および Windows 2003 Server のプロジェクトをビルドできます。 このプラットフォーム ツールセットを入手して使用する方法については、「[Windows XP 用プログラムの構成](../configuring-programs-for-windows-xp.md)」を参照してください。 プラットフォーム ツールセットの変更に関する詳細については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

- **プラットフォームのツールセット**

   プロジェクトの対象を別のバージョンの Visual C++ のライブラリおよびコンパイラにすることができます。 Visual Studio C++プロジェクトは、visual studio によってインストールされた既定のツールセット、または以前のバージョンの visual studio によってインストールされたツールセット (Windows XP で実行可能な実行可能ファイルを作成するツールセットを含む) のいずれかをターゲットにすることができます。 プラットフォーム ツールセットの変更に関する詳細については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

- **C++言語標準**

   使用する言語標準を指定します。 既定値は、/std:c++14 です。 C++17 の機能を使用するには、/std:c++17 を指定します。または、C++20 またはその他の試験的な機能を使用するには、/std:c++latest を指定します。 詳細については、「 [/std (言語の標準バージョンの指定)](std-specify-language-standard-version.md) 」を参照してください。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2015 および Visual Studio 2017 で、**ソリューションエクスプローラー**でプロジェクトノードを右クリックし、 **[プロパティ]** を選択すると、左側のウィンドウの **[構成プロパティ]** ノードの下の **[全般]** プロパティページに、次の2つのプロパティセクションが表示されます。

- 全般

- [プロジェクトの既定値]

## <a name="general"></a>全般

- **ターゲット プラットフォーム**

   プロジェクトが実行されるプラットフォームを指定します。 Windows、Android、または iOS などです。 値 **Windows 10** は、プロジェクトがユニバーサル Windows プラットフォームを対象としていることを意味します。 Windows の以前のバージョンを対象としている場合は、バージョンは一覧に表示されず、このフィールドの値は単に "**Windows**” と表示されます。 これは、プロジェクトを作成するときに設定される読み取り専用フィールドです。

- **ターゲットプラットフォームのバージョン (Visual Studio 2015)**

   プロジェクトを実行できるプラットフォームの最小バージョンを指定します。 このプロパティは、プロジェクトの種類でサポートされている場合にのみ表示されます。 アプリが最新の Windows SDK バージョンの機能を利用できるにもかかわらず、おそらく機能の一部が失われているためこれらの機能を使用せずに以前のバージョンで実行している場合、これら 2 つのプロパティの値は異なる可能性があります。 このような場合は、コードで実行時に実行しているプラットフォームのバージョンを確認する必要があります。古いバージョンのプラットフォームでは使用できない機能は使用しないでください。

   プロジェクトC++システムでは、このオプションは強制されません。 これは、C# や JavaScript など、他の言語との一貫性のため、およびプロジェクトを使用する他のユーザーのガイドとして含められています。 最小バージョンで使用できない機能を使用する場合、Visual C++ ではエラーは生成されません。

- **Windows SDK のバージョン (Visual Studio 2017)**

   Windows ターゲット プラットフォームに対して、プロジェクトで必要な Windows SDK のバージョンを指定します。 Visual Studio インストーラーを使用して C++ のワークロードをインストールすると、Windows SDK の必要な部分もインストールされます。 コンピューターに他の Windows SDK バージョンがある場合は、インストールされている SDK ツールの各バージョンがドロップダウン リストに表示されます。

   Windows 7 または Windows Vista を対象とするには、値 **8.1** を使用します。Windows SDK 8.1 はこれらのプラットフォームと下位互換性があるためです。 さらに、targetver.h に **_WIN32_WINNT** の適切な値を定義する必要があります。 Windows 7 では、これは 0x0601 になります。 「[WINVER および _WIN32_WINNT の変更](../../porting/modifying-winver-and-win32-winnt.md)」を参照してください。

   Visual Studio に含まれている Windows XP プラットフォーム ツールセットをインストールすれば、ライブラリの現在のバージョンを使用して Windows XP および Windows 2003 Server のプロジェクトをビルドできます。 このプラットフォーム ツールセットを入手して使用する方法については、「[Windows XP 用プログラムの構成](../configuring-programs-for-windows-xp.md)」を参照してください。 プラットフォーム ツールセットの変更に関する詳細については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

- **出力ディレクトリ**

   リンカーなどのツールが、ビルド処理で作成されるすべての最終出力ファイルを置くディレクトリを指定します。 通常は、リンカー、ライブラリアン、BSCMake などのツールの出力があります。 既定では、このプロパティはマクロ $(SolutionDir)$(Configuration)\ によって指定されるディレクトリです。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>」を参照してください。

- **中間ディレクトリ**

   コンパイラなどのツールが、ビルド処理で作成されるすべての中間ファイルを置くディレクトリを指定します。 通常は、C/C++ コンパイラ、MIDL、リソース コンパイラなどのツールの出力があります。 既定では、このプロパティはマクロ $(Configuration)\ によって指定されるディレクトリです。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>」を参照してください。

- **ターゲット名**

   このプロジェクトで生成されるファイル名を指定します。 既定では、このプロパティはマクロ $(ProjectName) によって指定されるファイル名です。

- **ターゲットの拡張子**

   このプロジェクトで生成されるファイル名拡張子 (.exe、.dll など) を指定します。

- **消去時に削除する拡張子**

   **[ビルド]** メニューの **[消去]** を選択すると、プロジェクトの構成がビルドされる中間ディレクトリからファイルが削除されます。 このプロパティで指定された拡張子を持つファイルは、 **[消去]** の実行時またはリビルドの実行時に削除されます。 ビルド システムでは、中間ディレクトリでこれらの拡張子を持つファイルのほかに、置かれている場所に関係なく、(.obj ファイルなどの中間出力を含む) 既存のビルドの出力も削除します。 ワイルドカード文字を指定できます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>」を参照してください。

- **ビルド ログ ファイル**

   プロジェクトをビルドしたときに作成されるログ ファイルの既定の場所を変更できます。 既定の場所は、マクロ $(IntDir)$(MSBuildProjectName).log によって指定されます。

   プロジェクト マクロを使用して、ディレクトリの場所を変更できます。 「[ビルドコマンドとプロパティの一般的なマクロ](common-macros-for-build-commands-and-properties.md)」を参照してください。

- **プラットフォームのツールセット**

   プロジェクトの対象を別のバージョンの Visual C++ のライブラリおよびコンパイラにすることができます。 Visual Studio C++プロジェクトは、visual studio によってインストールされた既定のツールセット、または以前のバージョンの visual studio によってインストールされたツールセット (Windows XP で実行可能な実行可能ファイルを作成するツールセットを含む) のいずれかをターゲットにすることができます。 プラットフォーム ツールセットの変更に関する詳細については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

- **マネージド インクリメンタル ビルドを有効にする**

   マネージド プロジェクトの場合、これによりアセンブリの生成時に、外部からの可視性の検出が可能になります。 マネージド プロジェクトへの変更が他のプロジェクトから見えない場合、依存プロジェクトはリビルドされません。 これにより、マネージド プロジェクトを含むソリューションのビルド時間を大幅に短縮できます。

## <a name="project-defaults"></a>[プロジェクトの既定値]

[プロジェクトの既定値] セクションのプロパティは、変更できる既定のプロパティを表します。 これらのプロパティの定義は、*インストール ディレクトリ* (\VC\VCProjectDefaults) の .props ファイル内にあります。

- **[構成の種類]**

  選択できる構成ファイルの種類は以下のとおりです。

  - **アプリケーション (.exe)**

     リンカーのツールセット (C/C++ コンパイラ、MIDL、リソース コンパイラ、リンカー、BSCMake、XML Web サービス プロキシ ジェネレーター、カスタム ビルド、ビルド前のイベント、リンク前のイベント、ビルド後のイベント) を表示します。

  - **ダイナミック ライブラリ (.dll)**

     リンカーのツールセットを表示し、/DLL リンカー オプションを指定し、_WINDLL 定義を CL に追加します。

  - **メイクファイル**

     メイクファイルのツールセット (NMake) を表示します。

  - **スタティック ライブラリ (.lib)**

     ライブラリアンのツールセット (リンカーの代わりにライブラリアンを使用し、XML Web サービス プロキシ ジェネレーターがないこと以外はリンカーのツールセットと同じ) を表示します。

  - **Utility**

     ユーティリティのツールセット (MIDL、カスタム ビルド、ビルド前のイベント、ビルド後のイベント) を表示します。

  プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>」を参照してください。

- **MFC の使用法**

   MFC プロジェクトが MFC DLL に静的にリンクするか動的にリンクするかを指定します。 非 MFC プロジェクトでは **[標準 Windows ライブラリを使用する]** を選択して、MFC の使用時にさまざまな Win32 ライブラリにリンクできます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>」を参照してください。

- **文字セット**

   _UNICODE または _MBCS を設定する必要があるかどうかを定義します。 該当する場合は、リンカーのエントリ ポイントにも影響します。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>」を参照してください。

- **共通言語ランタイム サポート**

   [/clr](clr-common-language-runtime-compilation.md) コンパイラ オプションが使用されます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>」を参照してください。

- **.NET Framework 対象バージョン**

   マネージド プロジェクトでは、ターゲットにする .NET Framework バージョンを指定します。

- **プロジェクト全体の最適化**

   [/GL](gl-whole-program-optimization.md) コンパイラ オプションと [/LTCG](ltcg-link-time-code-generation.md) リンカー オプションを指定します。 既定では、これはデバッグ構成に対しては無効で、リテール構成では有効になっています。

- **Windows ストア アプリのサポート**

   このプロジェクトが Windows ランタイム (ユニバーサル Windows プラットフォーム) アプリをサポートしているかどうかを指定します。 詳細については、「[/ZW (Windows ランタイムのコンパイル)](zw-windows-runtime-compilation.md)」および Windows デベロッパー センターを参照してください。

::: moniker-end

## <a name="see-also"></a>参照

[C++プロジェクトプロパティページのリファレンス](property-pages-visual-cpp.md)
