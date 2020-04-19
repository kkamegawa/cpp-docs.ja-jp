---
title: FIPS 準拠の安全なリモート Linux 開発のセットアップ
description: リモート開発のために Visual Studio と Linux マシンとの間で FIPS 準拠の暗号化された接続を設定する方法を説明します。
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520463"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>FIPS 準拠の安全なリモート Linux 開発のセットアップ

::: moniker range="<=vs-2017"

Linux サポートは Visual Studio 2017 以降で使用できます。 FIPS 準拠の安全なリモート Linux 開発は、Visual Studio 2019 バージョン 16.5 以降で利用できます。

::: moniker-end

::: moniker range="vs-2019"

Federal Information Processing Standard (FIPS) パブリケーション 140-2 は、暗号化モジュールに関する米国政府の標準です。 標準の実装は、NIST によって検証されています。 Windows では、[FIPS 準拠の暗号化モジュールのサポートが検証](/windows/security/threat-protection/fips-140-validation)されています。 Visual Studio 2019 バージョン 16.5 以降では、リモート開発のために Linux システムへの安全な FIPS 準拠の暗号化された接続を使用できます。

ここでは、Visual Studio とリモート Linux システムとの間に、FIPS 準拠の安全な接続を設定する方法について説明します。 このガイドは、Visual Studio で CMake または MSBuild Linux プロジェクトをビルドする場合に適用されます。 この記事は、[リモート Linux コンピューターへの接続](connect-to-your-remote-linux-computer.md)に関する記事にある接続手順の、FIPS に準拠したバージョンです。

## <a name="prepare-a-fips-compliant-connection"></a>FIPS 準拠の接続を準備する

Visual Studio とリモート Linux システムとの間で FIPS 準拠の暗号化された安全な ssh 接続を使用するには、いくらかの準備が必要です。 FIPS-140-2 の準拠に関しては、Visual Studio は RSA キーのみをサポートしています。

この記事の例では、Ubuntu 18.04 LTS と OpenSSH サーバー バージョン 7.6 を使用します。 ただし、比較的最近のバージョンの OpenSSH を使用する任意のディストリビューションでも同じ手順を使用できます。

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>リモート システムで SSH サーバーを設定するには

1. Linux システム上で、OpenSSH サーバーをインストールして起動します。

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. システム起動時に自動的に ssh サーバーを起動したい場合、systemctl を使用して有効にします。

   ```bash
   sudo systemctl enable ssh
   ```

