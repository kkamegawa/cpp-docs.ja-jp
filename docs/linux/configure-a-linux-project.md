---
title: Visual Studio で C++ Linux プロジェクトを構成する
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 5d42ca587946d3b5adcbd3b6fe35a6c1e1bb9ae8
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031371"
---
# <a name="configure-a-linux-project"></a>Linux プロジェクトを構成する

::: moniker range="vs-2015"

Linux サポートは Visual Studio 2017 以降で使用できます。

::: moniker-end

このトピックでは、[Visual Studio での新しい C++ Linux プロジェクトの作成](create-a-new-linux-project.md)に関するページで示されているように、C++ Linux プロジェクトを構成する方法について説明します。 CMake Linux プロジェクトについては、「[Linux CMake プロジェクトを構成する](cmake-linux-project.md)」を参照してください。 

物理的な Linux マシン、仮想マシン、または [Windows Subsystem for Linux](/windows/wsl/about) (WSL) を対象にするように、Linux プロジェクトを構成できます。 

::: moniker range="vs-2019"

**Visual Studio 2019 バージョン 16.1**:

- WSL を対象にしている場合、リモートの Linux システムを対象にしているときにビルドと IntelliSense に必要なコピー操作を回避することができます。

- ビルドとデバッグに別の Linux ターゲットを指定できます。

::: moniker-end

## <a name="general-settings"></a>全般設定

構成オプションを表示するには、 **[プロジェクト]、[プロパティ]** メニューの順に選択するか、**ソリューション エクスプローラー**でプロジェクトを右クリックし、コンテキスト メニューから **[プロパティ]** を選択します。 **[全般]** 設定が表示されます。

![全般構成](media/settings_general.png)

既定では、実行可能ファイル (.out) がビルドされます。 静的または動的なライブラリをビルドする場合や、既存のメイクファイルを使用する場合は、 **[構成の種類]** 設定を使用します。

プロパティ ページの設定に関する詳細については、「[Linux プロジェクト プロパティ ページの参照](prop-pages-linux.md)」を参照してください。

## <a name="remote-settings"></a>リモート設定

リモート Linux コンピューターに関連する設定を変更するには、[[全般]](prop-pages/general-linux.md) に表示されるリモート設定を構成します。

