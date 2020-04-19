---
title: プロジェクト ファイルの例
ms.date: 08/19/2019
helpviewer_keywords:
- .vcxproj files
- C++ projects, project file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
ms.openlocfilehash: 0eb87c3f3ba8bd60f0944ad673d22f9b84e070a5
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630764"
---
# <a name="project-files"></a>プロジェクト ファイル

Visual C++ Studio のプロジェクトファイルは XML ベースのファイルで、.vcxproj というファイル名拡張子を持ち、プロジェクトをC++ビルドするために必要な情報が含まれています。 プロジェクトファイルは、". props" または ".targets" という拡張子を持つさまざまなプロジェクトファイルをインポートすることに注意してください。 これらのファイルには追加のビルド情報が含まれており、それ自体が他の "props" ファイルまたは ".targets" ファイルを参照している場合があります。 ファイルのパス内のマクロ (たとえば `$(VCTargetsPath)`) は、Visual Studio のインストールに依存しています。 これらのマクロと "..." ファイルと ".targets" ファイルの詳細については、「 [VC++ ディレクトリ」プロパティページ](vcpp-directories-property-page.md)を参照してください。 [Visual Studio でコンパイラとビルドプロパティを設定C++ ](../working-with-project-properties.md)する方法と、[ビルドコマンドとプロパティの一般的なマクロ](common-macros-for-build-commands-and-properties.md)に関するページを参照してください。

## <a name="example"></a>例

::: moniker range=">=vs-2019"

次のサンプル .vcxproj ファイルは、[**新しいプロジェクト**] ダイアログボックスの [ **Windows デスクトップウィザード**] を選択して生成されたものです。 プロジェクト ファイルを処理するには、コマンド ラインで msbuild.exe ツールを使用するか、IDE で **Build** コマンドを使用します。 (必要なソース ファイルとヘッダー ファイルが指定されていないため、このサンプルを処理することはできません。)プロジェクト ファイルの XML 要素の詳細については、[プロジェクト ファイルのスキーマ参照](/visualstudio/msbuild/msbuild-project-file-schema-reference)に関するページを参照してください。

::: moniker-end

::: moniker range="<=vs-2017"

次のサンプルの .vcxproj ファイルは、**[新しいプロジェクト]** ダイアログ ボックスで **[Win32 コンソール アプリケーション]** を指定して生成されました。 プロジェクト ファイルを処理するには、コマンド ラインで msbuild.exe ツールを使用するか、IDE で **Build** コマンドを使用します。 (必要なソース ファイルとヘッダー ファイルが指定されていないため、このサンプルを処理することはできません。)プロジェクト ファイルの XML 要素の詳細については、[プロジェクト ファイルのスキーマ参照](/visualstudio/msbuild/msbuild-project-file-schema-reference)に関するページを参照してください。

::: moniker-end


>[!NOTE]
> Visual Studio 2017 以前のプロジェクトでは、を`pch.h`に`stdafx.h` 、 `pch.cpp`を`stdafx.cpp`に変更します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup Label="ProjectConfigurations">
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <PropertyGroup Label="Globals">
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>
    <Keyword>Win32Proj</Keyword>
    <RootNamespace>SomeProjName</RootNamespace>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <WholeProgramOptimization>true</WholeProgramOptimization>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings">
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <LinkIncremental>true</LinkIncremental>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <LinkIncremental>false</LinkIncremental>
  </PropertyGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <ClCompile>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <WarningLevel>Level3</WarningLevel>
      <MinimalRebuild>true</MinimalRebuild>
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>
      <Optimization>Disabled</Optimization>
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
    </Link>
  </ItemDefinitionGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <ClCompile>
      <WarningLevel>Level3</WarningLevel>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>
      <Optimization>MaxSpeed</Optimization>
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
      <FunctionLevelLinking>true</FunctionLevelLinking>
      <IntrinsicFunctions>true</IntrinsicFunctions>
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
      <EnableCOMDATFolding>true</EnableCOMDATFolding>
      <OptimizeReferences>true</OptimizeReferences>
    </Link>
  </ItemDefinitionGroup>
  <ItemGroup>
    <None Include="ReadMe.txt" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="pch.h" />
    <ClInclude Include="targetver.h" />
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="SomeProjName.cpp" />
    <ClCompile Include="pch.cpp">
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>
    </ClCompile>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets">
  </ImportGroup>
</Project>
```

## <a name="see-also"></a>関連項目

[Visual Studio プロジェクト - C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)
