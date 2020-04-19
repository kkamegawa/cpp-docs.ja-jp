---
title: Visual Studio でターゲットの Linux システムに接続する
description: Visual Studio の C++ プロジェクト内からリモートの Linux マシンまたは Linux 用 Windows サブシステムに接続する方法です。
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518219"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Visual Studio でターゲットの Linux システムに接続する

::: moniker range="vs-2015"

Linux サポートは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range="vs-2017"

Linux プロジェクトのターゲットは、リモート マシンとなるように構成することも、Windows Subsystem for Linux (WSL) とすることもできます。 両方のリモート マシンと WSL に対して、Visual Studio 2017 でリモート接続を設定する必要があります。

::: moniker-end

::: moniker range="vs-2019"

Linux プロジェクトのターゲットは、リモート マシンとなるように構成することも、Windows Subsystem for Linux (WSL) とすることもできます。 リモート マシンの場合は、Visual Studio でリモート接続を設定する必要があります。 WSL に接続するには、[WSL への接続](#connect-to-wsl)に関するセクションに進んでください。

::: moniker-end

::: moniker range=">=vs-2017"

リモート接続を使用する場合、Visual Studio はリモート マシンで C++ Linux プロジェクトをビルドします。 物理マシン、クラウド内の VM、WSL のいずれであるかは関係ありません。
プロジェクトをビルドするために、Visual Studio はソース コードをリモートの Linux コンピューターにコピーします。 その後、コードは Visual Studio の設定に基づいてコンパイルされます。

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 バージョン 16.5 以降でも、リモート開発のために、Linux システムへの安全な Federal Information Processing Standard (FIPS) 140-2 準拠の暗号化接続がサポートされています。 FISP 準拠の接続を使用するには、代わりに「[FIPS 準拠の安全なリモート Linux 開発のセットアップ](set-up-fips-compliant-secure-remote-linux-development.md)」のステップに従ってください。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>リモート システム上で SSH サーバーを設定する

Linux システム上でまだ ssh が設定および実行されていない場合、次のステップに従ってインストールします。 この記事の例では、Ubuntu 18.04 LTS と OpenSSH サーバー バージョン 7.6 を使用します。 ただし、比較的最近のバージョンの OpenSSH を使用する任意のディストリビューションでも同じ手順を使用できます。

1. Linux システム上で、OpenSSH サーバーをインストールして起動します。

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. システム起動時に自動的に ssh サーバーを起動したい場合、systemctl を使用して有効にします。

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>リモート接続を設定する

1. Visual Studio のメニュー バーで **[ツール] > [オプション]** を選択して、 **[オプション]** ダイアログを開きます。 その後、 **[クロス プラットフォーム] > [接続マネージャー]** を選択して [接続マネージャー] ダイアログを開きます。

   まだ Visual Studio で接続を設定したことがない場合、プロジェクトを初めてビルドする際に、Visual Studio によって [接続マネージャー] ダイアログが開かれます。

1. [接続マネージャー] ダイアログで、 **[追加]** ボタンを選択して新しい接続を追加します。

   ![接続マネージャー](media/settings_connectionmanager.png)

   いずれの場合も、 **[リモート システムへの接続]** ウィンドウが表示されます。

   ![リモート システムへの接続](media/connect.png)

1. 次の情報を入力します。

   | 入力 | 説明
   | ----- | ---
   | **ホスト名**           | ターゲット デバイスの名前または IP アドレス
   | **ポート**                | SSH サービスが実行されているポート (通常は 22)
   | **ユーザー名**           | 認証するユーザー
   | **認証の種類** | パスワードと秘密キーの両方がサポートされます
   | **パスワード**            | 入力したユーザー名のパスワード
   | **秘密キー ファイル**    | ssh 接続用に作成された秘密キー ファイル
   | **パスフレーズ**          | 上で選択した秘密キーで使用されるパスフレーズ

   認証には、パスワードまたはキー ファイルとパスフレーズを使用することができます。 多くの開発シナリオではパスワード認証で十分ですが、キー ファイルはさらに安全です。 既にキーの組があるなら、それを再利用できます。 現在、Visual Studio のリモート接続では RSA と DSA キーのみがサポートされています。

1. **[接続]** ボタンを選択すると、リモート コンピューターへの接続が試行されます。

   接続が成功すると、Visual Studio ではリモートのヘッダーを使うように IntelliSense が構成されます。 詳しくは、「[リモート システムのヘッダーでの IntelliSense](configure-a-linux-project.md#remote_intellisense)」をご覧ください。

   接続に失敗した場合は、変更する必要がある入力ボックスが赤色で示されます。

   ![接続マネージャーのエラー](media/settings_connectionmanagererror.png)

   キー ファイルを認証に使う場合は、ターゲット マシンの SSH サーバーが実行され、正しく構成されていることを確認します。

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>リモート接続のログを記録する

   ログを有効にして、接続の問題のトラブルシューティングに役立てることができます。 メニュー バーで、 **[ツール] > [オプション]** の順に選択します。 **[オプション]** ダイアログで、 **[クロス プラットフォーム] > [ログ]** を選択します。

   ![リモート ログ記録](media/remote-logging-vs2019.png)

   ログには、接続、リモート マシンに送信されたすべてのコマンド (そのテキスト、終了コード、実行時間)、および Visual Studio からシェルへのすべての出力が含まれます。 ログ記録は、Visual Studio でのすべてのクロスプラットフォーム CMake プロジェクトまたは MSBuild ベースの Linux プロジェクトで機能します。

   ファイルまたは出力ウィンドウの **[クロス プラットフォームのログ]** ペインに送られるように、出力を構成できます。 MSBuild ベースの Linux プロジェクトの場合、リモート マシンに送信された MSBuild コマンドは、プロセス外で出力されるため、 **[出力ウィンドウ]** にはルーティングされません。 代わりに、"msbuild_" というプレフィックスが付いたファイルに記録されます。

## <a name="command-line-utility-for-the-connection-manager"></a>接続マネージャーのコマンドライン ユーティリティ  

**Visual Studio 2019 バージョン 16.5 以降**:ConnectionManager.exe は、Visual Studio 外でのリモート開発の接続を管理するためのコマンドライン ユーティリティです。 これは、新しい開発マシンをプロビジョニングするなどのタスクに役立ちます。 または、これを利用して Visual Studio で継続的インテグレーションを設定することもできます。 ConnectionManager コマンドの例とすべてのリファレンスについては、「[ConnectionManager リファレンス](connectionmanager-reference.md)」を参照してください。  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>TCP ポート フォワーディング

Visual Studio の Linux サポートは、TCP ポート フォワーディングに依存しています。 リモート システムで TCP ポート フォワーディングが無効になっている場合、**Rsync** と **gdbserver** が影響を受けます。 お客様がこの依存関係の影響を受けている場合は、Developer Community でこちらの[提案チケット](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html)に賛成票を投じることができます。

rsync は、MSBuild ベースの Linux プロジェクトと CMake プロジェクトの両方で使用され、[IntelliSense で使用するヘッダーをリモート システムから Windows にコピーします](configure-a-linux-project.md#remote_intellisense)。 TCP ポート フォワーディングを有効にできない場合は、リモート ヘッダーの自動ダウンロードを無効にします。 無効にするには、 **[ツール] > [オプション]、[クロス プラットフォーム] > [接続マネージャー] > [リモート ヘッダー IntelliSense マネージャー]** の順に移動します。 リモート システムで TCP ポート フォワーディングが有効になっていない場合、IntelliSense のリモート ヘッダーのダウンロードが開始されると、次のエラーが表示されます。

![ヘッダー エラー](media/port-forwarding-headers-error.png)

rsync は、ソース ファイルをリモート システムにコピーするために、Visual Studio の CMake サポートでも使用されます。 TCP ポート フォワーディングを有効にできない場合は、リモート コピー ソース メソッドとして sftp を使用できます。 sftp は rsync よりも低速なことが多いですが、TCP ポート フォワーディングとの依存関係がありません。 [CMake 設定エディター](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)で、**remoteCopySourcesMethod** プロパティを使用してリモート コピー ソース メソッドを管理できます。 リモート システムで TCP ポート フォワーディングが無効になっている場合は、最初に rsync が呼び出されたときに CMake 出力ウィンドウにエラーが表示されます。

![Rsync エラー](media/port-forwarding-copy-error.png)

gdbserver は、埋め込みデバイスでのデバッグに使用できます。 TCP ポート フォワーディングを有効にできない場合は、すべてのリモート デバッグ シナリオで gdb を使用する必要があります。 リモート システム上のプロジェクトをデバッグする場合、既定で Gdb が使用されます。

## <a name="connect-to-wsl"></a>WSL に接続する

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 では、リモート Linux マシンに使用するのと同じ手順を使用して WSL に接続できます。 **ホスト名**には **localhost** を使います。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 バージョン 16.1 では、C++ を [Windows Subsystem for Linux (WSL)](/windows/wsl/about) とともに使用するためのネイティブ サポートが追加されています。 これは、ローカルの WSL インストールで直接ビルドおよびデバッグできることを意味します。 リモート接続を追加したり、SSH を構成したりする必要がなくなりました。 詳細については、こちらの [WSL をインストールする方法](/windows/wsl/install-win10)の説明をご覧ください。

Visual Studio と連携するように WSL インストールを構成するには、次のツールがインストールされている必要があります: gcc または clang、gdb、make、rsync、および zip。 次のコマンドを使うことで、apt が使われるディストリビューションにこれらをインストールできます。これによって g++ コンパイラもインストールされます。

```bash
sudo apt install g++ gdb make rsync zip
```

詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」をご覧ください。

WSL 用の MSBuild プロジェクトを構成するには、「[Linux プロジェクトを構成する](configure-a-linux-project.md)」を参照してください。 WSL 用の CMake プロジェクトを構成するには、[Linux CMake プロジェクトの構成](cmake-linux-project.md)に関する記事を参照してください。 WSL を使用するシンプルなコンソール アプリケーションを作成するための詳細な手順については、入門のブログ記事「[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)」 (C++ と Visual Studio 2019 および Windows Subsystem for Linux (WSL)) をご覧ください。

::: moniker-end

## <a name="see-also"></a>関連項目

[Linux プロジェクトを構成する](configure-a-linux-project.md)\
[Linux CMake プロジェクトを構成する](cmake-linux-project.md)\
[Linux プロジェクトの配置、実行、デバッグ](deploy-run-and-debug-your-linux-project.md)\
[CMake デバッグ セッションを構成する](../build/configure-cmake-debugging-sessions.md)
