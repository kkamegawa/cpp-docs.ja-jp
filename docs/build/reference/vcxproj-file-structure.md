---
title: .vcxproj ファイルと .props ファイルの構造
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: a24349980e9395257f20fcfcc0987883060a7c1d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303138"
---
# <a name="vcxproj-and-props-file-structure"></a>.vcxproj ファイルと .props ファイルの構造

[MSBuild](../msbuild-visual-cpp.md) は、Visual Studio の既定のプロジェクト システムです。Visual C++ で **[ファイル]** 、 > [新しいプロジェクト]**を選ぶと、MSBuild プロジェクトが作成されて、その設定が拡張子** の XML プロジェクト ファイルに格納されます。 プロジェクト ファイルでは .props ファイルと .targets ファイルをインポートすることもでき、これらのファイルにも設定を格納できます。 ほとんどの場合、プロジェクト ファイルを手動で編集する必要はありません。MSBuild のことをよく理解していない場合は、手動で編集しないようにしてください。 プロジェクトの設定を変更するには、可能な限り、Visual Studio のプロパティ ページを使う必要があります (「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」を参照してください)。 ただし、プロジェクト ファイルまたはプロパティ シートを手動で変更することが必要になる場合があります。 そのような場合のために、この記事ではファイルの構造に関する基本的な情報を提供します。

**重要:**

.vcxproj ファイルを手動で編集する場合は、以下のことに注意してください。

1. ファイルの構造は、この記事に記載されている所定のフォームに従う必要があります。

1. Visual Studio C++ プロジェクト システムは現在、プロジェクト項目でのワイルドカードをサポートしていません。 たとえば、次のような記述はサポートされていません。

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. 現在、Visual Studio C++ プロジェクト システムは、プロジェクト項目パスでのマクロをサポートしていません。 たとえば、次のような記述はサポートされていません。

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "サポートされていない" とは、IDE において、すべての操作に対してマクロが機能することが保証されないという意味です。 異なる構成の値を変更しないマクロは機能しますが、項目が別のフィルターまたはプロジェクトに移動された場合は保存されない可能性があります。 異なる構成で値を変えるマクロは問題を引き起こします。IDE では、さまざまなプロジェクト構成でプロジェクト項目のパスが異なることが想定されていないためです。

1. **[プロジェクトのプロパティ]** ダイアログで編集したときに、プロジェクトのプロパティが正しく追加、削除、変更されるためには、ファイルにプロジェクト構成ごとに異なるグループが含まれており、条件が次の形式になっている必要があります。

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. 各プロパティは、プロパティ規則ファイル内で指定されている正しいラベルを持つグループにおいて指定されている必要があります。 詳しくは、「[プロパティ ページの XML 規則ファイル](property-page-xml-files.md)」をご覧ください。

## <a name="vcxproj-file-elements"></a>.vcxproj ファイルの要素

任意のテキスト エディターまたは XML エディターを使って、.vcxproj ファイルの内容を調べることができます。 Visual Studio のソリューション エクスプローラーでプロジェクトを右クリックし、 **[プロジェクトのアンロード]** 、 **[Foo.vcxproj の編集]** の順に選ぶと表示されます。

最初に注目する点は、最上位の要素が特定の順序で表示されることです。 例 :

- ほとんどのプロパティ グループおよび項目定義グループは、Microsoft.Cpp.Default.props のインポートの後に出現します。

- すべてのターゲットは、ファイルの最後にインポートされます。

- 複数のプロパティ グループがあり、それぞれが一意のラベルを持ち、特定の順序で出現します。

MSBuild は順次評価モデルに基づいているため、プロジェクト ファイル内の要素の順序が非常に重要です。  インポートされたすべての .props および .targets ファイルを含むプロジェクト ファイルが、複数のプロパティ定義で構成されている場合、最後の定義が前の定義をオーバーライドします。 次の例では、値 "xyz" はコンパイル中に設定されます。これは、MSBUild エンジンが評価中に最後にそれを検出したためです。

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

