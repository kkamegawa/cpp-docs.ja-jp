---
title: Visual Studio の CMake プロジェクト
description: Visual Studio で CMake C++を使用してプロジェクトを作成およびビルドする方法。
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: be252759e93eb30d4f9b4ff1446dd4217fcdf2a6
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791831"
---
# <a name="cmake-projects-in-visual-studio"></a>Visual Studio の CMake プロジェクト

CMake は、複数のプラットフォームで動作するビルド プロセスを定義するためのクロスプラットフォームのオープン ソース ツールです。 この記事では、CMake について理解していることを前提としています。 詳細については、「[Build, Test and Package Your Software With CMake](https://cmake.org/)」 (CMake を使用してソフトウェアをビルド、テスト、パッケージ化する) を参照してください。

> [!NOTE]
> CMake は、過去数回のリリースで Visual Studio との統合性が向上しました。 使用しているバージョンの正しい情報を表示するには、このページの左上にあるバージョンセレクターが正しく設定されていることを確認します。

::: moniker range="vs-2019"

**C++ Windows 用の cmake ツール**コンポーネントでは、 [[フォルダーを開く](open-folder-projects-cpp.md)] 機能を使用して、IntelliSense とブラウズの目的で cmake プロジェクトファイル ( *cmakelists*など) を直接使用します。 Ninja と Visual Studio ジェネレーターはどちらもサポートされています。 Visual Studio ジェネレーターを使用すると、一時プロジェクトファイルが生成され、msbuild.exe に渡されます。 ただし、IntelliSense や閲覧目的でプロジェクトが読み込まれることはありません。 既存の CMake キャッシュをインポートすることもできます。

## <a name="installation"></a>のインストール

**C++**  **C++ Windows 用の cmake ツール**は、ワークロードを使用したおよび Linux 開発**でC++のデスクトップ開発**の一部としてインストールされます。 詳細については、「[クロスプラットフォームの CMake プロジェクト](../linux/cmake-linux-project.md)」を参照してください。

![C++ デスクトップ ワークロードでの CMake コンポーネント](media/cmake-install-2019.png)

詳細については、「[Install the C++ Linux workload in Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md)」(Visual Studio で C++ の Linux ワークロードをインストールする) を参照してください。

## <a name="ide-integration"></a>IDE の統合

**ファイル > > フォルダーを開い**て、 *cmakelists .txt*ファイルを含むフォルダーを開くと、次の処理が行われます。

- Visual Studio によって**cmake**項目が **[プロジェクト]** メニューに追加され、cmake スクリプトを表示および編集するためのコマンドが追加されます。

- **ソリューション エクスプローラー**に、フォルダーの構造とファイルが表示されます。

- Visual Studio によって cmake .exe が実行され、既定の (x64 デバッグ) 構成の CMake キャッシュファイル (*cmakecache.txt*) が生成されます。 CMake コマンド ラインおよび CMake からの追加出力が、**出力ウィンドウ**に表示されます。

- Visual Studio は、IntelliSense、情報の参照、リファクタリングなどを有効にするためのソース ファイルのインデックス付けを、バックグラウンドで開始します。 ユーザーが作業を行っている間、Visual Studio は、エディターおよびディスク上での変更を監視し、インデックスとソースの同期を維持します。

開くフォルダーに含まれる CMake プロジェクトの数は制限されていません。 Visual Studio は、ワークスペース内のすべての "ルート" の*Cmakelists .txt*ファイルを検出して構成します。 CMake 操作 (構成、ビルド、デバッグ)、 C++ IntelliSense、および参照は、ワークスペース内のすべての cmake プロジェクトで使用できます。

![複数のルートを持つ CMake プロジェクト](media/cmake-multiple-roots.png)

ターゲットごとに論理的にまとめられたプロジェクトを参照することも可能です。 **ソリューション エクスプローラー** ツールバーのドロップダウンから、 **[ターゲット ビュー]** を選択します。

![CMake ターゲット ビュー ボタン](media/cmake-targets-view.png)

**ソリューションエクスプローラー**の上部にある **[すべてのファイルを表示]** ボタンをクリックして、 *out/build/\<Config >* フォルダー内の cmake によって生成されたすべての出力を表示します。

Visual Studio では、 **Cmakesettings. json**という構成ファイルを使用します。 このファイルを使用すると、複数のビルド構成を定義して格納し、IDE でそれらを簡単に切り替えることができます。 *構成*は、特定のビルドの種類に固有の設定をカプセル化する Visual Studio の構造体です。 この設定は、Visual Studio が cmake .exe に渡す既定のコマンドラインオプションを構成するために使用されます。 ここで追加の CMake オプションを指定し、必要に応じて追加の変数を定義することもできます。 すべてのオプションは、内部変数または外部変数として CMake キャッシュに書き込まれます。 Visual Studio 2019 では、 **Cmake 設定エディター**は、設定を編集するための便利な方法を提供します。 詳細については、「[Customize CMake settings](customize-cmake-settings.md)」 (CMake 設定のカスタマイズ) を参照してください。

1つの設定 (`intelliSenseMode` は CMake に渡されませんが、Visual Studio でのみ使用されます。

CMake プロジェクトの場合と同様に、各プロジェクトフォルダーで**Cmakelists .txt**ファイルを使用します。 ソースファイルを指定したり、ライブラリを検索したり、コンパイラオプションとリンカーオプションを設定したり、ビルドシステムに関連する他の情報を指定したりすることができます。

デバッグ時に実行可能ファイルに引数を渡すには、 **launch**という別のファイルを使用できます。 場合によっては、Visual Studio によってこれらのファイルが自動的に生成されます。 手動で編集することも、自分でファイルを作成することもできます。

> [!NOTE]
> その他の種類の開いているフォルダープロジェクトでは、 **Cppproperties. json**と**tasks. json**の2つの追加の json ファイルが使用されます。 これらはいずれも CMake プロジェクトには関連していません。

## <a name="open-an-existing-cache"></a>既存のキャッシュを開く

既存の CMake キャッシュファイル (*cmakecache.txt*) を開くと、Visual Studio はキャッシュとビルドツリーの管理を試行しません。 カスタムツールまたは優先するツールを使用すると、CMake によってプロジェクトがどのように構成されるかを完全に制御できます。 Visual Studio で既存のキャッシュを開くには、[ファイル] を選択し **> CMake > 開き**ます。 次に、既存の*cmakecache.txt*ファイルに移動します。

開いているプロジェクトに既存の CMake キャッシュを追加できます。 新しい構成を追加するのと同じ方法で行います。 詳細については、 [Visual Studio での既存のキャッシュのオープン](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)に関するブログ記事を参照してください。

## <a name="building-cmake-projects"></a>CMake プロジェクトのビルド

CMake プロジェクトをビルドするには、次の選択肢があります。

1. 全般 ツールバーで、**構成** ドロップダウンを見つけます。 既定では、"x64-Debug" と表示されることがあります。 優先する構成を選択し、 **F5**キーを押すか、ツールバーの **[実行]** (緑色の三角形) ボタンをクリックします。 Visual Studio ソリューションと同じように、プロジェクトは最初に自動的にビルドされます。

1. *Cmakelists*を右クリックし、コンテキストメニューから **[ビルド]** を選択します。 フォルダー構造内に複数のターゲットがある場合は、すべてをビルドするか、特定の 1 つのターゲットだけをビルドするかを選べます。

1. メインメニューから **[ビルド > ビルド]** を選択します (**F7**キーまたは**Ctrl + Shift + B**キーを押します)。 **[全般]** ツール バーの **[スタートアップ アイテム]** ドロップダウンで CMake ターゲットが既に選択されていることを確認します。

![CMake ビルドメニューコマンド](media/cmake-build-menu.png "CMake ビルドコマンドメニュー")

想像したとおり、ビルド結果が**出力ウィンドウ**と**エラー一覧**に表示されます。

![CMake ビルドエラー](media/cmake-build-errors.png "CMake ビルドエラー")

複数のビルドターゲットがあるフォルダーでは、ビルドする CMake ターゲットを指定できます。 **cmake**メニューまたは*cmakelists .txt*コンテキストメニューの **[ビルド]** 項目を選択して、ターゲットを指定します。 CMake プロジェクトで**Ctrl + Shift + B キーを押す**と、現在アクティブなドキュメントがビルドされます。

## <a name="debugging-cmake-projects"></a>CMake プロジェクトのデバッグ

CMake プロジェクトをデバッグするには、優先する構成を選択し、 **F5**キーを押すか、ツールバーの **[実行]** ボタンを押します。 **[実行]** ボタンに "スタートアップ項目の選択" と表示されている場合は、ドロップダウン矢印を選択します。 実行するターゲットを選択します。 (CMake プロジェクトでは、[現在のドキュメント] オプションは .cpp ファイルの場合にのみ有効です)。

![CMake の [実行] ボタン](media/cmake-run-button.png "CMake の [実行] ボタン")

**[実行]** または **F5** コマンドを選ぶと、前回のビルドの後で何かが変更されている場合は、最初にプロジェクトがビルドされます。 *Cmakesettings. json*を変更すると、cmake キャッシュが再生成されます。

CMake デバッグセッションをカスタマイズするには、**起動. と json**ファイルのプロパティを設定します。 詳細については、[CMake デバッグ セッションの構成](configure-cmake-debugging-sessions.md)に関するページを参照してください。

## <a name="just-my-code-for-cmake-projects"></a>CMake プロジェクトのマイコードのみ

MSVC コンパイラを使用して Windows 用にビルドすると、CMake プロジェクトでマイコードのみデバッグがサポートされるようになります。 マイコードのみ設定を変更するには、**ツール**、オプション、**デバッグ** > **全般** の >  > **オプション** に移動します。

## <a name="vcpkg-integration"></a>Vcpkg の統合

[Vcpkg](vcpkg.md)がインストールされている場合、Visual Studio で開かれた cmake プロジェクトは、vcpkg ツールチェーンファイルを自動的に統合します。 つまり、CMake プロジェクトで vcpkg を使用するために追加の構成は必要ありません。 このサポートは、対象とするリモートシステム上のローカル vcpkg インストールと vcpkg インストールの両方で機能します。 CMake 設定の構成で他のツールチェーンを指定すると、この動作は自動的に無効になります。

## <a name="customize-configuration-feedback"></a>構成に関するフィードバックをカスタマイズする

既定では、エラーが発生しない限り、ほとんどの構成メッセージが抑制されます。 すべてのメッセージを表示するには、 **[ツール]**  > [オプション > **cmake** **]** でこの機能を有効にします。

   ![CMake 診断オプションを構成する](media/vs2019-cmake-configure-options.png "CMake 診断オプション")

## <a name="editing-cmakeliststxt-files"></a>CMakeLists.txt ファイルの編集

*Cmakelists .txt*ファイルを編集するには、**ソリューションエクスプローラー**でファイルを右クリックし、 **[開く]** を選択します。 ファイルに変更を加えると、黄色のステータスバーが表示され、IntelliSense が更新されることが通知されます。 更新操作を取り消すことができます。 *Cmakelists*の詳細については、 [cmake のドキュメント](https://cmake.org/documentation/)を参照してください。

   ![CMakeLists .txt ファイルの編集](media/cmake-cmakelists.png "CMakeLists .txt ファイルの編集")

ファイルを保存するとすぐに構成手順が自動的に再び実行され、 **[出力]** ウィンドウに情報が表示されます。 エラーと警告は、 **[エラー一覧]** または **[出力]** ウィンドウに表示されます。 **エラー一覧**のエラーをダブルクリックして、 *cmakelists*の問題のある行に移動します。

   ![CMakeLists .txt ファイルエラー](media/cmake-cmakelists-error.png "CMakeLists .txt ファイルエラー")

## <a name="cmake-configure-step"></a>CMake の構成ステップ

*Cmakesettings. json*ファイルまたは*cmakesettings .txt*ファイルに大幅な変更を加えると、Visual Studio は自動的に cmake 構成手順を再実行します。 構成手順がエラーなしで終了した場合、収集された情報C++は IntelliSense および言語サービスで利用できます。 ビルドおよびデバッグ操作でも使用されます。

## <a name="troubleshooting-cmake-cache-errors"></a>CMake キャッシュ エラーのトラブルシューティング

問題を診断するための CMake キャッシュの状態に関する詳細情報が必要な場合は、次のいずれかのコマンドを実行するために、**ソリューションエクスプローラー**の**プロジェクト**のメインメニューまたは*cmakelists .txt*コンテキストメニューを開きます。

- **[キャッシュの表示]** では、エディターのビルドルートフォルダーから*cmakecache.txt*ファイルが開きます。 (ここで*cmakecache.txt*に対して行った編集は、キャッシュを消去すると消去されます。 キャッシュをクリーニングした後も変更を保持するには、「 [CMake の設定をカスタマイズ](customize-cmake-settings.md)する」を参照してください)。

- **[キャッシュ フォルダーを開く]** は、エクスプローラー ウィンドウでビルド ルート フォルダーを開きます。

- **[キャッシュをクリーン]** は、次の CMake 構成ステップがクリーンなキャッシュから開始されるように、ビルド ルート フォルダーを削除します。

- **キャッシュの生成**を実行すると、Visual Studio によって環境が最新であると見なされる場合でも、生成ステップが強制的に実行されます。

自動キャッシュ生成は、 **CMake > 全般ダイアログ > の [ツール] > オプション**で無効にすることができます。

## <a name="run-cmake-from-the-command-line"></a>コマンド ラインから CMake を実行する

Visual Studio インストーラーから CMake をインストールした場合は、次の手順に従ってコマンド ラインから実行できます。

1. 適切な vsdevcmd.bat (x86 または x64) を実行します。 詳細については、「[コマンドラインでのビルド](building-on-the-command-line.md)」を参照してください。

1. 出力フォルダーに移動します。

1. CMake を実行してアプリをビルド/構成します。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 では、[クロスプラットフォームの cmake プロジェクト](../linux/cmake-linux-project.md)を含む cmake が豊富にサポートされています。 **Visual C++ Tools for cmake**コンポーネントでは、 **[フォルダーを開く]** 機能を使用して、IDE が、IntelliSense と参照のために Cmake プロジェクトファイル ( *cmakelists*など) を直接使用できるようにします。 Ninja と Visual Studio ジェネレーターはどちらもサポートされています。 Visual Studio ジェネレーターを使用すると、一時プロジェクトファイルが生成され、msbuild.exe に渡されます。 ただし、IntelliSense や閲覧目的でプロジェクトが読み込まれることはありません。 また、既存の CMake キャッシュをインポートすることもできます。

## <a name="installation"></a>のインストール

**Cmake 用のビジュアルC++ツール**は、ワークロードを使用したおよび**Linux 開発C++** で **C++のデスクトップ開発**の一部としてインストールされます。

![C++ デスクトップ ワークロードでの CMake コンポーネント](media/cmake-install.png)

詳細については、「[Install the C++ Linux workload in Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md)」(Visual Studio で C++ の Linux ワークロードをインストールする) を参照してください。

## <a name="ide-integration"></a>IDE 統合

**ファイル > > フォルダーを開い**て、 *cmakelists .txt*ファイルを含むフォルダーを開くと、次の処理が行われます。

- Visual Studio は、CMake スクリプトを表示および編集するためのコマンドを含む **[CMake]** メニュー項目を、メイン メニューに追加します。

- **ソリューション エクスプローラー**に、フォルダーの構造とファイルが表示されます。

- Visual Studio は CMake.exe を実行して、既定の "*構成*" (x86 デバッグ) 用の CMake キャッシュをオプションで生成します。 CMake コマンド ラインおよび CMake からの追加出力が、**出力ウィンドウ**に表示されます。

- Visual Studio は、IntelliSense、情報の参照、リファクタリングなどを有効にするためのソース ファイルのインデックス付けを、バックグラウンドで開始します。 ユーザーが作業を行っている間、Visual Studio は、エディターおよびディスク上での変更を監視し、インデックスとソースの同期を維持します。

開くフォルダーに含まれる CMake プロジェクトの数は制限されていません。 Visual Studio は、ワークスペース内のすべての "ルート" の*Cmakelists .txt*ファイルを検出して構成します。 CMake 操作 (構成、ビルド、デバッグ)、 C++ IntelliSense、および参照は、ワークスペース内のすべての cmake プロジェクトで使用できます。

![複数のルートを持つ CMake プロジェクト](media/cmake-multiple-roots.png)

ターゲットごとに論理的にまとめられたプロジェクトを参照することも可能です。 **ソリューション エクスプローラー** ツールバーのドロップダウンから、 **[ターゲット ビュー]** を選択します。

![CMake ターゲット ビュー ボタン](media/cmake-targets-view.png)

Visual Studio では、 *Cmakesettings. json*という名前のファイルを使用して、cmake .exe の環境変数またはコマンドラインオプションを格納します。 *Cmakesettings. json*では、複数の cmake ビルド構成を定義して格納することもできます。 IDE でそれらを切り替えることができます。

それ以外の場合は、CMake プロジェクトの場合と同じように、ソースファイルの指定、ライブラリの検索、コンパイラとリンカーのオプションの設定、ビルドシステム関連のその他の情報の指定など、 *Cmakelists*を使用します。

デバッグ時に引数を実行可能ファイルに渡す必要がある場合は、 **launch**という別のファイルを使用できます。 場合によっては、Visual Studio によってこれらのファイルが自動的に生成されます。 手動で編集することも、自分でファイルを作成することもできます。

> [!NOTE]
> その他の種類の開いているフォルダープロジェクトでは、 **Cppproperties. json**と**tasks. json**の2つの追加の json ファイルが使用されます。 これらはいずれも CMake プロジェクトには関連していません。

## <a name="import-an-existing-cache"></a>既存のキャッシュをインポートする

既存の*cmakecache.txt*ファイルをインポートすると、Visual Studio は、カスタマイズされた変数を自動的に抽出し、それらに基づいて事前設定さ*れた cmakesettings. json*ファイルを作成します。 元のキャッシュは、どのような方法でも変更されません。 コマンドラインから使用することも、生成に使用したツールや IDE を使用して使用することもできます。 新しい*Cmakesettings. json*ファイルは、プロジェクトのルートである*cmakesettings*と共に配置されます。 Visual Studio は、設定ファイルに基づいて新しいキャッシュを生成します。 自動キャッシュ生成は、 **CMake > 全般ダイアログ > の [ツール] > オプション**で上書きできます。

キャッシュ内のすべてのものがインポートされるわけではありません。  ジェネレーターや、コンパイラの場所などのプロパティは、IDE で問題なく機能することがわかっている既定値に置き換えられます。

### <a name="to-import-an-existing-cache"></a>既存のキャッシュをインポートするには

1. メインメニューから、[ファイル > 開く] を選択し **> CMake を開き**ます。

   ![CMake を開く](media/cmake-file-open.png "File、Open、CMake")

   このコマンドは、**キャッシュからの CMake のインポート**ウィザードを起動します。

2. インポートする*cmakecache.txt*ファイルに移動し、[ **OK]** をクリックします。 **[キャッシュから CMake のプロジェクトをインポートします]** ウィザードが表示されます。

   ![CMake キャッシュのインポート](media/cmake-import-wizard.png "CMake のキャッシュの作成ウィザードを開く")

   ウィザードが完了すると、プロジェクトのルートの*Cmakelists .txt*ファイルの横に**ソリューションエクスプローラー**に新しい*cmakecache.txt*ファイルが表示されます。

## <a name="building-cmake-projects"></a>CMake プロジェクトのビルド

CMake プロジェクトをビルドするには、次の選択肢があります。

1. 全般 ツールバーで、**構成** ドロップダウンを見つけます。 既定では、"Linux-Debug" または "x64-Debug" が表示されることがあります。 優先する構成を選択し、 **F5**キーを押すか、ツールバーの **[実行]** (緑色の三角形) ボタンをクリックします。 Visual Studio ソリューションと同じように、プロジェクトは最初に自動的にビルドされます。

1. *Cmakelists*を右クリックし、コンテキストメニューから **[ビルド]** を選択します。 フォルダー構造内に複数のターゲットがある場合は、すべてをビルドするか、特定の 1 つのターゲットだけをビルドするかを選べます。

1. メインメニューから、 **[ビルド > ビルド]** を選択します (**F7**キーまたは**Ctrl + Shift + B**キーを押します)。 **[全般]** ツール バーの **[スタートアップ アイテム]** ドロップダウンで CMake ターゲットが既に選択されていることを確認します。

![CMake ビルドメニューコマンド](media/cmake-build-menu.png "CMake ビルドコマンドメニュー")

ビルド構成、環境変数、コマンドライン引数、および*Cmakesettings. json*ファイル内のその他の設定をカスタマイズできます。 *Cmakelists .txt*ファイルを変更せずに変更を加えることができます。 詳細については、「[Customize CMake settings](customize-cmake-settings.md)」 (CMake 設定のカスタマイズ) を参照してください。

想像したとおり、ビルド結果が**出力ウィンドウ**と**エラー一覧**に表示されます。

![CMake ビルドエラー](media/cmake-build-errors.png "CMake ビルドエラー")

複数のビルドターゲットがあるフォルダーでは、ビルドする CMake ターゲットを指定できます。 **cmake**メニューまたは*cmakelists .txt*コンテキストメニューの **[ビルド]** 項目を選択して、ターゲットを指定します。 CMake プロジェクトで**Ctrl + Shift + B キーを押す**と、現在アクティブなドキュメントがビルドされます。

## <a name="debugging-cmake-projects"></a>CMake プロジェクトのデバッグ

CMake プロジェクトをデバッグするには、優先する構成を選択し、 **F5**キーを押します。 または、ツールバーの **[実行]** ボタンをクリックします。 **[実行]** ボタンに [スタートアップ アイテムの選択] と表示されている場合は、ドロップダウン矢印を選んで、実行するターゲットを選びます (CMake プロジェクトでは、[現在のドキュメント] オプションは .cpp ファイルの場合にのみ有効です)。

![CMake の [実行] ボタン](media/cmake-run-button.png "CMake の [実行] ボタン")

**[実行]** または **F5** コマンドを選ぶと、前回のビルドの後で何かが変更されている場合は、最初にプロジェクトがビルドされます。

CMake デバッグセッションをカスタマイズするには、**起動. と json**ファイルのプロパティを設定します。 詳細については、[CMake デバッグ セッションの構成](configure-cmake-debugging-sessions.md)に関するページを参照してください。

## <a name="editing-cmakeliststxt-files"></a>CMakeLists.txt ファイルの編集

*Cmakelists .txt*ファイルを編集するには、**ソリューションエクスプローラー**でファイルを右クリックし、 **[開く]** を選択します。 ファイルに変更を加えると、黄色のステータスバーが表示され、IntelliSense が更新されることが通知されます。 更新操作を取り消すことができます。 *Cmakelists*の詳細については、 [cmake のドキュメント](https://cmake.org/documentation/)を参照してください。

   ![CMakeLists .txt ファイルの編集](media/cmake-cmakelists.png "CMakeLists .txt ファイルの編集")

ファイルを保存するとすぐに構成手順が自動的に再び実行され、 **[出力]** ウィンドウに情報が表示されます。 エラーと警告は、 **[エラー一覧]** または **[出力]** ウィンドウに表示されます。 **エラー一覧**のエラーをダブルクリックして、 *cmakelists*の問題のある行に移動します。

   ![CMakeLists .txt ファイルエラー](media/cmake-cmakelists-error.png "CMakeLists .txt ファイルエラー")

## <a name="cmake-configure-step"></a>CMake の構成ステップ

*Cmakesettings. json*ファイルまたは*cmakesettings .txt*ファイルに大幅な変更が加えられると、Visual Studio は自動的に cmake 構成ステップを再実行します。 構成手順がエラーなしで終了した場合、収集された情報C++は IntelliSense および言語サービスで利用できます。 ビルドおよびデバッグ操作でも使用されます。

複数の CMake プロジェクトで、同じ CMake 構成名 (たとえば、x86-Debug) を使用することができます。 これらはすべて、構成が選択されると、(独自のビルドルートフォルダーに) 構成およびビルドされます。 その CMake 構成に参加しているすべての CMake プロジェクトから、ターゲットをデバッグすることができます。

   ![CMake ビルドのみのメニュー項目](media/cmake-build-only.png "CMake ビルドのみのメニュー項目")

ビルドとデバッグセッションは、ワークスペース内のプロジェクトのサブセットに制限できます。 *Cmakesettings. json*ファイルに一意の名前を使用して新しい構成を作成します。 その後、これらのプロジェクトにのみ構成を適用します。 この構成を選択すると、IntelliSense とビルドおよびデバッグコマンドは、指定されたプロジェクトにのみ適用されます。

## <a name="troubleshooting-cmake-cache-errors"></a>CMake キャッシュ エラーのトラブルシューティング

問題を診断するために CMake キャッシュの状態に関する詳しい情報が必要な場合は、**CMake** のメイン メニューまたは**ソリューション エクスプローラー**で *CMakeLists.txt* のコンテキスト メニューを開き、次のコマンドのいずれかを実行します。

- **[キャッシュの表示]** では、エディターのビルドルートフォルダーから*cmakecache.txt*ファイルが開きます。 (ここで*cmakecache.txt*に対して行った編集は、キャッシュを消去すると消去されます。 キャッシュをクリーニングした後も変更を保持するには、「 [CMake の設定をカスタマイズ](customize-cmake-settings.md)する」を参照してください)。

- **[キャッシュ フォルダーを開く]** は、エクスプローラー ウィンドウでビルド ルート フォルダーを開きます。

- **[キャッシュをクリーン]** は、次の CMake 構成ステップがクリーンなキャッシュから開始されるように、ビルド ルート フォルダーを削除します。

- **キャッシュの生成**を実行すると、Visual Studio によって環境が最新であると見なされる場合でも、生成ステップが強制的に実行されます。

自動キャッシュ生成は、 **CMake > 全般ダイアログ > の [ツール] > オプション**で無効にすることができます。

## <a name="single-file-compilation"></a>単一ファイルのコンパイル

CMake プロジェクトで1つのファイルをビルドするには、**ソリューションエクスプローラー**でファイルを右クリックします。 ポップアップメニューから **[コンパイル]** を選択します。 また、現在開いているファイルをエディターで作成するには、次のようにメインの**Cmake**メニューを使用します。

![CMake の単一ファイルのコンパイル](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>コマンド ラインから CMake を実行する

Visual Studio インストーラーから CMake をインストールした場合は、次の手順に従ってコマンド ラインから実行できます。

1. 適切な vsdevcmd.bat (x86 または x64) を実行します。 詳細については、「[コマンドラインでのビルド](building-on-the-command-line.md)」を参照してください。

1. 出力フォルダーに移動します。

1. CMake を実行してアプリをビルド/構成します。

::: moniker-end

::: moniker range="vs-2015"

Visual Studio 2015 では、Visual Studio のユーザーは [CMake ジェネレーター](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)を使って MSBuild プロジェクト ファイルを生成し、IDE はそのファイルを IntelliSense、参照、およびコンパイルに使っていました。

::: moniker-end

## <a name="see-also"></a>関連項目

[チュートリアル: Visual C++ Studio でクロスプラットフォームプロジェクトを作成する](get-started-linux-cmake.md)\
[Linux CMake プロジェクトを構成する](../linux/cmake-linux-project.md)\
[リモートの Linux コンピューター\ に接続](../linux/connect-to-your-remote-linux-computer.md)します。
[CMake ビルド設定をカスタマイズ](customize-cmake-settings.md)\
[Cmakesettings. json スキーマリファレンス](cmakesettings-reference.md)\
[CMake デバッグセッションの構成](configure-cmake-debugging-sessions.md)\
[Linux プロジェクトの配置、実行、デバッグ](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 定義済み構成リファレンス](cmake-predefined-configuration-reference.md)
