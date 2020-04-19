---
title: Visual Studio で Linux CMake プロジェクトを作成および構成する
description: Visual Studio で Linux CMake プロジェクトを作成、構成、編集、コンパイルする方法
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 9c6a60162c2dbbab8e348b27d1987d7f1001bee0
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416086"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Linux CMake プロジェクトの作成と構成

::: moniker range="vs-2015"

Linux サポートは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 で新しい Linux CMake プロジェクトを作成するには:

1. Visual Studio で **[ファイル]、[新しいプロジェクト]** の順に選択するか、**Ctrl + Shift + N** キーを押します。
1. **[言語]** を **[C++]** に設定し、「CMake」を検索します。 その後、 **[次へ]** をクリックします。 **[名前]** と **[場所]** を入力し、 **[作成]** を選択します。

Visual Studio では、実行可能ファイルの名前と、要求される最小の CMake バージョンのみを使用して、最小限の CMakeLists.txt ファイルが作成されます。 このファイルは手動で自由に編集できます。Visual Studio によって変更が上書きされることはありません。 **ソリューション エクスプローラー**でルートの CMakeLists.txt ファイルを右クリックし、 **[CMake settings for project]\(プロジェクト用の CMake の設定\)** を選択することで、CMake コマンドライン引数と環境変数を指定できます。 デバッグ用のオプションを指定するには、プロジェクト ノードを右クリックし、 **[デバッグ設定と起動設定]** を選択します。

::: moniker-end

既存の CMake プロジェクトを含むフォルダーを開くと、Visual Studio では CMake キャッシュの変数が使用され、IntelliSense とビルドが自動的に構成されます。 ローカルの構成およびデバッグ設定は、必要に応じて Visual Studio を使用している他のユーザーと共有できる JSON ファイルに格納されます。

Visual Studio では CMakeLists.txt ファイルが変更されないため、同じプロジェクトで作業している他のユーザーが、既に使用している任意のツールを使用し続けることができます。 Visual Studio では、CMakeLists.txt (場合によっては CMakeSettings.json) の編集が保存されると、キャッシュが再生成されます。 ただし、**既存のキャッシュ**構成が使用されている場合、Visual Studio によるキャッシュの変更は行われません。

Visual Studio での CMake のサポートに関する一般的な情報については、「[Visual Studio の CMake プロジェクト](../build/cmake-projects-in-visual-studio.md)」を参照してください。 まずこちらを読んでから、ここでの作業を進めてください。

## <a name="before-you-begin"></a>始める前に

まず、CMake コンポーネントを含む **C++ による Linux 開発** ワークロードがインストールされていることを確認します。 [Visual Studio での C++ Linux ワークロードのインストール](download-install-and-setup-the-linux-development-workload.md)に関するページを参照してください。 

Linux システムに次のものがインストールされていることを確認してください。 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Linux による CMake プロジェクトのサポートには、ターゲット マシンに CMake の最新バージョンがインストールされていることが必要となります。 ディストリビューションの既定のパッケージ マネージャーが提供するバージョンは、しばしば最新ではなく、Visual Studio で必要なすべての機能をサポートしていません。 Visual Studio 2019 では、Linux システムに CMake の最新バージョンがインストールされているかどうかを検出します。 見つからない場合は、Visual Studio のエディター ウィンドウの上部に、[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) からそれをインストールすることを提案する情報バーが表示されます。

Visual Studio で CMake を利用するには、CMake 3.8 で導入されたサーバー モードに対応する必要があります。 Visual Studio 2019 では、バージョン 3.14 以降をお勧めします。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio で CMake を利用するには、CMake 3.8 で導入されたサーバー モードに対応する必要があります。 Microsoft から提供されている CMake バリアントについては、[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) から最新のビルド済みバイナリをダウンロードします。

バイナリは `~/.vs/cmake` にインストールされます。 バイナリを配布すると、プロジェクトが自動的に再生成されます。 `CMakeSettings.json` の `cmakeExecutable` フィールドで指定する CMake が無効 (存在しない、またはサポートされていないバージョン) で、かつビルド済みバイナリが存在している場合は、Visual Studio では `cmakeExecutable` が無視され、ビルド済みバイナリが使われます。

:::moniker-end

## <a name="open-a-folder"></a>フォルダーを開く

最初に、メイン メニューから **[ファイル]**  >  **[開く]**  >  **[フォルダー]** の順に選択するか、コマンド ラインに「`devenv.exe <foldername>`」と入力します。 開いたフォルダーには、ソース コードと共に CMakeLists.txt ファイルが入っているはずです。
次のサンプルでは、単純な CMakeLists.txt ファイルと .cpp ファイルを確認できます。

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Linux ターゲットを選ぶ