- リモートのターゲット Linux コンピューターを指定するには、 **[リモート ビルド マシン]** エントリを使用します。 これによって、以前に作成された接続のいずれかを選択できます。 新しいエントリを作成する場合は、[リモートの Linux コンピューターへの接続](connect-to-your-remote-linux-computer.md)に関するセクションを参照してください。

   ![ビルド マシン](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 バージョン 16.1**: Windows Subsystem for Linux を対象にするには、 **[プラットフォーム ツールセット]** の下向きの矢印をクリックして、 **[WSL_1_0]** を選びます。 その他のリモート オプションは消え、既定の WSL シェルへのパスが代わりに表示されます。

   ![WSL ビルド マシン](media/wsl-remote-vs2019.png)

   サイド バイ サイドの WSL インストールがある場合は、ここで別のパスを指定できます。 複数の配布の管理に関する詳細については、「[Manage and configure Windows Subsystem for Linux](/windows/wsl/wsl-config#set-a-default-distribution)」(Windows Subsystem for Linux の管理と構成) を参照してください。

   **[構成プロパティ]** > **[デバッグ]** ページで、デバッグに異なるターゲットを指定できます。

   ::: moniker-end

- **[リモート ビルド ルート ディレクトリ]** で、リモートの Linux コンピューター上のプロジェクトを構築するルート場所が決定します。 これは、変更しない限り、既定で **~/projects** に設定されます。

- **[リモート ビルド プロジェクト ディレクトリ]** は、リモートの Linux コンピューターでこの特定のプロジェクトが構築される場所です。 これは、既定で **$(RemoteRootDir)/$(ProjectName)** に設定され、上で設定したルート ディレクトリ下の、現在のプロジェクトから名前が付けられたディレクトリに展開されます。

> [!NOTE]
> 既定の C および C++ コンパイラ、またはプロジェクトのビルドに使用したリンカーとアーカイバーを変更する場合は、 **[C/C++]、[全般]** セクションと **[リンカー]、[全般]** セクションで適切なエントリを使用します。 たとえば、GCC や Clang の特定のバージョンを指定できます。 詳細については、「[C/C++ プロパティ (Linux C++)](prop-pages/c-cpp-linux.md)」と「[リンカー プロパティ (Linux C++)](prop-pages/linker-linux.md)」を参照してください。

## <a name="copy-sources-remote-systems-only"></a>ソースのコピー (リモート システムのみ)

::: moniker range="vs-2019"

このセクションは、WSL を対象とするときには適用されません。

::: moniker-end

リモート システムのビルド時に、開発用 PC 上のソース ファイルは、Linux コンピューターにコピーされ、そこでコンパイルされます。 既定では、Visual Studio プロジェクトのすべてのソースは、上記の設定で指定された場所にコピーされます。 ただし、リストにさらにソースを追加するこもできます。あるいは、ソースのコピーを完全にオフ (メイクファイル プロジェクトではこれが既定) にすることもできます。

- **[コピーするソース]** で、リモート コンピューターにコピーするソースが決定します。 既定では、 **\@(SourcesToCopyRemotely)** はプロジェクトのすべてのソース コード ファイルの規定値ですが、画像などの資産ファイルやリソースファイルは含まれません。

- **[ソースのコピー]** をオンまたはオフにして、リモート コンピューターへのソース ファイルのコピーを有効または無効にすることができます。

- **[コピーする追加ソース]** では、リモート システムにコピーするソース ファイルを追加することができます。 セミコロンで区切ったリストを指定することも、次のように、 **:=** 構文で使用するローカルおよびリモート名を指定することもできます。

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>ビルド イベント

すべてのコンパイルはリモート コンピューター (または WSL) で実行されるため、プロジェクト プロパティの [ビルド イベント] セクションにいくつかのビルド イベントが追加されています。 追加されたのは **[リモートのビルド前イベント]** 、 **[リモートのリンク前イベント]** 、 **[リモートのビルド後イベント]** で、リモート コンピューターでプロセスの個々のステップの前後に発生します。

![ビルド イベント](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> リモート システムのヘッダーでの IntelliSense

**接続マネージャー**で新しい接続を追加すると、Visual Studio によってリモート システム上のコンパイラのインクルード ディレクトリが自動的に検出されます。 Visual Studio によってこれらのファイルが圧縮されて、お使いのローカル Windows コンピューター上のディレクトリにコピーされます。 その後、Visual Studio または CMake プロジェクトでその接続を使用するたびに、IntelliSense を提供するためにこれらのディレクトリ内のヘッダーが使用されます。

> [!NOTE]
> Visual Studio 2019 バージョン 16.5 以降では、リモート ヘッダーのコピーが最適化されています。 Linux プロジェクトを開くとき、または Linux ターゲットに合わせて CMake を構成するときに、ヘッダーがオンデマンドでコピーされるようになりました。 コピーは、プロジェクトに指定されたコンパイラに基づいて、プロジェクトごとにバックグラウンドで実行されます。 詳細については、「[Linux IntelliSense の精度とパフォーマンスの改善点](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/)」を参照してください。

この機能は、Linux コンピューターにインストールされている zip に依存します。 この apt-get コマンドを使用して、zip をインストールできます。

```cmd
sudo apt install zip
```

ヘッダーのキャッシュを管理するには、 **[ツール] > [オプション]、[クロス プラットフォーム] > [接続マネージャー] > [リモート ヘッダー IntelliSense マネージャー]** の順に移動します。 Linux コンピューターに変更を行った後にヘッダー キャッシュ更新するには、リモート接続を選択してから、 **[更新]** を選択します。 接続自体を削除せずにヘッダーを削除するには、 **[削除]** を選択します。 **ファイル エクスプローラー**でローカル ディレクトリを開くには、 **[探索]** を選択します。 このフォルダーを読み取り専用として扱います。 Visual Studio 2017 バージョン 15.3 より前に作成された既存の接続用にヘッダーをダウンロードするには、その接続を選択し、 **[ダウンロード]** を選択します。

::: moniker range="vs-2017"

![リモート ヘッダー IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![リモート ヘッダー IntelliSense](media/connection-manager-vs2019.png)

ログ記録を有効にして、問題のトラブルシューティングに役立てることができます。

![リモート ログ記録](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>関連項目

[コンパイラとビルドのプロパティの設定](../build/working-with-project-properties.md)<br/>
[C++ 全般プロパティ (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[VC++ ディレクトリ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[ソースのプロジェクト プロパティのコピー (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[ビルド イベント プロパティ (Linux C++)](../linux/prop-pages/build-events-linux.md)