次のスニペットに、最小限の .vcxproj ファイルを示します。 Visual Studio によって生成されるすべての .vcxproj ファイルには、これらの最上位 MSBuild 要素がこの順序で含まれます (ただし、最上位要素の複数のコピーが含まれる場合があります)。 なお、`Label` 属性は任意のタグであり、Visual Studio によって編集のための目印としてのみ使われます。それ以外の機能はありません。

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

以下のセクションでは、これらの各要素の目的と、その順序の理由について説明します。

### <a name="project-element"></a>Project 要素

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` はルート ノードです。 この要素は、使われる MSBuild のバージョンを指定し、このファイルが MSBuild.exe に渡されたときに実行する既定のターゲットも指定します。

### <a name="projectconfigurations-itemgroup-element"></a>ItemGroup の ProjectConfigurations 要素

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` には、プロジェクトの構成の説明が含まれます。 たとえば、Debug|Win32、Release|Win32、Debug|ARM などです。 プロジェクトの多くの設定は、特定の構成に固有です。 たとえば、リリース ビルドでは最適化プロパティを設定しても、デバッグ ビルドでは設定しないことがあります。

`ProjectConfigurations` 項目グループは、ビルド時には使われません。 Visual Studio IDE はプロジェクトを読み込むために必要です。 この項目グループを .props ファイルに移動して、.vcxproj ファイルにインポートすることができます。 ただし、その際に、構成の追加または削除が必要になった場合は、.props ファイルを手動で編集する必要があります。IDE を使うことはできません。

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 要素

次のスニペットでは、プロジェクトの構成を示します。 この例では、"Debug|x64" が構成の名前です。 プロジェクトの構成の名前は、$(Configuration)|$(Platform) という形式になっている必要があります。 ProjectConfiguration ノードは、Configuration と Platform の 2 つのプロパティを持つことができます。 構成がアクティブになると、ここで指定した値がこれらのプロパティに自動的に設定されます。

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE は、すべての ProjectConfiguration 項目で使われている Configuration と Platform の値の任意の組み合わせに対して、プロジェクトの構成が見つかるものと想定しています。 これは、多くの場合、この要件を満たすためにプロジェクトには意味のないプロジェクト構成が存在する可能性があることを意味します。 たとえば、プロジェクトに次のような構成があるものとします。

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

この場合、"Special 32-bit Optimization" は x64 に対しては意味がありませんが、次のような構成も存在する必要があります。

- Debug|x64

- Retail|x64

- Special 32-bit Optimization|x64

**ソリューション構成マネージャー**では、任意の構成に対してビルドと配置のコマンドを無効にできます。

### <a name="globals-propertygroup-element"></a>PropertyGroup の Globals 要素

```xml
<PropertyGroup Label="Globals" />
```

`Globals` には、ProjectGuid、RootNamespace、ApplicationType/ApplicationTypeRevision などのプロジェクト レベルの設定が含まれます。 最後の 2 つは、多くの場合、ターゲット OS を定義します。 参照およびプロジェクト項目は現在は条件を持つことができないため、プロジェクトがターゲットにできる OS は 1 つだけです。 これらのプロパティは、通常、プロジェクト ファイル内の他の場所ではオーバーライドされません。 このグループは構成に依存しないので、普通、プロジェクト ファイル内に存在する Globals グループは 1 つのみです。

### <a name="microsoftcppdefaultprops-import-element"></a>Import の Microsoft.Cpp.default.props 要素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props** プロパティ シートは Visual Studio に付属しており、変更できません。 プロジェクトの既定の設定が含まれます。 既定値は、ApplicationType によって異なる場合があります。

### <a name="configuration-propertygroup-elements"></a>PropertyGroup の Configuration 要素

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` プロパティ グループには、添付された構成条件 (`Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"` など) があり、構成ごとに 1 つずつの、複数のコピーが提供されます。 このプロパティ グループは、特定の構成に対して設定されるプロパティをホストします。 構成プロパティは PlatformToolset を含み、**Microsoft.Cpp.props** でのシステム プロパティ シートのインクルードも制御します。 たとえば、プロパティ `<CharacterSet>Unicode</CharacterSet>` を定義した場合、システム プロパティ シート **microsoft.Cpp.unicodesupport.props** がインクルードされます。 **Microsoft.Cpp.props** を調べると、`<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` という行が見つかります。