フォルダーを開くとすぐに、Visual Studio によって CMakeLists.txt ファイルが解析され、**x86-Debug** の Windows ターゲットが指定されます。 リモートの Linux を対象とするには、プロジェクト設定を **Linux-Debug** または **Linux-Release** に変更します。 (後述の「[Linux 用の CMake 設定を構成する](#configure_cmake_linux)」を参照してください)。

::: moniker range="vs-2019"

Windows Subsystem for Linux をターゲットにするには、メイン ツールバーの構成ドロップダウンの **[構成の管理]** をクリックします。 次に、 **[構成の追加]** ボタンを押し、GCC を使用する場合は **[WSL-Debug]** または **[WSL-Release]** を選択し、Clang/LLVM ツールセットを使用する場合は [Clang バリアント] を選択します。 

**Visual Studio 2019 バージョン 16.1** では、WSL をターゲットにする場合、ソース ファイルが配置されている Windows ファイル システムに Linux 上のコンパイラが直接アクセスできるため、ソースやヘッダーをコピーする必要はありません (Windows バージョン 1903 以降では、Windows アプリケーションも Linux のヘッダー ファイルに直接アクセスできますが、Visual Studio ではこの機能はまだ活用されていません)。

::: moniker-end

対象がリモートの場合、Visual Studio では既定で **[ツール]**  >  **[オプション]**  >  **[クロス プラットフォーム]**  >  **[接続マネージャー]** の下にある最初のリモート システムが選択されます。 リモート接続が見つからない場合、リモート接続を作成するように求められます。 詳細については、[リモートの Linux コンピューターへの接続](connect-to-your-remote-linux-computer.md)に関するページを参照してください。

リモートの Linux を対象に指定した場合、ソースはリモート システムにコピーされます。

対象を選択したら、CMake は Linux システム上で自動実行され、プロジェクト用の CMake キャッシュを生成します。 

![Linux での CMake キャッシュの生成](media/cmake-linux-1.png "Linux で CMake キャッシュを生成する")

Visual Studio は、これらを Linux マシンからローカルの Windows コンピューター上のディレクトリに自動的にコピーして、リモートの Linux システムのヘッダーに IntelliSense のサポートを提供します。 詳細については、[リモート ヘッダーの IntelliSense](configure-a-linux-project.md#remote_intellisense) のセクションを参照してください。

## <a name="debug_cmake_project"></a> CMake プロジェクトをデバッグする

指定したデバッグ対象のシステムでコードをデバッグするには、ブレークポイントを設定し、プロジェクト設定の隣にあるツール バー メニューのスタートアップ項目として CMake ターゲットを選び、ツール バーの **[&#x23f5; 実行]** を選択するか、F5 キーを押します。

プログラムのコマンドライン引数をカスタマイズするには、**ソリューション エクスプローラー**の上部にある **[ターゲットの切り替え]** ボタンを押し、 **[ターゲット ビュー]** を選択します。 次に、ターゲットを右クリックし、 **[デバッグ設定と起動設定]** を選択します。 これにより、プログラムに関する情報を含んだ launch.vs.json 構成ファイルが開かれるか、作成されます。 ソース ファイルの場所を指定するには、次の例に示すように、**sourceFileMap** プロパティをファイルに追加します。

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

追加の引数を指定するには、`args` JSON 配列に引数を追加します。 詳細については、[C++ の [フォルダーを開く]](../build/open-folder-projects-cpp.md) プロジェクトに関するページ、および [CMake デバッグ セッションの構成](../build/configure-cmake-debugging-sessions.md)に関するページを参照してください。

## <a name="configure_cmake_linux"></a>Linux 用の CMake 設定を構成する

CMake Linux プロジェクト内の CMakeSettings.json ファイルで、[CMake 設定のカスタマイズ](../build/customize-cmake-settings.md)に関するページで一覧表示されているすべてのプロパティに加え、リモートの Linux コンピューター上のビルド設定を制御する追加のプロパティを指定できます。 

::: moniker range="vs-2019"

Visual Studio 2019 の CMake の既定の設定を変更するには、メイン ツールバーから **[構成]** ドロップダウンを開き、 **[構成の管理]** を選択します。 

![CMake の [構成の管理]](../build/media/vs2019-cmake-manage-configurations.png "CMake 構成ドロップダウン")

これにより **CMake 設定エディター**が表示されます。これを使用してルート プロジェクト フォルダー内の `CMakeSettings.json` ファイルを編集できます。 エディターの **[JSON の編集]** ボタンをクリックしてファイルを直接開くこともできます。 詳細については、[CMake 設定のカスタマイズ](../build/customize-cmake-settings.md)に関するページを参照してください。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 の既定の CMake 設定を変更するには、メイン メニューから **[CMake]、[CMake の設定の変更]、[CMakeLists.txt]** の順に選択するか、 **[ソリューション エクスプローラー]** の CMakeSettings.txt を右クリックし、 **[Change CMake Settings]\(CMake の設定の変更\)** を選びます。 Visual Studio によって、ルート プロジェクト フォルダー内に新しい `CMakeSettings.json` ファイルが作成されます。 **CMake 設定**エディター使用してファイルを開いたり、ファイルを直接変更したりできます。 詳細については、「[Customize CMake settings](../build/customize-cmake-settings.md)」 (CMake 設定のカスタマイズ) を参照してください。

次の例は、前のコード サンプルに基づく Visual Studio 2017 (および Visual Studio 2019 バージョン 16.0) での Linux-Debug 用の既定の構成を示しています。

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 バージョン 16.1 以降での既定の Linux-Debug 構成を次に示します。

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```
::: moniker-end

これらの設定の詳細については、[CMakeSettings.json リファレンス](../build/cmakesettings-reference.md)に関するページを参照してください。


## <a name="optional-settings"></a>オプション設定

さらに制御するために次のオプション設定を使用できます。

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

これらのオプションでは、ビルドの前後や CMake 生成の前に Linux システムでコマンドを実行できます。 値は、リモート システムで有効な任意のコマンドを指定できます。 出力はパイプで Visual Studio に戻されます。



## <a name="see-also"></a>関連項目

[プロジェクトのプロパティの操作](../build/working-with-project-properties.md)<br/>
[Visual Studio の CMake プロジェクト](../build/cmake-projects-in-visual-studio.md)<br/>
[リモートの Linux コンピューターに接続する](connect-to-your-remote-linux-computer.md)<br/>
[CMake 設定をカスタマイズする](../build/customize-cmake-settings.md)<br/>
[CMake デバッグ セッションを構成する](../build/configure-cmake-debugging-sessions.md)<br/>
[Linux プロジェクトの配置、実行、デバッグ](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 定義済み構成リファレンス](../build/cmake-predefined-configuration-reference.md)<br/>
