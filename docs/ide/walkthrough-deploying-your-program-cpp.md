---
title: 'チュートリアル: プログラムの配置 (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 5cc4ead7aaef2ffa56870a374b0b73d16eb31521
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400966"
---
# <a name="walkthrough-deploying-your-program-c"></a>チュートリアル: プログラムの配置 (C++)

ここまでの関連チュートリアルを完了することで、アプリケーションの作成が完了しました。最後の手順は、他のユーザーが自分のコンピューターにプログラムをインストールできるようにインストーラーを作成することです。 インストーラーを作成するには、新しいプロジェクトを既存のソリューションに追加します。 この新しいプロジェクトの出力は、別のコンピューターにアプリをインストールする setup.exe ファイルです。

このチュートリアルでは、Windows インストーラーを使用してアプリケーションを配置する方法を示します。 アプリケーションの配置には ClickOnce を使用することもできます。 詳細については、「 [Visual C++ アプリケーションの ClickOnce 配置](../windows/clickonce-deployment-for-visual-cpp-applications.md)」を参照してください。 一般的な配置の詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](/visualstudio/deployment/deploying-applications-services-and-components)」をご覧ください。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルは、C++ 言語の基本を理解していることを前提としています。

- また、これまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了していることも必要です。

- このチュートリアルは Visual Studio の Express Edition では完了できません。

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Visual Studio のセットアップおよび配置プロジェクト テンプレートをインストールする

このセクション内の手順は、インストールした Visual Studio のバージョンによって異なります。 このページの左上にあるバージョン セレクターが適切に設定されていることを確認してください。

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Visual Studio 2019 のセットアップおよび配置プロジェクト テンプレートをインストールする

1. Microsoft Visual Studio Installer Projects の拡張機能をまだダウンロードしていない場合は、これをダウンロードします。 この拡張機能は、Visual Studio 開発者向けの無料版であり、Visual Studio にセットアップおよび配置プロジェクト テンプレートの機能を追加するものです。 インターネットに接続しているときに、Visual Studio で、 **[拡張機能]**  >  **[拡張機能の管理]** の順に選択します。 **[拡張機能と更新プログラム]** ダイアログ ボックスで **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 **Enter** キーを押し、 **[Microsoft Visual Studio \<バージョン> Installer Projects]** を選択して、 **[ダウンロード]** をクリックします。 拡張機能を実行してインストールするよう選択し、Visual Studio を再起動します。

1. Visual Studio のメニュー バーで **[ファイル]** > **[最近使ったプロジェクトとソリューション]** の順に選択し、プロジェクトを選択して再び開きます。

1. メニューバーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** の順に選択して、 **[新しいプロジェクトの作成]** ダイアログ ボックスを開きます。 検索ボックスに「セットアップ」と入力し、結果の一覧から **[セットアップ プロジェクト]** を選択します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (ProjectName)]/(ファイル アシスタント (<プロジェクト名>)/)** タブがエディター ウィンドウで開きます。

1. **[アプリケーション フォルダー]** ノードを右クリックし、 **[追加]** > **[プロジェクト出力]** を選択して、 **[プロジェクト出力グループの追加]** ダイアログ ボックスを開きます。

1. ダイアログ ボックスで **[プライマリ出力]** を選択し、 **[OK]** をクリックします。 **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** という名前の項目が表示されます。

1. **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** 項目を選択し、 **[Create Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカットを作成\)** を右クリックします。 **[Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカット\)** という名前の新しい項目が表示されます。

1. ショートカット項目の名前を *Game* に変更し、ウィンドウの左側にある **[ユーザーのプログラム メニュー]** ノードに項目をドラッグ アンド ドロップします。

1. **ソリューション エクスプローラー**で、 **[Game Installer]** プロジェクトを選択し、 **[ビュー]** > **[プロパティ ウィンドウ]** を選択するか、**F4** キーを押して **[プロパティ]** ウィンドウを開きます。

1. インストーラーに表示する追加の詳細を指定します。  たとえば、 **[製造元]** に *Contoso*、 **[製品名]** に *Game Installer*、 **[SupportUrl]** に *http\://www.contoso.com* を使用します。

1. メニュー バーで **[ビルド]**  >  **[構成マネージャー]** の順に選択します。 **[プロジェクト]** テーブルの **[ビルド]** 列で、 **[Game Installer]** のボックスをオンにします。 **[閉じる]** をクリックします。

