---
title: Visual Studio で CMake デバッグ セッションを構成する
description: Visual Studio を使用して CMake デバッガーの設定を構成する方法について説明します。
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 5e627f02b5245baede6e92268cedfc43957f3abc
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031327"
---
# <a name="configure-cmake-debugging-sessions"></a>CMake デバッグ セッションを構成する

::: moniker range="vs-2015"

ネイティブ CMake のサポートは、Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range=">=vs-2017"

すべての実行可能な CMake ターゲットが、 **[全般]** ツール バーの **[スタートアップ アイテム]** ドロップダウンに表示されます。 デバッグ セッションを開始するには、1 つを選択してデバッガーを起動するだけです。

![CMake スタートアップ項目のドロップダウン](media/cmake-startup-item-dropdown.png "CMake スタートアップ項目のドロップダウン")

ソリューションエクスプローラーからデバッグセッションを開始することもできます。 最初に、 **[ソリューションエクスプローラー]** ウィンドウの [ **Cmake ターゲット] ビュー**に切り替えます。

![CMake ターゲットビューのボタン](media/cmake-targets-view.png  "CMake ターゲットビューのメニュー項目")

次に、任意の実行可能ファイルを右クリックし、 **[デバッグ]** または **[デバッグと起動の設定]** を選択します。 **デバッグ**は、アクティブな構成に基づいて、選択したターゲットのデバッグを自動的に開始します。 **デバッグと起動の設定**では、*起動した json*ファイルが開き、選択したターゲットの新しいデバッグ構成が追加されます。

## <a name="customize-debugger-settings"></a>デバッガー設定をカスタマイズする

プロジェクト内の任意の実行可能な CMake ターゲットのデバッガー設定は、 *launch*. という名前のファイルでカスタマイズできます。 このファイルには、次の3つのエントリポイントがあります。

- メインメニューから [デバッグ **> デバッグと起動の設定**] を選択して、アクティブなデバッグターゲットに固有のデバッグ構成を編集します。 アクティブなターゲットを選択していない場合、このオプションはグレー表示されます。

- ソリューションエクスプローラーの [**ターゲット] ビュー**に移動します。 次に、デバッグターゲットを右クリックし、 **[デバッグ設定と起動設定]** を選択して、選択したターゲットに固有のデバッグ構成を編集します。

- ルートの CMakeLists を右クリックし、 **[デバッグ設定と起動設定]** を選択して **[デバッガーの選択]** ダイアログボックスを開きます。 このダイアログでは、任意のデバッグ構成を追加できますが、`projectTarget` プロパティを使用して呼び出す CMake ターゲットを手動で指定する必要があります。

*Cmakesettings. json*ファイル内の任意のキーを参照するには、「 *launch. vs. json*」で `cmake.` を先頭に付けます。 次の例は、現在選択されている構成の*Cmakesettings. json*ファイル内の `remoteCopySources` キーの値を取得する単純な*起動と json*ファイルを示しています。

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Launch ファイルと*json*ファイルを保存すると、Visual Studio によって、 **[スタートアップ項目]** ドロップダウンに新しい名前のエントリが作成されます。 任意の数の CMake ターゲットに対して、複数のデバッグ構成を作成するために、launch ファイルと*json*ファイルを編集することができます。

## <a name="launchvsjson-reference"></a>を起動します。と json のリファレンス

すべてのデバッグシナリオをサポートするために、多くの launch プロパティと*json*プロパティがあります。 次のプロパティは、リモートとローカルの両方で、すべてのデバッグ構成に共通です。

- `projectTarget`: プロジェクトをビルドするときに呼び出す CMake ターゲットを指定します。 このプロパティは、 **$ {activeDebugTarget} またはターゲットビューのデバッグ > デバッグと起動の設定をデバッグ**から*開始*した場合に、Visual Studio によって自動的に設定されます。

- `program`: リモートシステム上のプログラム実行可能ファイルへの完全パス。 ここでは、マクロ `${debugInfo.fullTargetPath}` を使用できます。

- `args`: デバッグするプログラムに渡されるコマンドライン引数。

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>リモートの Linux プロジェクトの場合は、「」を参照してください。

