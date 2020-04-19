---
title: プロパティ ページの XML 規則ファイル
ms.date: 05/06/2019
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: da9fa72419dc6971e90124b061da48493d7ca017
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303166"
---
# <a name="property-page-xml-rule-files"></a>プロパティ ページの XML 規則ファイル

IDE のプロジェクト プロパティ ページは、VCTargets フォルダー内の XML ファイルで構成されます。 正確なパスは、インストールされている Visual Studio のエディションと製品の言語に依存します。 Visual Studio 2019 Enterprise Edition の英語版のパスは、`%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033` です。 XML ファイルは、規則の名前、カテゴリ、および個々のプロパティ、それらのデータ型、既定値、および表示方法について説明します。 IDE でプロパティを設定すると、新しい値がプロジェクト ファイルに格納されます。

これらのファイルの内部動作と Visual Studio IDE を理解する必要があるシナリオは、(a) カスタム プロパティ ページを作成する場合、または (b) Visual Studio IDE 以外の方法でプロジェクト プロパティをカスタマイズする場合だけです。

最初に、プロジェクトのプロパティ ページを開いてみましょう (**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、[プロパティ] を選択します)。

![Visual Studio C++ プロジェクトのプロパティ](../media/cpp-property-page-2017.png)

**[構成プロパティ]** の下の各ノードは、Rule (規則) と呼ばれます。 Rule は、コンパイラのような 1 つのツールを表すこともありますが、通常はプロパティを持つもの、実行するもの、および何らかの出力を生成するものを指す用語です。 各規則は VCTargets フォルダー内の xml ファイルから設定されます。 たとえば、上記に示した C/C++ 規則は、'cl.xml' によって設定されます。

上記のように、各 Rule にはカテゴリに分類されたプロパティのセットがあります。 Rule の下の各サブ ノードは、カテゴリを表します。 たとえば、C/C++ の下の最適化ノードには、コンパイラ ツールの最適化に関連するすべてのプロパティが含まれています。 プロパティとその値自体が、右側のウィンドウにグリッド形式で表示されます。

