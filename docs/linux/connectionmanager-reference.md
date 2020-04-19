---
title: ConnectionManager リファレンス
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258034"
---
# <a name="connectionmanager-reference"></a>ConnectionManager リファレンス

::: moniker range="<=vs-2017"

ConnectionManager.exe は、Visual Studio 2019 バージョン 16.5 以降で使用できます。

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe は、Visual Studio 外でのリモート開発の接続を管理するためのコマンドライン ユーティリティです。 これは、新しい開発マシンをプロビジョニングするなどのタスクに役立ちます。 または、これを利用して Visual Studio で継続的インテグレーションを設定することもできます。 これは、[開発者コマンド プロンプト] ウィンドウで使用することができます。 開発者コマンド プロンプトの詳細については、「[コマンドラインから C++ Microsoft ツールセットを使用する](../build/building-on-the-command-line.md)」を参照してください。

ConnectionManager.exe は、Visual Studio 2019 バージョン 16.5 以降で使用できます。 これは、Visual Studio インストーラーの **[C++ による Linux 開発]** ワークロードに含まれています。 インストーラーで**接続マネージャー**を選択した場合も、自動的にインストールされます。 これは、 *%VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe* にインストールされます。

ConnectionManager.exe の機能は Visual Studio でも利用することができます。 IDE 内でリモート開発の接続を管理するには、メニュー バーで **[ツール]**  >  **[オプション]** を選択して、[オプション] ダイアログを開きます。 [オプション] ダイアログで、 **[クロス プラットフォーム]**  >  **[接続マネージャー]** を選択します。

## <a name="syntax"></a>構文

> **ConnectionManager.exe** *command* \[*arguments*] \[*options*]

### <a name="commands-and-arguments"></a>コマンドと引数

- **add** *user\@host* \[ **--port** *port*] \[ **--password** *password*] \[ **--privatekey** *privatekey_file*]

  新しい接続を認証し、追加します。 既定では、ポート 22 とパスワード認証を使用します。 (パスワードを入力するように求められます。) **--password** および **--privatekey** の両方を使用して秘密キーのパスワードを指定します。

- **remove** \[*connection_id* \| *user\@host* \[ **--port** *port*]]

  接続を削除します。 引数が指定されていない場合、削除する接続を指定するよう求められます。

- **remove-all**

  すべての保存されている接続を削除します。

- **list**

  すべての保存されている接続の情報と ID を表示します。

- **help**

  ヘルプ画面を表示します。

- **version**

  バージョン情報を表示します。

### <a name="options"></a>オプション

- **-q**、 **--quiet**

  `stdout` または `stderr` への出力を抑止します。

- **--no-prompt**

  適切な場合、プロンプトを表示せず失敗します。

- **--no-verify**

  認証せずに接続を追加または変更します。

- **--file** *filename*

  指定された *filename* から接続情報を読み取ります。

- **--no-telemetry**

  利用状況データの Microsoft への送信を無効にします。 **--no-telemetry** フラグが渡されない限り、利用状況データは収集されて Microsoft に送信されます。  

- **-n**、 **--dry-run**

  コマンドのドライ ランを実行します。

- **-p**

  **--password** と同じです。

- **-i**

  **--privatekey** と同じです。

## <a name="examples"></a>使用例

このコマンドは、localhost で "user" という名前のユーザーの接続を追加します。 この接続では、 *%USERPROFILE%\.ssh\id_rsa* にあるキー ファイルを認証に使用します。

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

このコマンドは、接続のリストから ID 1975957870 の接続を削除します。

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>関連項目

[Visual Studio でターゲットの Linux システムに接続する](connect-to-your-remote-linux-computer.md)

::: moniker-end
