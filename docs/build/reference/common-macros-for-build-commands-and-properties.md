---
title: MSBuild のコマンドとプロパティの一般的なマクロ
ms.date: 08/02/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: e2c7fe6f2ea63f2cbd259e4114843fcfc28fcd84
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988330"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>MSBuild のコマンドとプロパティの一般的なマクロ

インストールオプションによっては、visual studio プロジェクトで (MSBuild に基づいて) 何百ものマクロを使用できるようになります。 これらは、既定で設定されている MSBuild プロパティ、または、またはプロジェクト設定で設定された MSBuild プロパティに対応します。 次のマクロは、プロジェクトの **[プロパティ ページ]** ダイアログ ボックス内の、文字列を入力できるどの場所にも使用できます。 これらのマクロでは大文字と小文字が区別されません。

## <a name="view-the-current-properties-and-macros"></a>現在のプロパティとマクロを表示する

現在使用可能なすべてのマクロを表示するには、 **[プロパティページ]** ダイアログの **[VC++ ディレクトリ]** で、プロパティ行の末尾にあるドロップダウン矢印をクリックします。 **[編集]** をクリックし、編集 ダイアログボックスで **[マクロ]** ボタンを選択します。 Visual Studio に表示されているプロパティとマクロの現在のセットが、それぞれの現在の値と共に表示されます。 詳細については、「 [ C++プロジェクトプロパティページの参照](property-pages-visual-cpp.md)」の「**ユーザー定義の値の指定**」セクションを参照してください。

![VC + + マクロボタン](../media/vcppdir_libdir_macros.png "マクロメニュー")

## <a name="list-of-common-macros"></a>一般的なマクロの一覧

次の表は、使用可能なマクロのよく使用されるサブセットを示しています。ここには他に多くのものがあります。 **[マクロ]** ダイアログにアクセスして、プロジェクトのすべてのプロパティとその現在の値を確認します。 MSBuild プロパティ定義がどのように作成され、.props、.targets、および .vcxproj ファイル内でマクロとして使用されるかについて詳しくは、「[MSBuild プロパティ](/visualstudio/msbuild/msbuild-properties)」を参照してください。

