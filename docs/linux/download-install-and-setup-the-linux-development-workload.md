---
title: Visual Studio で C++ の Linux ワークロードをインストールする
description: Visual Studio で C++ の Linux ワークロードをダウンロード、インストール、セットアップする方法について説明します。
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 1dad17756cbc12fdf65250b7c54314ff2a645287
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966211"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Linux ワークロードのダウンロード、インストール、セットアップ

::: moniker range="vs-2015"

Linux プロジェクトは Visual Studio 2017 以降でサポートされます。

::: moniker-end

::: moniker range=">=vs-2017"

Windows 上の Visual Studio IDE を使って、リモートの Linux システムや、仮想マシン、または [Windows Subsystem for Linux](/windows/wsl/about) 上で実行される C++ プロジェクトの作成、編集、およびデバッグを行うことができます。 

Visual Studio プロジェクトに変換しなくても、CMake を使用する既存のコード ベースで作業できます。 コード ベースがクロス プラットフォームの場合、Visual Studio 内から Windows と Linux の両方をターゲット設定できます。 たとえば、Windows 上で Visual Studio を使ってコードの編集、ビルド、デバッグを行った後、すぐにそのプロジェクトのターゲットを Linux に変更して Linux 環境内でビルドとデバッグを行うことができます。 Linux 用のヘッダー ファイルがローカル コンピューターに自動的にコピーされます。そこで Visual Studio によってそれらが使用され、IntelliSense の完全なサポート (ステートメント入力候補、定義へ移動など) が提供されます。 
 
これらのどのシナリオについても、**C++ による Linux 開発**ワークロードが必要です。 

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio のセットアップ

1. Windows 検索ボックスに「Visual Studio インストーラー」と入力します。

   ![Windows 検索ボックス](media/visual-studio-installer-search.png)

2. **アプリ**の結果でインストーラーを探し、それをダブルクリックします。 インストーラーが開いたら、 **[変更]** を選択して **[ワークロード]** タブをクリックします。 **[Other toolsets]\(その他のツールセット\)** まで下へスクロールして、 **[C++ による Linux 開発]** ワークロードを選択します。

   ![Visual C++ for Linux Development ワークロード](media/linuxworkload.png)

1. IoT または組み込みのプラットフォームをターゲットにしている場合は、右側の **[インストールの詳細]** ウィンドウに移動します。 **[C++ による Linux 開発]** の下で **[オプション コンポーネント]** を展開し、必要なコンポーネントを選択します。 Linux で CMake は既定でサポートされるよう選択されています。

1. **[変更]** をクリックして、インストールを続行します。

## <a name="options-for-creating-a-linux-environment"></a>Linux 環境を作成するためのオプション

Linux マシンがまだない場合は、Azure で Linux 仮想マシンを作成できます。 詳細については、「[クイック スタート: Azure portal で Linux 仮想マシンを作成する](/azure/virtual-machines/linux/quick-create-portal)」を参照してください。

Windows 10 の Windows Subsystem for Linux (WSL) では、お好みの Linux ディストリビューションをインストールして、対象とすることができます。 詳細については、「[Windows Subsystem for Linux Installation Guide for Windows 10](/windows/wsl/install-win10)」 (Windows 10 用の Windows Subsystem for Linux のインストール ガイド) を参照してください。 Windows ストアにアクセスできない場合は、[WSL ディストリビューション パッケージを手動でダウンロードする](/windows/wsl/install-manual)ことができます。 WSL は便利なコンソール環境ですが、グラフィック アプリケーション用には推奨されません。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio の Linux プロジェクトを使用する場合、リモートの Linux システムまたは WSL に次の依存関係がインストールされている必要があります。