次のプロパティは、**リモートデバッグ構成**に固有です。 また、[カスタムの gdb コマンドを実行](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)して、基になるデバッガーにコマンドを直接送信したり、 [miengine のログ記録を有効](https://github.com/microsoft/MIEngine/wiki/Logging)にして、gdb に送信されるコマンド、gdb が返す出力、および各コマンドの実行時間を確認することもできます。

- `cwd`: リモートコンピューター上の依存関係やその他のファイルを検索するための現在の作業ディレクトリ。 マクロ `${debugInfo.defaultWorkingDirectory}` を使用できます。 既定値は、 *Cmakelists*でオーバーライドされない限り、リモートワークスペースのルートになります。 このプロパティは、リモート構成にのみ使用されます。`currentDir` は、ローカルプロジェクトの起動中のアプリの現在のディレクトリを設定するために使用されます。

- `environment`: 次の構文でプログラムの環境に追加する追加の環境変数。

```json
  "environment": [
      {
        "name": "ENV1",
        "value": "envvalue1"
      },
      {
        "name": "ENV2",
        "value": "envvalue2"
      }
    ]
```

- `pipeArgs`: 接続を構成するためにパイププログラムに渡されるコマンドライン引数。 パイププログラムは、Visual Studio と gdb の間で標準入力/出力を中継するために使用されます。 コマンド `${debuggerCommand}` は、リモートシステムで gdb を起動し、次のように変更できます。

  - 環境変数の表示の値を Linux システムにエクスポートします。 次の例では、この値は `:1`です。

  ```json
  "pipeArgs": [
      "/s",
      "${debugInfo.remoteMachineId}",
      "/p",
      "${debugInfo.parentProcessId}",
      "/c",
      "export DISPLAY=:1;${debuggerCommand}",
      "--tty=${debugInfo.tty}"
    ],
  ```

  - Gdb の実行前にスクリプトを実行します。 実行権限がスクリプトに設定されていることを確認します。

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: プロセスが起動されるとすぐに中断するかどうかを指定するブール値です。 既定値は false です。

- `visualizerFile`: このプロセスをデバッグするときに使用する[natvis ファイル](/visualstudio/debugger/create-custom-views-of-native-objects)。 このオプションは gdb の整形出力と互換性がありません。 また、このプロパティを設定するときに `showDisplayString` も設定します。

- `showDisplayString`: `visualizerFile` が指定されている場合に表示文字列を有効にするブール値。 このオプションを `true` に設定すると、デバッグ中にパフォーマンスが低下する可能性があります。

- `setupCommands`: 基になるデバッガーを設定するために実行する1つ以上の gdb コマンド。

- `externalConsole`: デバッグ対象のコンソールを起動するかどうかを指定するブール値。

- `miDebuggerPath`: gdb への完全なパス。 指定されていない場合、Visual Studio はまず、デバッガーのパスを検索します。

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`: gdb とデバッグするプログラムをホストするリモート Linux システム。

::: moniker-end

::: moniker range="vs-2019"

リモート**デバッグ**システムから**リモートビルドシステム**を分離するには、次のプロパティを使用できます。 詳細については、「[ビルドおよびデバッグ用に別のコンピューターを指定する](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects)」を参照してください。

- `remoteMachineName`: gdb とデバッグするプログラムをホストするリモート Linux システム。 このエントリは、 *Cmakesettings. json*で指定されたビルドに使用されるリモートの Linux システムと一致する必要はありません。 Ctrl キーを押し**ながら Space**キーを押して、[接続マネージャー](../linux/connect-to-your-remote-linux-computer.md)に格納されているすべてのリモート接続の一覧を表示します。

- `disableDeploy`: ビルドとデバッグの分離が無効になっているかどうかを示します。 この機能を有効にすると、ビルドとデバッグが2台の異なるコンピューターで実行されるようになります。

- `deployDirectory`: 実行可能ファイルがコピーされるリモートデバッグコンピューター上のディレクトリ (`remoteMachineName`で指定)。

- `deploy`: 高度な配置設定の配列。 展開プロセスをより細かく制御する必要がある場合にのみ、これらの設定を構成する必要があります。 既定では、リモート デバッグ マシンには、デバッグ プロセスにとって必要なファイルのみが配置されます。

  - `sourceMachine`: ファイルまたはディレクトリのコピー元となるコンピューター。 Ctrl キーを押し**ながら Space**キーを押すと、接続マネージャーに格納されているすべてのリモート接続の一覧が表示されます。

  - `targetMachine`: ファイルまたはディレクトリがコピーされるコンピューター。 Ctrl キーを押し**ながら Space**キーを押すと、接続マネージャーに格納されているすべてのリモート接続の一覧が表示されます。

  - `sourcePath`: `sourceMachine`上のファイルまたはディレクトリの場所。

  - `targetPath`: `targetMachine`上のファイルまたはディレクトリの場所。

  - `deploymentType`: 展開の種類の説明。 `LocalRemote` と `RemoteRemote` がサポートされています。 `LocalRemote` は、ローカルファイルシステムから、launch. と*json*の `remoteMachineName` で指定されたリモートシステムにコピーすることを意味します。 `RemoteRemote` は、 *Cmakesettings. json*で指定されたリモートビルドシステムから、launch. と*json*で指定された別のリモートシステムにコピーすることを意味します。

  - `executable`: 配置されたファイルが実行可能ファイルであるかどうかを示します。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>リモートプロセスにアタッチする

デバッガーをアタッチするプロセス ID に `processId` を設定することにより、Linux システムで実行されているプロセスにアタッチできます。 詳細については、「 [GDB を使用したプロセスへのアタッチのトラブルシューティング](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)」を参照してください。

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>Gdbserver を使用して Linux でデバッグする

Visual Studio 2019 バージョン 16.5 Preview 1 以降では、gdbserver を使用した CMake プロジェクトのリモートデバッグがサポートされています。 詳細については、「 [gdbserver を使用した Linux CMake プロジェクトのデバッグ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)」を参照してください。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>関連項目

[Visual Studio での Cmake プロジェクトの](cmake-projects-in-visual-studio.md)\
[Linux CMake プロジェクトを構成する](../linux/cmake-linux-project.md)\
[リモートの Linux コンピューター\ に接続](../linux/connect-to-your-remote-linux-computer.md)します。
[CMake ビルド設定をカスタマイズ](customize-cmake-settings.md)\
[CMake デバッグセッションの構成](configure-cmake-debugging-sessions.md)\
[Linux プロジェクトの配置、実行、デバッグ](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 定義済み構成リファレンス](cmake-predefined-configuration-reference.md)

::: moniker-end