### <a name="microsoftcppprops-import-element"></a>Import の Microsoft.Cpp.props 要素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Microsoft.Cpp.props** プロパティ シートでは、コンパイラの最適化と警告レベルのプロパティや、MIDL ツールの TypeLibraryName プロパティなど、多くのツール固有プロパティの既定値が (直接的に、またはインポートを介して) 定義されています。 また、すぐ上にあるプロパティ グループで定義されている構成プロパティに基づいて、さまざまなシステム プロパティ シートをインポートします。

### <a name="extensionsettings-importgroup-element"></a>ImportGroup の ExtensionSettings 要素

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` グループには、ビルドのカスタマイズの一部であるプロパティ シートのインポートが含まれます。 ビルドのカスタマイズは、最大 3 つのファイル (.targets ファイル、.props ファイル、.xml ファイル) によって定義されます。 このインポート グループには、.props ファイルのインポートが含まれています。

### <a name="propertysheets-importgroup-elements"></a>ImportGroup の PropertySheets 要素

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` グループには、ユーザー プロパティ シートのインポートが含まれます。 これらは、Visual Studio のプロパティ マネージャー ビューを通じて追加するプロパティ シートです。 これらのインポートは列記されている順序が重要であり、プロパティ マネージャーに反映されます。 通常、プロジェクト ファイルには、この種のインポート グループの複数のインスタンス (プロジェクト構成ごとに 1 つずつ) が含まれます。