- **コンパイラ** - Visual Studio 2019 では、GCC と [Clang](/cpp/build/clang-support-cmake?view=vs-2019) が最初からサポートされています。
- **gdb** - Visual Studio によって Linux システム上の gdb が自動的に起動され、Visual Studio デバッガーのフロントエンドを使用した、Linux 上の完全に忠実なデバッグ エクスペリエンスが提供されます。
- **rsync** および **zip** - rsync と zip を含めることにより、IntelliSense で使用するためのヘッダー ファイルを、Visual Studio が Linux システムから Windows ファイルシステムに抽出できるようになります。
- **make**
- **openssh-server** (リモートの Linux システムのみ) - Visual Studio は、セキュリティで保護された SSH 接続を介してリモートの Linux システムに接続します。
- **CMake** (CMake プロジェクトのみ) - Microsoft の[静的にリンクされた Linux 用 CMake バイナリ](https://github.com/microsoft/CMake/releases)をインストールできます。

以下のコマンドでは、clang ではなく g++ を使っていることを前提としています。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio の Linux プロジェクトを使用する場合、リモートの Linux システムまたは WSL に次の依存関係がインストールされている必要があります。

- **gcc** - Visual Studio 2017 では、GCC が最初からサポートされています。
- **gdb** - Visual Studio によって Linux システム上の gdb が自動的に起動され、Visual Studio デバッガーのフロントエンドを使用した、Linux 上の完全に忠実なデバッグ エクスペリエンスが提供されます。
- **rsync** および **zip** - rsync と zip を含めることにより、IntelliSense で使用するためのヘッダー ファイルを、Visual Studio が Linux システムから Windows ファイルシステムに抽出できるようになります。
- **make**
- **openssh-server** - Visual Studio は、セキュリティで保護された SSH 接続を介してリモートの Linux システムに接続します。
- **CMake** (CMake プロジェクトのみ) - Microsoft の[静的にリンクされた Linux 用 CMake バイナリ](https://github.com/microsoft/CMake/releases)をインストールできます。

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux のセットアップ: WSL 上の Ubuntu

WSL をターゲットにしている場合は、ビルドとデバッグを行うためにリモート接続を追加したり、SSH を構成したりする必要はありません。 Intellisense のサポートで Linux のヘッダーを Visual Studio と自動的に同期するには、**zip** と **rsync** が必要です。 必要なアプリケーションがまだない場合は、次の手順でインストールできます。

```bash
sudo apt-get install g++ gdb make rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>リモートの Linux システム上の Ubuntu

ターゲットの Linux システムには、**openssh-server**、**g++** 、**gdb**、**make** がインストールされていて、ssh デーモンが実行されている必要があります。 Intellisense サポート対応のローカル コンピューターでリモート ヘッダーを自動同期するには、**zip** と **rsync** が必須です。 これらのアプリケーションがまだない場合は、次の手順でインストールできます。

1. Linux コンピューターのシェル プロンプトで次のコマンドを実行します。

   ```bash
   sudo apt-get install openssh-server g++ gdb make rsync zip
   ```

   sudo コマンドにより、root パスワードの入力を求められる場合があります。  その場合は、入力して続行します。 完了すると、必要なサービスとツールがインストールされます。

1. 次のコマンドを実行し、Linux コンピューターで ssh サービスを実行します。

   ```bash
   sudo service ssh start
   ```

   サービスが開始され、バックグラウンドで実行され、接続を受け付けられる状態になります。

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>WSL 上の Fedora

Fedora は、**dnf** パッケージ インストーラーを使用しています。 **g++** 、**gdb**、**make**、**rsync**、および **zip** をダウンロードするには、次を実行します。

   ```bash
   sudo dnf install gcc-g++ gdb rsync make zip
   ```

Intellisense のサポートで Linux のヘッダーを Visual Studio と自動的に同期するには、**zip** と **rsync** が必要です。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>リモートの Linux システム上の Fedora

Fedora を実行しているターゲット マシンで **dnf** パッケージ インストーラーを使用します。 **openssh-server**、**g++** 、**gdb**、**make**、**rsync**、および **zip** をダウンロードし、ssh デーモンを再起動するには、次の手順に従います。

1. Linux コンピューターのシェル プロンプトで次のコマンドを実行します。

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb make rsync zip
   ```

   sudo コマンドにより、root パスワードの入力を求められる場合があります。  その場合は、入力して続行します。 完了すると、必要なサービスとツールがインストールされます。

1. 次のコマンドを実行し、Linux コンピューターで ssh サービスを実行します。

   ```bash
   sudo systemctl start sshd
   ```

   サービスが開始され、バックグラウンドで実行され、接続を受け付けられる状態になります。

::: moniker-end

::: moniker range="vs-2015"

Linux での C++ での開発は Visual Studio 2017 以降でサポートされています。

::: moniker-end

## <a name="next-steps"></a>次の手順

これで Linux プロジェクトを作成するか開いて、ターゲット システム上で実行できるように構成する準備が整いました。 詳細については次を参照してください:

- [新しい Linux プロジェクトを作成する](create-a-new-linux-project.md)
- [Linux CMake プロジェクトを構成する](cmake-linux-project.md)