cl.xml はメモ帳または任意の XML エディターで開くことができます (下のスナップショットを参照)。 Rule と呼ばれるルート ノードが表示されます。これは、UI に表示されているように、その下で定義されたプロパティの同じリストと、追加の追加のメタデータを持ちます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
```

プロパティ ページの UI の構成プロパティの下には、すべてのノードに対応する 1 つの XML ファイルがあります。 UI 内の規則を追加または削除するには、プロジェクト内の対応する XML ファイルに場所を含めるか削除します。 たとえば、Microsoft.CppBuild.targets (1033 フォルダーより 1 つ上のレベル) に cl.xml を含めるには、次のようにします。

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

すべてのデータの cl.xml を取り除く場合は、次のスケルトンになります。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

次のセクションでは、主要な各要素とそれらに添付することができるメタデータの一部について説明します。

1. **Rule:** 通常は xml ファイル内のルート ノードで、多数の属性を持つことができます。

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Name:** Name 属性は Rule の ID です。 プロジェクトのすべてのプロパティ ページの xml ファイル間で一意である必要があります。

   b. **PageTemplate:** この属性の値は、UI テンプレートのコレクションから選択するために UI によって使用されます。 "tool" テンプレートは、標準のグリッド形式でプロパティをレンダリングします。 この属性のその他の組み込みの値は、"debugger" と "generic" です。 これらの値を指定した結果の UI 形式を確認するには、デバッグ ノードと全般ノードをそれぞれ確認します。 "debugger" ページ テンプレートの UI は、ドロップダウン ボックスを使用して異なるデバッガーのプロパティを切り替えますが、"generic" テンプレートは、Rule ノードの下に複数のカテゴリのサブノードを持つのではなく、さまざまなプロパティのカテゴリをすべて 1 ページに表示します。 この属性は、UI への単なる提案で、xml ファイルは UI に依存しないように設計されています。 UI ごとに異なる目的のためにこの属性を使用することができます。

   c. **SwitchPrefix:** これはコマンドラインで使用されるスイッチのプレフィックスです。 "/" の値は、/ZI、/nologo、/W3 のようなスイッチになります。

   d. **Order:** これは、システム内の他のすべての Rule と比較した、この Rule の相対的な場所で予想される UI クライアント候補に対する提案です。

   e. **xmlns:** これは、標準の XAML 要素です。 3 つの名前空間が一覧表示されます。 これらは、XAML の逆シリアル化クラスの名前空間、XAML スキーマ、およびシステム名前空間にそれぞれ対応しています。

   f. **DisplayName:** Rule ノードのプロパティ ページの UI に表示される名前です。 この値はローカライズされます。 内部のローカライズ ツールの要件により、DisplayName は (Name や SwitchPrefix のような) 属性としてではなく、Rule の子要素として作成されています。 XAML の観点からは、両方とも同じです。 そのため、単に属性にして煩雑さを軽減することも、そのままにしておくこともできます。

   g. **DataSource:** これは、プロジェクト システムにプロパティ値を読み書きする場所およびそのグループ化 (下記参照) を伝える非常に重要なプロパティです。 cl.xml の場合、これらの値は次のとおりです。

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` は、プロジェクト システムに Rule のすべてのプロパティをプロジェクト ファイルまたはプロパティ シート ファイルに書き込む必要があることを伝えます (プロパティ ページを生成するために使用したノードに依存します)。 他の考えられる値は、値を .user ファイルに値を書き込む "UserFile" です。

   - `ItemType="ClCompile"` は、プロパティがこの項目の種類の ItemDefinition メタデータまたは項目メタデータ (後者は、プロパティ ページがソリューション エクスプローラーでファイル ノードから生成された場合のみ) として格納されることを示します。 このフィールドが設定されていない場合、このプロパティは、PropertyGroup の共通プロパティとして書き込まれます。

   - `Label=""` は、プロパティが `ItemDefinition` メタデータとして書き込まれるときに、親 ItemDefinitionGroup のラベルが空になることを示しますます (すべての MSBuild 要素がラベルを持つことができます)。 Visual Studio 2017 以降では、ラベルの付いたグループを使用して、.vcxproj プロジェクト ファイルを移動します。 ほとんどの Rule のプロパティを含むグループは、空の文字列をラベルとして持つことに注意してください。

   - `HasConfigurationCondition="true"` は、現在のプロジェクト構成に対してのみ有効になるように、値に構成条件を添えるようにプロジェクト システムに指示します (条件は、親グループまたは値そのものに添えることができます)。 たとえば、プロジェクト ノードのプロパティ ページを開き、 **[構成プロパティ] > [C/C++ の全般]** の下でプロパティ **Treat Warnings As Error** の値を "Yes" に設定します。 次の値がプロジェクト ファイルに書き込まれます。 親 Itemdefinitiongroup に構成条件が添付されていることに注目してください。

      ```xml
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      この値が、stdafx.h などの特定のファイルのプロパティページで設定されている場合、プロパティ値は、次に示すように、プロジェクトファイルの*stdafx.h*項目の下に書き込まれます。 構成条件がどのようにメタデータ自体に直接添付されているかに注目してください。

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   上記に一覧表示されていない **DataSource** のもう 1 つの属性が、**PersistedName** です。 この属性を使用すると、別の名前を使用しているプロジェクト ファイル内のプロパティを表すことができます。 既定では、この属性はプロパティの**名前**に設定されます。

   個々のプロパティは、その親ルールの DataSource をオーバーライドできます。 その場合、そのプロパティの値の場所は、ルール内の他のプロパティとは異なります。

   h. ここに示されていない、Rule のその他の属性があります (Description、SupportsFileBatching など)。 Rule またはその他の要素に適用可能な属性の完全なセットは、これらの型のドキュメントを参照することで取得できます。 または、`Microsoft.Build.Framework.XamlTypes` アセンブリ内の `Microsoft.Build.Framework .dll` 名前空間内の型でパブリック プロパティを調べることもできます。

   i. **DisplayName**、**PageTemplate**、および **Order** は、ここに存在している UI 関連のプロパティか、そうでない場合は、UI に依存しないデータ モデルです。 これらのプロパティは、プロパティ ページを表示するために使用される任意の UI でほぼ確実に使用されます。 **DisplayName** と **Description** の 2 つのプロパティは、xml ファイル内のほぼすべての要素に存在します。 また、ローカライズされるのはこの 2 つのプロパティだけです (これらの文字列のローカライズについては、以降の記事で説明します)。

1. **Category:** Rule は複数の Category を持つことができます。 xml ファイル内でカテゴリが表示される順序は、カテゴリを同じ順序で表示するための UI への提案です。 たとえば、UI で見られるように、C/C++ ノードの下のカテゴリの順序が、全般、最適化、プリプロセッサというようになっているのは、  cl.xml 内と同じ順序です。 サンプル カテゴリは、次のようになります。

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   上記のスニペットでは、上記で説明した **Name** 属性と **DisplayName** 属性が示されています。 ここでも、**Category** には、上記で使用されていないその他の属性があります。 これらについて知るには、ドキュメントを読むか、ildasm.exe を使用するアセンブリを調べます。

1. **Properties:** これは xml ファイルの本質で、この Rule 内のすべてのプロパティの一覧が含まれています。 各プロパティは、上記の XAML スケルトンで示されている 5 つの可能な型のいずれかを指定できます。 もちろん、これらの型の一部だけをファイル内で指定することもできます。 プロパティは、十分に説明できるように多くの属性を持つことができます。 ここでは、 **Stringproperty**のみについて説明します。 残りは非常に似ています。

    ```xml
    <StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
      <StringProperty.DisplayName>
        <sys:String>Object File Name</sys:String>
      </StringProperty.DisplayName>
      <StringProperty.Description>
        <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
      </StringProperty.Description>
    </StringProperty>
    ```

   スニペット内の属性のほとんどは、前述しました。 新しい属性は、Subtype、Category、および Switch です。

   a. **Subtype** は、**StringProperty** と **StringListProperty** に対してのみ使用可能な属性で、コンテキスト情報を提供します。 たとえば、"file" の値は、プロパティがファイル パスを表すことを示します。 このような文脈情報は、ユーザーがファイルを視覚的に選択できるようにするためのプロパティエディターとして Windows エクスプローラーを提供することで、編集エクスペリエンスを向上させるために使用されます。

   b. **Category:** このプロパティが該当するカテゴリを宣言します。 UI 内の **[出力ファイル]** カテゴリの下で、このプロパティの検索を試みます。

   c. **Switch:** Rule がツールを表す場合 (この場合のコンパイラ ツールなど)、Rule のほとんどのプロパティがビルド時にツールの実行可能ファイルにスイッチとして渡されます。 この属性の値は、使用されるスイッチ リテラルを示します。 上記のプロパティは、そのスイッチが **Fo** にする必要があることを指定します。 このプロパティは、親 Rule で **SwitchPrefix** 属性と組み合わされて、 **/Fo"Debug\"** として実行可能ファイルに渡されます (プロパティ ページの UI で C/C++ のコマンド ラインで表示可能)。

   その他のプロパティの属性は次のとおりです。

   d. **表示:** 何らかの理由でプロパティがプロパティページに表示されないようにする場合は (ただし、ビルド時に使用できる場合もあります)、この属性を false に設定します。

   e. **ReadOnly:** プロパティページでこのプロパティの値の読み取り専用ビューを指定する場合は、この属性を true に設定します。

   f. **IncludeInCommandLine:** プロパティの中には、ビルド時にツールに渡す必要のないものもあります。 この属性を false に設定すると、渡されないようにすることができます。