1. メニューバーで、 **[ビルド]** > **[ソリューションのビルド]** の順に選択して、Game プロジェクトと Game Installer プロジェクトをビルドします。

1. ソリューション フォルダーで、Game Installer プロジェクトからビルドされた setup.exe プログラムを見つけて実行し、Game アプリケーションをコンピューターにインストールします。 このファイル (および GameInstaller.msi) をコピーして、アプリケーションとその必要なライブラリ ファイルを別のコンピューターにインストールできます。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Visual Studio 2017 以前用のセットアップおよび配置プロジェクト テンプレートをインストールする

1. インターネットに接続しているときに、Visual Studio で、 **[ツール]** > **[拡張機能と更新プログラム]** を選択します。

1. **[拡張機能と更新プログラム]** で **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 **Enter** キーを押し、 **[Microsoft Visual Studio \<バージョン> Installer Projects]** を選択して、 **[ダウンロード]** をクリックします。

1. 拡張機能をインストールするよう選択し、Visual Studio を再起動します。

1. メニュー バーで、 **[ファイル]** > **[最近使ったプロジェクトとソリューション]** の順に選択し、 **[Game]** ソリューションを選択して再び開きます。

### <a name="to-create-a-setup-project-and-install-your-program"></a>セットアップ プロジェクトを作成してプログラムをインストールするには

1. アクティブなソリューション構成を [解放] に変更します。 メニュー バーで **[ビルド]**  >  **[構成マネージャー]** の順に選択します。 **[構成マネージャー]** ダイアログ ボックスで、 **[アクティブ ソリューション構成]** ドロップダウン リストの **[解放]** をクリックします。 **[閉じる]** をクリックして構成を保存します。

1. メニューバーで、 **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択して、 **[新しいプロジェクト]** ダイアログ ボックスを開きます。

1. ダイアログ ボックスの左ウィンドウで、 **[インストール済み]**  >  **[その他のプロジェクトの種類]** ノードを展開し、 **[Visual Studio インストーラー]** を選択します。 中央のウィンドウで、 **[Setup Project]\(セットアップ プロジェクト\)** を選択します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 この例では「*Game Installer*」と入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (Game Installer)]/(ファイル アシスタント (Game Installer)/)** タブがエディター ウィンドウで開きます。

1. **[アプリケーション フォルダー]** ノードを右クリックし、 **[追加]** > **[プロジェクト出力]** を選択して、 **[プロジェクト出力グループの追加]** ダイアログ ボックスを開きます。

1. ダイアログ ボックスで **[プライマリ出力]** を選択し、 **[OK]** をクリックします。 **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** という名前の項目が表示されます。

1. **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** 項目を選択し、 **[Create Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカットを作成\)** を右クリックします。 **[Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカット\)** という名前の新しい項目が表示されます。

1. ショートカット項目の名前を *Game* に変更し、ウィンドウの左側にある **[ユーザーのプログラム メニュー]** ノードに項目をドラッグ アンド ドロップします。

1. **ソリューション エクスプローラー**で、 **[Game Installer]** プロジェクトを選択し、 **[ビュー]** > **[プロパティ ウィンドウ]** を選択するか、**F4** キーを押して **[プロパティ]** ウィンドウを開きます。

1. インストーラーに表示する追加の詳細を指定します。  たとえば、 **[製造元]** に *Contoso*、 **[製品名]** に *Game Installer*、 **[SupportUrl]** に *http\://www.contoso.com* を使用します。

1. メニュー バーで **[ビルド]**  >  **[構成マネージャー]** の順に選択します。 **[プロジェクト]** テーブルの **[ビルド]** 列で、 **[Game Installer]** のボックスをオンにします。 **[閉じる]** をクリックします。

1. メニューバーで、 **[ビルド]** > **[ソリューションのビルド]** の順に選択して、Game プロジェクトと Game Installer プロジェクトをビルドします。

1. ソリューション フォルダーで、Game Installer プロジェクトからビルドされた setup.exe プログラムを見つけて実行し、Game アプリケーションをコンピューターにインストールします。 このファイル (および GameInstaller.msi) をコピーして、アプリケーションとその必要なライブラリ ファイルを別のコンピューターにインストールできます。

::: moniker-end

## <a name="next-steps"></a>次の手順

**前へ:** [チュートリアル:プロジェクトのデバッグ (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
[デスクトップ アプリケーションの配置](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