### <a name="usermacros-propertygroup-element"></a>PropertyGroup の UserMacros 要素

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` には、ユーザーが変数として作成し、ビルド プロセスのカスタマイズに使われるプロパティが含まれます。 たとえば、カスタム出力パスを定義するためのユーザー マクロを $(CustomOutputPath) として定義し、それを使って他の変数を定義できます。 このプロパティ グループは、そのようなプロパティを格納します。 Visual Studio では、Visual C++ が構成用のユーザー マクロをサポートしていないため、このグループはプロジェクト ファイル内に作成されないことに注意してください。 ユーザー マクロは、プロパティ シートでサポートされています。

### <a name="per-configuration-propertygroup-elements"></a>構成ごとの PropertyGroup 要素

```xml
<PropertyGroup />
```

このプロパティ グループには、すべてのプロジェクト構成の構成ごとに 1 つずつ、複数のインスタンスがあります。 各プロパティ グループには、1 つの構成条件が添付されている必要があります。 いずれかの構成がない場合、 **[プロジェクトのプロパティ]** ダイアログは正しく動作しません。 上記のプロパティ グループとは異なり、このプロパティ グループにはラベルはありません。 このグループには、プロジェクトの構成レベルの設定が含まれます。 これらの設定は、指定された項目グループの一部であるすべてのファイルに適用されます。 ビルドのカスタマイズ項目定義のメタデータはここで初期化されます。

この PropertyGroup は `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` の後に指定する必要があり、その前にラベルがない他の PropertyGroup は使用できません (それ以外の場合、プロジェクトプロパティの編集は正常に機能しません)。

### <a name="per-configuration-itemdefinitiongroup-elements"></a>構成ごとの ItemDefinitionGroup 要素

```xml
<ItemDefinitionGroup />
```

項目の定義が含まれます。 これらは、ラベルのない構成ごとの PropertyGroup 要素と同じ条件規則に従う必要があります。

### <a name="itemgroup-elements"></a>ItemGroup 要素

```xml
<ItemGroup />
```

プロジェクト内の項目 (ソース ファイルなど) が含まれます。 プロジェクト項目 (つまり、規則の定義によってプロジェクト項目として扱われる項目の種類) に対しては、条件はサポートされていません。

メタデータでは、構成ごとに構成の条件が必要です (すべて同じであっても)。 例 :

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual Studio C++ プロジェクト システムは現在、プロジェクト項目でのワイルドカードをサポートしていません。

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

現在、Visual Studio C++ プロジェクト システムは、プロジェクト項目でのマクロをサポートしていません。

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

参照は ItemGroup で指定され、次のような制限があります。

- 参照は、条件をサポートしていません。

- 参照のメタデータは、条件をサポートしていません。

### <a name="microsoftcpptargets-import-element"></a>Import の Microsoft.Cpp.targets 要素

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

ビルドやクリーンアップなど、Visual C++ のターゲットを (直接、またはインポートを介して) 定義します。

### <a name="extensiontargets-importgroup-element"></a>ImportGroup の ExtensionTargets 要素

```xml
<ImportGroup Label="ExtensionTargets" />
```

このグループには、ビルド カスタマイズのターゲット ファイルのインポートが含まれます。

## <a name="impact-of-incorrect-ordering"></a>正しくない順序の影響

Visual Studio IDE の動作は、プロジェクト ファイルが上で説明した順序になっていることに依存します。 たとえば、プロパティ ページでプロパティの値を定義すると、IDE は一般に、ラベルが空であるプロパティ グループにそのプロパティの定義を配置します。 これにより、システム プロパティ シートで取り込まれた既定値が、ユーザー定義の値によって確実にオーバーライドされます。 同様に、ターゲット ファイルは、それより前に定義されているプロパティを使用し、一般にそれ自体ではプロパティを定義していないため、最後にインポートされます。 同じように、ユーザー プロパティ シートはシステム プロパティ シートの後でインポートされます (**Microsoft.Cpp.props** によってインクルードされます)。 これにより、ユーザーはシステム プロパティ シートによって取り込まれたすべての既定値をオーバーライドできます。

.vcxproj ファイルがこのレイアウトに従っていない場合、意図したビルド結果にならない可能性があります。 たとえば、誤ってユーザー定義のプロパティ シートの後でシステム プロパティ シートをインポートした場合、ユーザーの設定はシステム プロパティ シートによってオーバーライドされます。

IDE のデザイン時のエクスペリエンスも、要素の正しい順序にある程度依存します。 たとえば、.vcxproj ファイルに `PropertySheets` インポート グループがない場合、IDE は、ユーザーが**プロパティ マネージャー**で作成した新しいプロパティ シートを配置する場所を決定できない可能性があります。 その結果、ユーザーのシートがシステムのシートによってオーバーライドされる場合があります。 IDE によって使われるヒューリスティックは、.vcxproj ファイルのレイアウトの小さな不整合は許容できますが、この記事でこれまでに示した構造から外れないようにすることを強くお勧めします。

## <a name="how-the-ide-uses-element-labels"></a>IDE が要素のラベルを使用する方法

IDE では、全般プロパティ ページで **UseOfAtl** プロパティを設定すると、プロジェクト ファイルの Configuration プロパティ グループに書き込まれますが、同じプロパティ ページの **TargetName** プロパティは、ラベルのない構成ごとのプロパティ グループに書き込まれます。 Visual Studio は、プロパティ ページの xml ファイルで、各プロパティを書き込む場所についての情報を取得します。 **[全般]** プロパティ ページでは (Visual Studio 2019 Enterprise Edition の英語版を使っているとした場合)、そのファイルは `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` です。 プロパティ ページの XML 規則ファイルでは、Rule とそのすべてのプロパティに関する静的な情報が定義されています。 そのような情報の 1 つは、書き込み先ファイル (その値が書き込まれるファイル) での Rule プロパティの優先位置です。 優先位置は、プロジェクト ファイルの要素の Label 属性によって指定されます。

## <a name="property-sheet-layout"></a>プロパティ シートのレイアウト

次の XML スニペットは、プロパティ シート (.props) ファイルの最小限のレイアウトです。 .vcxproj ファイルに似ており、.props の要素の機能は、これまでの説明から推測できるものです。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

独自のプロパティ シートを作成するには、VCTargets フォルダー内の .props ファイルの 1 つをコピーし、目的に応じて変更します。 Visual Studio 2019 Enterprise Edition の場合、VCTargets の既定のパスは `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` です。

## <a name="see-also"></a>参照

[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)<br/>
[プロパティ ページの XML ファイル](property-page-xml-files.md)