1. */etc/ssh/sshd_config* をルートとして開きます。 次の行を編集 (存在しない場合は追加) します。

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa は、VS がサポートする唯一の FIPS 準拠のホスト キー アルゴリズムです。 aes\*-ctr アルゴリズムも FIPS に準拠していますが、Visual Studio での実装は認められていません。 ecdh-\* キー交換アルゴリズムは FIPS に準拠していますが、Visual Studio ではサポートしていません。

   使用できるオプションはこれだけではありません。 追加の暗号、ホスト キー アルゴリズムなどを使用するように ssh を構成できます。 考慮すべき他の重要なセキュリティ オプションには、`PermitRootLogin`、`PasswordAuthentication`、`PermitEmptyPasswords` があります。 詳細については、sshd_config の man ページまたは[SSH サーバー構成](https://www.ssh.com/ssh/sshd_config)に関する記事を参照してください。

1. sshd_config を保存して閉じた後、ssh サーバーを再起動して新しい構成を適用します。

   ```bash
   sudo service ssh restart
   ```

次に、Windows コンピューターで RSA キーの組を作成します。 その後、ssh で使用できるように、公開キーをリモート Linux システムにコピーします。

### <a name="to-create-and-use-an-rsa-key-file"></a>RSA キー ファイルを作成して使用するには

1. Windows マシン上で、次のコマンドを使用して RSA の公開および秘密キーの組を生成します。

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   このコマンドにより、公開キーと秘密キーが作成されます。 既定では、キーは *%USERPROFILE%\\.ssh\\id_rsa* と *%USERPROFILE%\\.ssh\\id_rsa.pub* に保存されます。 (Powershell では、cmd マクロ `%USERPROFILE%` ではなく `$env:USERPROFILE` を使用してください) キーの名前を変更する場合、続くステップでは変更した名前を使用してください。  セキュリティを強化するために、パスフレーズを使用することをお勧めします。

1. Windows から、Linux マシンに公開キーをコピーします。

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. Linux システムで、承認済みキーのリストにキーを追加し、ファイルに適切なアクセス許可があることを確認します。

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. これで、新しいキーを ssh で使用できるかをテストできます。 Windows からのサインインに使用します。

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

正常に ssh を設定し、暗号化キーを作成および配置し、接続をテストできました。 これで Visual Studio 接続を設定する準備が整いました。

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Visual Studio でリモート システムに接続する

1. Visual Studio のメニュー バーで **[ツール] > [オプション]** を選択して、 **[オプション]** ダイアログを開きます。 その後、 **[クロス プラットフォーム] > [接続マネージャー]** を選択して [接続マネージャー] ダイアログを開きます。

   まだ Visual Studio で接続を設定したことがない場合、プロジェクトを初めてビルドする際に、Visual Studio によって [接続マネージャー] ダイアログが開かれます。

1. [接続マネージャー] ダイアログで、 **[追加]** ボタンを選択して新しい接続を追加します。

   ![接続マネージャー](media/settings_connectionmanager.png)

   **[リモート システムへの接続]** ウィンドウが表示されます。

   ![リモート システムへの接続](media/connect.png)

1. **[リモートシステムへの接続]** ダイアログで、リモート マシンの接続の詳細を入力します。

   | 入力 | 説明
   | ----- | ---
   | **ホスト名**           | ターゲット デバイスの名前または IP アドレス
   | **ポート**                | SSH サービスが実行されているポート (通常は 22)
   | **ユーザー名**           | 認証するユーザー
   | **認証の種類** | FIPS 準拠の接続のための秘密キーを選択します
   | **秘密キー ファイル**    | ssh 接続用に作成された秘密キー ファイル
   | **パスフレーズ**          | 上で選択した秘密キーで使用されるパスフレーズ

   認証の種類を**秘密キー**に変更します。 **[秘密キー ファイル]** フィールドに秘密キーへのパスを入力します。 **[参照]** ボタンを使用して秘密キー ファイルを探すこともできます。 その後、 **[パスフレーズ]** フィールドに、秘密キー ファイルを暗号化するために使用するパスフレーズを入力します。

1. **[接続]** ボタンを選択すると、リモート コンピューターへの接続が試行されます。

   接続が成功すると、Visual Studio ではリモートのヘッダーを使うように IntelliSense が構成されます。 詳しくは、「[リモート システムのヘッダーでの IntelliSense](configure-a-linux-project.md#remote_intellisense)」をご覧ください。

   接続に失敗した場合は、変更する必要がある入力ボックスが赤色で示されます。

   ![接続マネージャーのエラー](media/settings_connectionmanagererror.png)

   接続のトラブルシューティングの詳細については、[リモートの Linux コンピューターへの接続](connect-to-your-remote-linux-computer.md)に関するページを参照してください。

## <a name="command-line-utility-for-the-connection-manager"></a>接続マネージャーのコマンドライン ユーティリティ  

**Visual Studio 2019 バージョン 16.5 以降**:ConnectionManager.exe は、Visual Studio 外でのリモート開発の接続を管理するためのコマンドライン ユーティリティです。 これは、新しい開発マシンをプロビジョニングするなどのタスクに役立ちます。 または、これを利用して Visual Studio で継続的インテグレーションを設定することもできます。 ConnectionManager コマンドの例とすべてのリファレンスについては、「[ConnectionManager リファレンス](connectionmanager-reference.md)」を参照してください。  

## <a name="optional-enable-or-disable-fips-mode"></a>省略可能:FIPS モードを有効または無効にする

Windows で FIPS モードをグローバルに有効にすることができます。

1. FIPS モードを有効にするには、**Windows+R** を押して [ファイル名を指定して実行] ダイアログを開き、gpedit.msc を実行します。

1. **[ローカル コンピューター ポリシー] > [コンピューターの構成] > [Windows の設定] > [セキュリティの設定] > [ローカル ポリシー]** を展開して、 **[セキュリティ オプション]** を選択します。

1. **[ポリシー]** の下で、 **[システム暗号化: 暗号化、ハッシュ、署名のための FIPS 準拠アルゴリズムを使う]** を選択し、**Enter** を押してそのダイアログ ボックスを開きます。

1. **[ローカル セキュリティの設定]** タブで、 **[有効]** または **[無効]** を選択した後、**OK** を選択して変更を保存します。

> [!WARNING]
> FIPS モードを有効にすると、アプリケーションによっては中断したり予想外の動作をしたりすることがあります。 詳細については、ブログ記事「["FIPS モード" をお勧めしない理由](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)」を参照してください。

## <a name="additional-resources"></a>その他の技術情報

[FIPS 140 の検証に関する Microsoft ドキュメント](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2:Security Requirements for Cryptographic Modules \(FIPS 140-2:暗号化モジュールのためのシステム要件\)](https://csrc.nist.gov/publications/detail/fips/140/2/final) (NIST のサイト)

[Cryptographic Algorithm Validation Program:Validation Notes \(暗号化アルゴリズム検証プログラム: 検証についての注記\)](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (NIST のサイト)

「["FIPS モード" をお勧めしない理由](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)」の Microsoft のブログ記事

[SSH サーバーの構成](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>関連項目

[Linux プロジェクトを構成する](configure-a-linux-project.md)\
[Linux CMake プロジェクトを構成する](cmake-linux-project.md)\
[リモートの Linux コンピューターに接続する](connect-to-your-remote-linux-computer.md)\
[Linux プロジェクトの配置、実行、デバッグ](deploy-run-and-debug-your-linux-project.md)\
[CMake デバッグ セッションを構成する](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
