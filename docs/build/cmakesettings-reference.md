---
title: CMakeSettings.json スキーマ リファレンス
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 542a469393d3655418f69e5d51d59adfa824ad15
ms.sourcegitcommit: 9a63e9b36d5e7fb13eab15c2c35bedad4fb03ade
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600041"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json スキーマ リファレンス

::: moniker range="vs-2015"

CMake プロジェクトは、Visual Studio 2017 以降でサポートされています。

::: moniker-end

::: moniker range=">=vs-2017"

**Cmakesettings. json**ファイルには、Visual Studio が IntelliSense に使用する情報が含まれており、指定された*構成*およびコンパイラ*環境*に対して cmake に渡すコマンドライン引数を構築します。 構成では、特定のプラットフォームおよびビルドの種類 (`x86-Debug`、`Linux-Release`など) に適用されるプロパティを指定します。 各構成は、MSVC、GCC、Clang などのコンパイラツールセットに関する情報をカプセル化する環境を指定します。 CMake では、コマンドライン引数を使用して、プロジェクトのルート*cmakecache.txt*ファイルとその他のプロジェクトファイルを再生成します。 値は、 *Cmakelists .txt*ファイルでオーバーライドできます。 

IDE で構成を追加または削除し、JSON ファイルで直接編集するか、 **Cmake 設定エディター** (Visual Studio 2019 以降) を使用することができます。 IDE で構成を簡単に切り替えて、さまざまなプロジェクトファイルを生成することができます。 詳細については、「 [Visual Studio での CMake ビルド設定のカスタマイズ](customize-cmake-settings.md)」を参照してください。

## <a name="configurations"></a>構成

`configurations` 配列には、CMake プロジェクトのすべての構成が含まれています。 定義済みの構成の詳細については、「[定義済みの構成のリファレンス](cmake-predefined-configuration-reference.md)」を参照してください。 ファイルには、任意の数の事前定義済みまたはカスタム構成を追加できます。 

`configuration` には次のプロパティがあります。