|マクロ|説明|
|-----------|-----------------|
|**$(Configuration)**|現在のプロジェクト構成の名前 ("Debug" など)。|
|**$(DevEnvDir)**|Visual Studio のインストール ディレクトリ (ドライブ + パスで定義) です。最後に円記号 (\\) が含まれます。|
|**$(FrameworkDir)**|.NET Framework をインストールしたディレクトリです。|
|**$(FrameworkSDKDir)**|.NET Framework をインストールしたディレクトリです。 .NET Framework は、Visual Studio 一部としてインストールされている場合も、個別にインストールされている場合もあります。|
|**$(FrameworkVersion)**|Visual Studio が使用する .NET Framework のバージョンです。 **$(FrameworkDir)** と組み合わせると、Visual Studio が使用する .NET Framework のバージョンへの完全なパスになります。|
|**$(FxCopDir)**|fxcop.cmd ファイルへのパスです。 Fxcop ファイルは、Visual Studio のすべてのエディションと共にインストールされるわけではありません。|
|**$(IntDir)**|中間ファイルに指定されたディレクトリへのパスです。 相対パスの場合、中間ファイルは、プロジェクトディレクトリに追加されたこのパスに移ります。 このパスの末尾にはスラッシュが必要です。 この値は、**中間ディレクトリ**プロパティの値に解決されます。 **$ (OutDir)** を使用してこのプロパティを定義しないでください。|
|**$(OutDir)**|出力ファイルのディレクトリへのパスです。 相対パスの場合、出力ファイルはプロジェクトディレクトリに追加されたこのパスに移ります。 このパスの末尾にはスラッシュが必要です。 これは、**出力ディレクトリ**プロパティの値に解決されます。 **$ (Intdir)** を使用してこのプロパティを定義しないでください。|
|**$(Platform)**|現在のプロジェクト プラットフォームの名前 (例: "Win32") です。|
|**$ (PlatformShortName)**|現在のアーキテクチャの短い名前 ("x86"、"x64" など)。|
|**$(ProjectDir)**|プロジェクトのディレクトリ (ドライブ + パスで定義) です。最後に円記号 (\\) が含まれます。|
|**$(ProjectExt)**|プロジェクトのファイル拡張子。 ファイル拡張子の前にピリオド '.' が付きます。|
|**$(ProjectFileName)**|プロジェクトのファイル名 (基本名 + ファイル拡張子で定義) です。|
|**$(ProjectName)**|プロジェクトの基本名です。|
|**$(ProjectPath)**|プロジェクトの絶対パス名 (ドライブ + パス + 基本名 + ファイル拡張子で定義) です。|
|**$ (PublishDir)**|発行先の出力場所。末尾に円記号 '\\' が含まれています。 既定値は **$ (OutDir) app. publish\\** フォルダーです。|
|**$(RemoteMachine)**|[デバッグ] プロパティ ページで **Remote Machine** プロパティの値を設定します。 詳細については、「 [C または C++ デバッグ構成のプロジェクト設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 」を参照してください。|
|**$(RootNameSpace)**|アプリケーションを含む名前空間 (定義されている場合) です。|
|**$(SolutionDir)**|ソリューションのディレクトリ (ドライブ + パスで定義) です。最後に円記号 (\\) が含まれます。 IDE でソリューションをビルドする場合にのみ定義されます。|
|**$(SolutionExt)**|ソリューションのファイル拡張子です。 ファイル拡張子の前にピリオド '.' が付きます。 IDE でソリューションをビルドする場合にのみ定義されます。|
|**$(SolutionFileName)**|ソリューションのファイル名 (基本名 + ファイル拡張子で定義) です。 IDE でソリューションをビルドする場合にのみ定義されます。|
|**$(SolutionName)**|ソリューションの基本名です。 IDE でソリューションをビルドする場合にのみ定義されます。|
|**$(SolutionPath)**|ソリューションの絶対パス名 (ドライブ + パス + 基本名 + ファイル拡張子で定義) です。 IDE でソリューションをビルドする場合にのみ定義されます。|
|**$(TargetDir)**|ビルドのプライマリ出力ファイルのディレクトリ (ドライブ + パスで定義) です。最後に円記号 (\\) が含まれます。|
|**$(TargetExt)**|ビルドのプライマリ出力ファイルのファイル拡張子。 ファイル拡張子の前にピリオド '.' が付きます。|
|**$(TargetFileName)**|ビルドのプライマリ出力ファイルの名前 (基本名 + ファイル拡張子で定義) です。|
|**$(TargetName)**|ビルドのプライマリ出力ファイルの基本名です。|
|**$(TargetPath)**|ビルドのプライマリ出力ファイルの絶対パス名 (ドライブ + パス + 基本名 + ファイル拡張子で定義) です。|
|**$(VCInstallDir)**|Visual Studio インストールの C++ コンテンツを格納するディレクトリ。 このプロパティには、対象となる Microsoft C++ (MSVC) ツールセットのバージョンが含まれていますが、ホストの Visual Studio とは異なる場合があります。 たとえば、`$(PlatformToolset) = v140`でビルドする場合、 **$ (VCInstallDir)** には Visual Studio 2015 インストールのパスが含まれます。|
|**$(VSInstallDir)**|Visual Studio をインストールしたディレクトリです。 このプロパティにはターゲットの Visual Studio ツールセットのバージョンが含まれますが、ホストの Visual C++ とは異なることがあります。 たとえば、 `$(PlatformToolset) = v110`を設定してビルドした場合、 **$(VSInstallDir)** には Visual Studio 2012 インストールへのパスが含まれます。|
|**$(WebDeployPath)**|Web 配置のルートから、プロジェクト出力が存在するディレクトリへの相対パスです。|
|**$(WebDeployRoot)**|**\<localhost>** への絶対パスです。 たとえば、c:\inetpub\wwwroot などです。|

## <a name="obsolete-macros"></a>古いマクロ

C++ のビルド システムは、Visual Studio 2008 と Visual Studio 2010 の間で大幅に変更されました。 以前のプロジェクトの種類で使用されていた多くのマクロは、新しいものに変更されています。 これらのマクロは使用されなくなったか、あるいは 1 つまたは複数の同等のプロパティまたは[項目メタデータ マクロ ](/visualstudio/msbuild/itemmetadata-element-msbuild)( **%(** _名前_ **)** ) 値に置き換えられました。 "移行済み" とマークされたマクロは、プロジェクトの移行ツールによって更新できます。 そのマクロを含むプロジェクトが Visual Studio 2008 以前から Visual Studio 2010 に移行された場合、Visual Studio はそのマクロを同等の現在のマクロに変換します。 新しいバージョンの Visual Studio は、プロジェクトを Visual Studio 2008 以前から新しいプロジェクトの種類に変換できません。 2 つの手順でこれらのプロジェクトを変換する必要があります。まず Visual Studio 2010 に変換し、Visual Studio の新しいバージョンにその結果を変換します。 詳細については、「[Overview of potential upgrade issues](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)」 (アップグレードの潜在的な問題の概要) を参照してください。

|マクロ|説明|
|-----------|-----------------|
|**$(InputDir)**|(移行済み)入力ファイルのディレクトリ (ドライブ + パスとして定義されています)。末尾に円記号 '\\' が含まれています。 プロジェクトが入力の場合、このマクロは **$(ProjectDir)** と同等です。|
|**$(InputExt)**|(移行済み)入力ファイルのファイル拡張子。 ファイル拡張子の前にピリオド '.' が付きます。 プロジェクトが入力の場合、このマクロは **$(ProjectExt)** と同等です。 ソース ファイルの場合、これは **%(Extension)** です。|
|**$(InputFileName)**|(移行済み)入力ファイルのファイル名 (基本名 + ファイル拡張子で定義)。 プロジェクトが入力の場合、このマクロは **$(ProjectFileName)** と同等です。 ソース ファイルの場合、これは **%(Identity)** です。|
|**$(InputName)**|(移行済み)入力ファイルの基本名。 プロジェクトが入力の場合、このマクロは **$(ProjectName)** と同等です。 ソース ファイルの場合、これは **%(Filename)** です。|
|**$(InputPath)**|(移行済み)入力ファイルの絶対パス名 (ドライブ + パス + 基本名 + ファイル拡張子で定義)。 プロジェクトが入力の場合、このマクロは **$(ProjectPath)** と同等です。 ソース ファイルの場合、これは **%(FullPath)** です。|
|**$(ParentName)**|このプロジェクト項目を含む項目の名前です。 これは、親フォルダー名またはプロジェクト名になります。|
|**$(SafeInputName)**|有効なクラス名としてのファイル名です。ファイル拡張子は除きます。 このプロパティには、正確に等しいものはありません。|
|**$(SafeParentName)**|有効な名前形式で指定された、直接の親の名前です。 たとえば、フォームは .resx ファイルの親です。 このプロパティには、正確に等しいものはありません。|
|**$(SafeRootNamespace)**|プロジェクト ウィザードでコードが追加される名前空間の名前です。 この名前空間名には、有効な C++ 識別子で許可される文字列だけが含まれます。 このプロパティには、正確に等しいものはありません。|

## <a name="see-also"></a>参照

[Visual Studio プロジェクト- C++ ](../creating-and-managing-visual-cpp-projects.md)\
[ビジュアルC++移植およびアップグレードガイド](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[アップグレード時の潜在的な問題の概要](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
