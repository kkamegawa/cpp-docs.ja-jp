---
title: .vcxproj. ファイルをフィルター処理する
ms.date: 09/25/2019
description: Visual Studio C++プロジェクトのフィルターファイルを使用して、ソリューションエクスプローラー内のファイルのカスタム論理フォルダーを定義します
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: ee44bf3d1cbe06d6c007ed8976ec384a456efca5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686924"
---
# <a name="vcxprojfilters-files"></a>.vcxproj. ファイルをフィルター処理する

*フィルター*ファイル (\*) は、ルートプロジェクトフォルダーに配置されている MSBuild 形式の XML ファイルです。 ここでは、**ソリューションエクスプローラー**内の論理フォルダーに入るファイルの種類を指定します。 次の図では、 *.cpp*ファイルは **[ソースファイル]** ノードにあります。 *.h*ファイルは **[ヘッダーファイル]** ノードの下にあり *、.ico*ファイルと *.rc*ファイルは **[リソースファイル]** の下にあります。 この配置は、フィルターファイルによって制御されます。

![ソリューションエクスプローラーの論理フォルダー](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>カスタムフィルターファイルを作成する

このファイルは、Visual Studio によって自動的に作成されます。 デスクトップアプリケーションの場合、定義済みの論理フォルダー (フィルター) は、**ソースファイル**、**ヘッダーファイル**、および**リソースファイル**です。 UWP などの他のプロジェクトの種類には、既定のフォルダーのセットが異なる場合があります。 Visual Studio では、既知のファイルの種類が各フォルダーに自動的に割り当てられます。 カスタム名またはカスタムファイルの種類を保持するフィルターを使用してフィルターを作成する場合は、プロジェクトのルートフォルダーまたは既存のフィルターの下に独自のフィルターファイルを作成できます。 (**参照**と**外部依存関係**は、フィルター処理に関与しない特殊なフォルダーです)。

## <a name="example"></a>例

次の例は、前に示した例のフィルターファイルを示しています。 これにはフラットな階層があります。つまり、入れ子になった論理フォルダーはありません。 `UniqueIdentifier` ノードは省略可能です。 これにより、Visual Studio オートメーションインターフェイスがフィルターを検索できるようになります。 `Extensions` も省略可能です。 新しいファイルがプロジェクトに追加されると、ファイル拡張子が一致する最上位のフィルターに追加されます。 特定のフィルターにファイルを追加するには、フィルターを右クリックし、 **[新しい項目の追加]** を選択します。

`ClInclude` ノードが含まれている `ItemGroup` は、プロジェクトの初回起動時に作成されます。 独自の .vcxproj ファイルを生成する場合は、すべてのプロジェクト項目にフィルターファイルのエントリが含まれていることを確認してください。 `ClInclude` ノードの値は、ファイル拡張子に基づく既定のフィルター処理よりも優先されます。 Visual Studio を使用して新しい項目をプロジェクトに追加すると、IDE によってフィルターファイルに個々のファイルエントリが追加されます。 ファイルの拡張子を変更すると、フィルターは自動的に再割り当てされません。 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

入れ子になった論理フォルダーを作成するには、次に示すように、フィルター `ItemGroup` 内のすべてのノードを宣言します。 各子ノードは、最上位の親への完全論理パスを宣言する必要があります。 次の例では、空の `ParentFilter` は、後のノードで参照されるため、宣言する必要があります。

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

