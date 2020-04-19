---
title: '方法: MSBuild プロジェクトでビルドイベントを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060071"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>方法: MSBuild プロジェクトでビルドイベントを使用する

ビルドイベントは、ビルド処理の特定の段階で MSBuild が実行するコマンドです。 ビルド*前*のイベントは、ビルドが開始される前に発生します。リンク*前*のイベントは、リンクステップが開始される前に発生します。ビルド*後*イベントは、ビルドが正常に終了した後に発生します。 ビルドイベントは、関連付けられたビルドステップが発生した場合にのみ発生します。 たとえば、リンクステップが実行されていない場合、リンク前イベントは発生しません。

3つの各ビルドイベントは、実行されるコマンド要素 (`<Command>`) と、 **MSBuild**がビルドイベントを実行するときに表示される message 要素 (`<Message>`) によって、項目定義グループで表されます。 各要素は省略可能です。同じ要素を複数回指定した場合は、最後の出現が優先されます。

ビルドイベントが実行されるかどうか`<`を示すために、オプション*のビルド内*の要素 (*ビルドイベント*`UseInBuild>`) をプロパティグループに指定できます。 *ビルド内*の要素の内容の値は、 **true**または**false**のいずれかになります。 既定では、対応する*ビルド内*の要素がに`false`設定されていない限り、ビルドイベントが実行されます。

次の表に、各ビルドイベント XML 要素の一覧を示します。

|XML 要素|説明|
|-----------------|-----------------|
|`PreBuildEvent`|このイベントは、ビルドが開始される前に実行されます。|
|`PreLinkEvent`|このイベントは、リンクステップが開始される前に実行されます。|
|`PostBuildEvent`|このイベントは、ビルドが完了した後に実行されます。|

次の表に、各*ビルド*要素の一覧を示します。

|XML 要素|説明|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|*ビルド前*のイベントを実行するかどうかを指定します。|
|`PreLinkEventUseInBuild`|*リンク前*のイベントを実行するかどうかを指定します。|
|`PostBuildEventUseInBuild`|*ビルド後*のイベントを実行するかどうかを指定します。|

## <a name="example"></a>例

次の例は、チュートリアルで作成した myproject ファイルの Project 要素の内部に[追加できます。MSBuild を使用してC++プロジェクト](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)を作成する。 *ビルド前*のイベントによって、メイン .cpp のコピーが作成します。*リンク前*のイベントによって、メイン .obj のコピーが作成します。*ビルド後*のイベントによって、myproject のコピーが作成されます。 リリース構成を使用してプロジェクトをビルドすると、ビルドイベントが実行されます。 プロジェクトがデバッグ構成を使用してビルドされている場合、ビルドイベントは実行されません。

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>関連項目

[コマンド ラインでの MSBuild - C++](msbuild-visual-cpp.md)<br/>
[チュートリアル: MSBuild を使用した C++ プロジェクトの作成](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
