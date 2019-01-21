---
title: Visual Studio で Linux CMake プロジェクトを構成する
description: Visual Studio で Linux CMake プロジェクトを構成する方法
ms.date: 07/20/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 28902f0a2938fe653eb4dfbb6e512367b1052b8c
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978323"
---
# <a name="configure-a-linux-cmake-project"></a>Linux CMake プロジェクトを構成する

**Visual Studio 2017 バージョン 15.4 以降**<br/>
Visual Studio に Linux C++ ワークロードをインストールすると、Linux の CMake サポートが既定で選択されます。 Visual Studio プロジェクトに変換しなくても、CMake を利用する既存のコード ベースで作業できるようになりました。 コード ベースがクロス プラットフォームの場合、Visual Studio 内から Windows と Linux の両方をターゲット設定できます。

このトピックは、Visual Studio の CMake サポートに関する基本的な知識が読者にあるものとして作成されています。 詳細については、「[CMake Tools for Visual C++](../ide/cmake-tools-for-visual-cpp.md)」 (Visual C++ の CMake ツール) をご覧ください。 CMake 自体の詳細については、「[Build, Test and Package Your Software With CMake](https://cmake.org/)」 (CMake でソフトウェアをビルド、テスト、パッケージ化する) を参照してください。

> [!NOTE]
> Visual Studio で CMake を利用するには、CMake 3.8 で導入されたサーバー モードに対応する必要があります。 Microsoft から提供されている CMake 変数の場合は、[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) から最新のビルド済みバイナリをダウンロードします。 Visual Studio 2019 では、ビルド済みバイナリを自動的に配置させることが可能です (「[ビルド済み CMake バイナリをダウンロードする](#download-prebuilt-cmake-binaries)」を参照)。

## <a name="open-a-folder"></a>フォルダーを開く

最初に、メイン メニューから **[ファイル]** > **[開く]** > **[フォルダー]** の順に選択するか、コマンド ラインに「`devenv.exe <foldername>`」と入力します。 開いたフォルダーには、ソース コードと共に CMakeLists.txt ファイルが入っているはずです。
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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Linux ターゲットを選ぶ

フォルダーを開くとすぐに、Visual Studio によって CMakeLists.txt ファイルが解析され、**x86-Debug** の Windows ターゲットが指定されます。 Linux を対象とするには、プロジェクト設定を **Linux-Debug** または **Linux-Release** に変更します。

既定では、**[ツール]** > **[オプション]** > **[クロス プラットフォーム]** > **[接続マネージャー]** の下にある一覧の、最初のリモート システムが選ばれます。 リモート接続が見つからない場合、リモート接続を作成するように求められます。

Linux ターゲットを指定すると、ソースが Linux マシンにコピーされます。 次に、Linux マシンで CMake が実行され、プロジェクトの CMake キャッシュが生成されます。

![Linux で CMake キャッシュを生成する](media/cmake-linux-1.png "Linux で CMake キャッシュを生成する")

**Visual Studio 2017 バージョン 15.7 以降:**<br/>
リモート ヘッダーの IntelliSense サポートを提供するため、Visual Studio によってローカルの Windows コンピューター上のディレクトリに自動的にコピーされます。 詳細については、[リモート ヘッダーの IntelliSense](configure-a-linux-project.md#remote_intellisense) のセクションを参照してください。

## <a name="debug-the-project"></a>プロジェクトをデバッグする

リモート システムでコードをデバッグするには、ブレークポイントを設定し、プロジェクト設定の隣にあるツール バー メニューのスタートアップ項目として CMake ターゲットを選び、ツール バーの **[&#x23f5; 実行]** を選択するか、F5 キーを押します。

プログラムのコマンド ライン引数をカスタマイズするには、**ソリューション エクスプローラー**で実行可能ファイルを右クリックし、**[デバッグ設定と起動設定]** を選びます。 これにより、プログラムに関する情報を含んだ launch.vs.json 構成ファイルが開かれるか、作成されます。 追加の引数を指定するには、`args` JSON 配列に引数を追加します。 詳細については、「[Open Folder projects in Visual C++ (Visual C++ の [フォルダーを開く] プロジェクト)](../ide/non-msbuild-projects.md)」をご覧ください。

## <a name="configure-cmake-settings-for-linux"></a>Linux の CMake 設定を構成する

既定の CMake 設定を変更するには、メイン メニューで **[CMake]、[CMake の設定の変更]、[CMakeLists.txt]** の順に選ぶか、**[ソリューション エクスプローラー]** の CMakeSettings.txt を右クリックし、**[CMake の設定の変更]** を選びます。 次に、`CMakeSettings.json` という名称のフォルダーに新しいファイルが作成されます。このファイルには、プロジェクト設定のメニュー項目の一覧にある既定の構成が入力されます。 次のサンプルでは、前のコード サンプルに基づく、Linux デバッグの既定の構成を確認できます。

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

`name` 値には、任意の値を指定できます。 リモート システムが複数存在する場合、`remoteMachineName` 値によって、ターゲットとなるリモート システムが指定されます。 このフィールドには IntelliSense が有効になっており、適切なシステムの選択を支援します。 フィールド `remoteCMakeListsRoot` によって、リモート システム上にある、プロジェクト ソースのコピー先が指定されます。 フィールド `remoteBuildRoot` は、リモート システムでビルド出力が生成される場所です。 その出力は、`buildRoot` によって指定される場所にもローカル コピーされます。 cmake インストールを行うときに適用されることを除き、`remoteInstallRoot` フィールドと `installRoot` フィールドは `remoteBuildRoot` と `buildRoot` に似ています。 `remoteCopySources` エントリにより、ローカル ソースがリモート コンピューターにコピーされるかどうかが制御されます。 ファイルが大量にあり、自分で既にソースを同期している場合、これを false に設定することがあります。 `remoteCopyOutputVerbosity` 値により、エラーを診断する必要がある場合のコピー ステップの詳細度が制御されます。 `remoteCopySourcesConcurrentCopies` エントリにより、コピーのために生成されるプロセスの数が制御されます。 `remoteCopySourcesMethod` 値は rsync または sftp になります。 `remoteCopySourcesExclusionList` フィールドでは、リモート コンピューターにコピーされる内容を制御できます。 `rsyncCommandArgs` 値では、コピーの rsync メソッドを制御できます。 `remoteCopyBuildOutput` フィールドにより、リモート ビルド出力がローカル ビルド フォルダーにコピーされるかどうかが制御されます。

さらに制御するためのオプション設定もいくつかあります。

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

そうしたオプションでは、ビルドの前後や CMake 生成の前にリモート ボックスでコマンドを実行できます。 リモート ボックスで有効なコマンドになります。 出力はパイプで Visual Studio に戻されます。

## <a name="download-prebuilt-cmake-binaries"></a>ビルド済み CMake バイナリをダウンロードする

Linux distro には古いバージョンの CMake が含まれている場合があります。 Visual Studio で CMake を利用するには、CMake 3.8 で導入されたサーバー モードに対応する必要があります。 Microsoft から提供されている CMake 変数の場合は、[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) から最新のビルド済みバイナリをダウンロードします。

**Visual Studio 2019**<br/>
リモート コンピューター上に有効な CMake が見つからなかった場合、情報バーが表示され、CMake のビルド済みバイナリを自動的に配置するオプションが表示されます。 バイナリは `~/.vs/cmake` にインストールされます。 バイナリを配布すると、プロジェクトが自動的に再生成されます。 `CMakeSettings.json` の `cmakeExecutable` フィールドで指定する CMake が無効 (存在しない、またはサポートされていないバージョン) で、かつビルド済みバイナリが存在している場合は、Visual Studio では `cmakeExecutable` が無視され、ビルド済みバイナリが使われます。

## <a name="see-also"></a>「

[プロジェクトのプロパティの操作](../ide/working-with-project-properties.md)<br/>
[Visual C++ 用の CMake ツール](../ide/cmake-tools-for-visual-cpp.md)