- `addressSanitizerEnabled`: `true` は、アドレスサニタイザー (Windows の試験段階) でプログラムをコンパイルします。 Linux では、最適な結果を得るために、-fno-frame-ポインターとコンパイラの最適化レベル Os または-Oo を使用してコンパイルします。
- `addressSanitizerRuntimeFlags`: ASAN_OPTIONS 環境変数を介して AddressSanitizer に渡されるランタイムフラグ。 形式: フラグ 1 = 値: フラグ 2 = value2。
- `buildCommandArgs`: --ビルド-- の後に CMake に渡されるネイティブ ビルド スイッチを指定します。 たとえば、Ninja ジェネレーターの使用時に -v を渡すと、コマンド ラインの出力が Ninja に強制されます。 Ninja コマンドの詳細については、「[Ninja のコマンド ライン引数](#ninja)」参照してください。
- `buildRoot`: 選択したジェネレーターに CMake がビルド スクリプトを生成するディレクトリを指定します。  **-DCMAKE_BINARY_DIR**スイッチにマップし、 *cmakecache.txt*が作成される場所を指定します。 フォルダーが存在しない場合は、作成されます。 サポートされているマクロには、`${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}` などがあります。
- `cacheGenerationCommand`: コマンドラインツールと引数を指定します。たとえば、 *gencache*を使用してキャッシュを生成します。 コマンドは、ユーザーが明示的に再生成を要求したとき、または CMakeLists .txt または Cmakelists. json ファイルが変更されたときに、指定した環境のシェルから実行されます。
- `cacheRoot`: CMake キャッシュへのパスを指定します。 このディレクトリには、既存の*cmakecache.txt*ファイルが含まれている必要があります。
- `clangTidyChecks`: clang-tidy に渡される警告のコンマ区切りの一覧です。ワイルドカードを使用できます。 '-' プレフィックスによってチェックが削除されます。
- `cmakeCommandArgs`: プロジェクトファイルを生成するために呼び出されたときに CMake に渡される追加のコマンドラインオプションを指定します。
- `cmakeToolchain`: toolchain ファイルを指定します。 これは、-DCMAKE_TOOLCHAIN_FILE を使用して CMake に渡されます。
- `codeAnalysisRuleset`: コード分析を実行しているときに使用するルールセットを指定します。 Visual Studio によってインストールされたルールセット ファイルの完全なパスまたはファイル名を指定できます。
- `configurationType`: 選択したジェネレーターにビルドの種類の構成を指定します。 次のいずれかを指定できます。

  - デバッグ
  - Release
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`: テストの実行中に CTest に渡す追加のコマンド ライン オプションを指定します。
- `description`: メニューに表示されるこの構成の説明。
- `enableClangTidyCodeAnalysis`: コード分析には Clang-Tidy を使用します。
- `enableMicrosoftCodeAnalysis`: コード分析に Microsoft コード分析ツールを使用します。
- `generator`: この構成に使用する CMake ジェネレーターを指定します。 次のいずれかを指定できます。
  
  **Visual Studio 2019 のみ:**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 以降:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - UNIX メイクファイル
  - Ninja

Ninja は柔軟性や機能ではなく、ビルド速度が速いことを目的に設計されているため、既定値としてこれが設定されます。 ただし、CMake プロジェクトによっては、Ninja を使うと正しくビルドできないことがあります。 この問題が発生した場合は、代わりに Visual Studio プロジェクトを生成するように CMake に指示できます。

Visual studio 2017 で Visual Studio ジェネレーターを指定するには、[Cmake] を選択してメインメニューからを開きます。 **CMake の設定を変更**します。 "Ninja" を削除し、「V」と入力します。 これにより IntelliSense がアクティブになり、必要なジェネレーターを選択できます。

Visual studio 2019 で Visual Studio ジェネレーターを指定するには**ソリューションエクスプローラー**で*cmakelists .txt*ファイルを右クリックし、 **[プロジェクトの cmake の設定]** を選択し > **[詳細設定の表示]** を選択します。 **cmake ジェネレーター**> ます。

アクティブな構成で Visual Studio ジェネレーターを指定すると、`-m -v:minimal` 引数を指定して MSBuild.exe が既定で呼び出されます。 ビルドをカスタマイズするには、 *Cmakesettings. json*ファイル内で、`buildCommandArgs` プロパティを使用してビルドシステムに渡す追加の[MSBuild コマンドライン引数](../build/reference/msbuild-visual-cpp-overview.md)を指定します。

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`: 選択したジェネレーターに CMake がインストール ターゲットを生成するディレクトリを指定します。 サポートされているマクロには、`${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}` などがあります。
- `inheritEnvironments`: この構成が依存している 1 つまたは複数のコンパイラ環境を指定します。 任意のカスタム環境を使用することも、定義済みの環境を使用することもできます。 詳細については、[環境](#environments)に関するページを参照してください。
- `intelliSenseMode`: IntelliSense の情報を計算するために使用するモードを指定します。 次のいずれかを指定できます。

  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm

- `name`: 構成に名前を付けます。  定義済みの構成の詳細については、「[定義済みの構成のリファレンス](cmake-predefined-configuration-reference.md)」を参照してください。
- `wslPath`: Windows Subsystem for Linux のインスタンスのランチャーへのパス。

### <a name="additional-settings-for-cmake-linux-projects"></a>CMake Linux プロジェクトの追加設定

- `remoteMachineName`: CMake、ビルド、およびデバッガーをホストするリモートの Linux マシンの名前を指定します。 新しい Linux マシンを追加するには、接続マネージャーを使用します。 サポートされているマクロには、`${defaultRemoteMachineName}` が含まれます。
- `remoteCopySourcesOutputVerbosity`: リモート マシンへのソース コピー操作の詳細レベルを指定します。 "ノーマル"、"詳細"、"診断" のいずれかを指定できます。
- `remoteCopySourcesConcurrentCopies`: リモートコンピューターへのソースの同期中に使用される同時コピー数を指定します (sftp のみ)。
- `remoteCopySourcesMethod`: リモート マシンにファイルをコピーするメソッドを指定します。 "rsync" または "sftp" のいずれかを指定できます。
- `remoteCMakeListsRoot`: CMake プロジェクトを含むリモート マシン上のディレクトリを指定します。 サポートされているマクロには、`${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}` などがあります。
- `remoteBuildRoot`: 選択したジェネレーターに CMake がビルド スクリプトを生成するリモート マシン上のディレクトリを指定します。 サポートされているマクロには、`${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}` などがあります。
- `remoteInstallRoot`: 選択したジェネレーターに CMake がインストール ターゲットを生成するリモート マシン上のディレクトリを指定します。 サポートされているマクロには、`${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}` などがあります。`VARIABLE` は、システム、ユーザー、またはセッション レベルで定義されている変数です。
- `remoteCopySources`: Visual Studio がソースファイルをリモートコンピューターにコピーする必要があるかどうかを指定する `boolean`。 既定値は true です。 自分でファイルの同期を管理する場合は、false に設定します。
- `remoteCopyBuildOutput`: リモートシステムからビルド出力をコピーするかどうかを指定する `boolean`。
- `remoteCopyAdditionalIncludeDirectories`: 追加のインクルードディレクトリをリモートコンピューターからコピーして、IntelliSense をサポートします。 "/Path1;/path2" の形式で指定します。
- `remoteCopyExcludeDirectories`: リモートコンピューターからコピーするディレクトリを含めません。 "/Path1;/path2" の形式で指定します。
- `remoteCopyUseCompilerDefaults`: コンパイラの既定の定義を使用し、IntelliSense のパスを含めるかどうかを指定します。 のコンパイラが gcc スタイルの引数をサポートしていない場合にのみ、false にする必要があります。
- `rsyncCommandArgs`: rsync に渡される追加のコマンド ライン オプションのセットを指定します。
- `remoteCopySourcesExclusionList`: ソースファイルをコピーするときに除外するパスの一覧を指定する `array` です。パスには、ファイルまたはディレクトリの名前、またはコピーのルートを基準とした相対パスを指定できます。 glob パターン マッチング用のワイルドカード \\\"*\\\" および \\\"?\\\" を使用できます。
- `cmakeExecutable`: CMake プログラムの実行可能ファイルへの完全なパスを指定します。ファイル名と拡張子を含めます。
- `remotePreGenerateCommand`: CMake を実行して*Cmakelists .txt*ファイルを解析する前に実行するコマンドを指定します。
- `remotePrebuildCommand`: ビルド前にリモート マシン上で実行するコマンドを指定します。
- `remotePostbuildCommand`: ビルド後にリモート マシン上で実行するコマンドを指定します。
- `variables`: cmake 変数の名前と値のペアが含まれています。これは **、D の** *_名前_=_値_* として cmake に渡されます。 CMake プロジェクトのビルド手順で、 *cmakecache.txt*ファイルに変数を直接追加することを指定する場合は、ここで追加することをお勧めします。 次の例は、14.14.26428 MSVC ツールセットに名前と値のペアを指定する方法を示しています。

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

`"type"`を定義しない場合、`"STRING"` の種類は既定で想定されることに注意してください。
- `remoteCopyOptimizations`: リモートターゲットへのソースコピーを制御するための**Visual Studio 2019 バージョン 16.5**以降のプロパティ。 既定では、最適化が有効になっています。 `remoteCopyUseOptimizations`、`rsyncSingleDirectoryCommandArgs`、および `remoteCopySourcesMaxSmallChange` を含みます。

## <a name="environments"></a>下

*環境*には、Visual Studio が cmake .exe を呼び出すために使用するプロセスで設定された環境変数がカプセル化されています。 MSVC プロジェクトの場合、変数は、[開発者コマンドプロンプト](building-on-the-command-line.md)で特定のプラットフォーム用に設定されているものです。 たとえば、`msvc_x64_x64` 環境は、 **vs 2017 の開発者コマンドプロンプト**と、 **-arch = amd64-host_arch = amd64**引数を使用した**vs 2019 の開発者コマンドプロンプト**を実行する場合と同じです。 *Cmakesettings. json*の `env.{<variable_name>}` 構文を使用すると、フォルダーへのパスを作成するなど、個々の環境変数を参照できます。  次の定義済みの環境が用意されています。

- linux_arm: ARM Linux をリモートでターゲットにします。
- linux_x64: x64 Linux をリモートでターゲットにします。
- linux_x86: リモートで x86 Linux をターゲットとします。
- msvc_arm: MSVC コンパイラを使用して ARM Windows をターゲットにします。
- msvc_arm_x64:64 ビットの MSVC コンパイラを使用して ARM Windows をターゲットにします。
- msvc_arm64: MSVC コンパイラを使用して ARM64 Windows をターゲットにします。
- msvc_arm64_x64:64 ビットの MSVC コンパイラを使用して ARM64 Windows をターゲットにします。
- msvc_x64: MSVC コンパイラを使用して x64 Windows をターゲットにします。
- msvc_x64_x64:64 ビットの MSVC コンパイラを使用して x64 Windows をターゲットにします。
- msvc_x86: MSVC コンパイラを使用して x86 Windows をターゲットにします。
- msvc_x86_x64:64 ビットの MSVC コンパイラを使用して x86 Windows をターゲットにします。

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>CMakeLists から環境変数にアクセスする

CMakeLists .txt ファイルからは、すべての環境変数が `$ENV{variable_name}`構文によって参照されます。 環境で使用可能な変数を表示するには、対応するコマンドプロンプトを開き、「`SET`」と入力します。 環境変数の一部の情報は、CMake システムのイントロスペクション変数でも使用できますが、環境変数を使用する方が便利な場合があります。 たとえば、MSVC コンパイラバージョンまたは Windows SDK バージョンは、環境変数を介して簡単に取得できます。

### <a name="custom-environment-variables"></a>カスタム環境変数

`CMakeSettings.json`では、`environments` 配列でグローバルまたは構成ごとにカスタム環境変数を定義できます。 カスタム環境は、定義済みの環境の代わりに使用できる一連のプロパティをグループ化したり、定義済みの環境を拡張または変更したりするための便利な方法です。 `environments` 配列内の各項目は以下で構成されています。

- `namespace`: フォーム `namespace.variable` 内の構成から環境変数を参照できるように環境に名前を付けます。 既定の環境オブジェクトは `env` と呼ばれ、`%USERPROFILE%`を含む特定のシステム環境変数が設定されます。
- `environment`: この変数グループを一意に識別します。 後で `inheritEnvironments` エントリでグループが継承できるようにします。
- `groupPriority`: これらの変数を評価するときの優先度を指定する整数です。 数字が大きい大きい項目が最初に評価されます。
- `inheritEnvironments`: このグループによって継承される環境のセットを指定する値の配列。 この機能を使用すると、既定の環境を継承し、実行時に CMake.exe に渡されるカスタム環境変数を作成することができます。 

**Visual Studio 2019 バージョン16.4 以降:** デバッグターゲットは、 *Cmakesettings. json*で指定した環境で自動的に起動されます。 [Launch と json](launch-vs-schema-reference-cpp.md) [の比較に](tasks-vs-json-schema-reference-cpp.md)より、環境変数を、ターゲット単位またはタスク単位でオーバーライドまたは追加できます。

次の例では、1 つのグローバル変数 **BuildDir** を定義します。これは、x86-Debug と x64-Debug の両方の構成で継承されます。 各構成は、この変数を使って、その構成の **buildRoot** プロパティの値を指定します。 各構成が **inheritEnvironments** プロパティを使ってその構成のみに適用される変数を指定する方法にも注意してください。

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

次の例では、x86 デバッグ構成が **BuildDir** プロパティに対して独自の値を定義します。 この値は、**BuildRoot** が **に評価されるように、グローバル**BuildDir`D:\custom-builddir\x86-Debug` プロパティによって設定される値をオーバーライドします。

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>マクロ

*Cmakesettings. json*では、次のマクロを使用できます。

- `${workspaceRoot}` –ワークスペースフォルダーの完全なパス
- `${workspaceHash}` – ワークスペースの場所のハッシュです。現在のワークスペースの一意識別子を作成するのに便利です (たとえば、フォルダーのパスで使用する場合)
- `${projectFile}` – ルート CMakeLists.txt ファイルの完全なパスです
- `${projectDir}` – ルート CMakeLists.txt ファイルのフォルダーの完全なパスです
- `${thisFile}` – `CMakeSettings.json` ファイルの完全なパスです
- `${name}` – 構成の名前です
- `${generator}` – この構成で使用される CMake ジェネレーターの名前です

*Cmakesettings. json*のマクロと環境変数へのすべての参照は、cmake .exe コマンドラインに渡される前に展開されます。

## <a name="ninja"></a> Ninja のコマンド ライン引数

ターゲットを指定しないと、"default" ターゲットがビルドされます。

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|オプション|Description|
|--------------|------------|
| --version  | Ninja のバージョンを書き出します ("1.7.1")|
|   -C DIR   | 何かを実行する前に、DIR (ディレクトリ) に変更します|
|   -f FILE  | 入力ビルド ファイルを指定します (既定値は build.ninja)|
|   -j N     | N 個のジョブを並列実行します (既定値は 14、使用可能な CPU の数から派生)|
|   -k N     | N 個のジョブが失敗するまで続けます (既定値は 1)|
|   -l N     | 負荷の平均が N より大きい場合は、新しいジョブを開始しません|
|   -n       | ドライ実行 (コマンドを実行しませんが、成功したように動作します)|
|   -v       | ビルド中にすべてのコマンド ラインを表示します|
|   -d MODE  | デバッグを有効にします (モードを一覧表示するには -d list を使用)|
|   -t TOOL  | サブツールを実行します (サブツールを一覧表示するには -t list を使用)。 トップレベルのオプションを終了します。さらにフラグがツールに渡されます|
|   -w FLAG  | 警告を調整します (警告を一覧表示するには -w list を使用)|

::: moniker-end
