---
title: 'チュートリアル: プログラムの配置 (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 7170fe3ae058f832e452089021d9f863f1791f14
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657514"
---
# <a name="walkthrough-deploying-your-program-c"></a>チュートリアル: プログラムの配置 (C++)

ここまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了することで、アプリケーションの作成が完了しました。最後の手順は、他のユーザーが自分のコンピューターにプログラムをインストールできるようにインストーラーを作成することです。 インストーラーを作成するには、新しいプロジェクトを既存のソリューションに追加します。 この新しいプロジェクトの出力は、別のコンピューターにアプリをインストールする setup.exe ファイルです。

このチュートリアルでは、Windows インストーラーを使用してアプリケーションを配置する方法を示します。 アプリケーションの配置には ClickOnce を使用することもできます。 詳細については、「 [Visual C++ アプリケーションの ClickOnce 配置](../ide/clickonce-deployment-for-visual-cpp-applications.md)」を参照してください。 一般的な配置の詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](/visualstudio/deployment/deploying-applications-services-and-components)」をご覧ください。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルは、C++ 言語の基本を理解していることを前提としています。

- また、これまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了していることも必要です。

- このチュートリアルは Visual Studio の Express Edition では完了できません。

- Microsoft Visual Studio Installer Projects の拡張機能をまだダウンロードしていない場合は、後で説明するさらなる手順に従って、これをダウンロードします。 この拡張機能は、Visual Studio 開発者向けの無料版であり、Visual Studio にセットアップおよび配置プロジェクト テンプレートの機能を追加するものです。

### <a name="to-install-the-visual-studio-setup-and-deployment-project-template"></a>Visual Studio のセットアップおよび配置プロジェクト テンプレートをインストールするには

1. インターネットに接続しているときに、Visual Studio で、**[ツール]** > **[拡張機能と更新プログラム]** を選択します。

1. **[拡張機能と更新プログラム]** で **[オンライン]** タブを選択し、検索ボックスに「*Microsoft Visual Studio Installer Projects*」と入力します。 **Enter** キーを押し、**[Microsoft Visual Studio \<バージョン> Installer Projects]** を選択して、**[ダウンロード]** をクリックします。

1. 拡張機能をインストールするよう選択し、Visual Studio を再起動します。

1. メニュー バーで **[ファイル]** > **[最近使ったプロジェクトとソリューション]** の順に選択し、**Game** ソリューションを選択して再び開きます。

### <a name="to-create-a-setup-project-and-install-your-program"></a>セットアップ プロジェクトを作成してプログラムをインストールするには

1. アクティブなソリューション構成を [解放] に変更します。 メニュー バーで **[ビルド]** > **[構成マネージャー]** の順に選択します。 **[構成マネージャー]** ダイアログ ボックスで、**[アクティブ ソリューション構成]** ドロップダウン リストの **[解放]** をクリックします。 **[閉じる]** をクリックして構成を保存します。

1. メニュー バーで **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し、**[新しいプロジェクト]** ダイアログ ボックスを開きます。

1. ダイアログ ボックスの左ウィンドウで、**[インストール済み]** > **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio インストーラー]** を選択します。 中央のウィンドウで、**[Setup Project]\(セットアップ プロジェクト\)** を選択します。

1. **[名前]** ボックスにセットアップ プロジェクトの名前を入力します。 この例では「*Game Installer*」と入力します。 **[ソリューション]** ドロップダウン リストで **[ソリューションに追加]** をクリックします。 **[OK]** をクリックすると、セットアップ プロジェクトが作成されます。 **[File Assistant (Game Installer)]/(ファイル アシスタント (Game Installer)/)** タブがエディター ウィンドウで開きます。

1. **[アプリケーション フォルダー]** ノードを右クリックし、**[追加]** > **[プロジェクト出力]** を選択して、**[プロジェクト出力グループの追加]** ダイアログ ボックスを開きます。

1. ダイアログ ボックスで **[プライマリ出力]** を選択し、**[OK]** をクリックします。 **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** という名前の項目が表示されます。

1. **[Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力\)** 項目を選択し、**[Create Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカットを作成\)** を右クリックします。 **[Shortcut to Primary Output from Game (Active)]\(Game (アクティブ) のプライマリ出力へのショートカット\)** という名前の新しい項目が表示されます。

1. ショートカット項目の名前を *Game* に変更し、ウィンドウの左側にある **[ユーザーのプログラム メニュー]** ノードに項目をドラッグ アンド ドロップします。

1. **ソリューション エクスプローラー**で **[Game Installer]** プロジェクトを選択し、**[ビュー]** > **[プロパティ ウィンドウ]** を選択するか、または **F4** キーを押して **[プロパティ]** ウィンドウを開きます。

1. インストーラーに表示する追加の詳細を指定します。  たとえば、**[製造元]** に *Contoso*、**[製品名]** に *Game Installer*、**[SupportUrl]** に *http\://www.contoso.com* を使用します。

1. メニュー バーで **[ビルド]** > **[構成マネージャー]** の順に選択します。 **[プロジェクト]** テーブルの **[ビルド]** 列で、**[Game Installer]** のボックスをオンにします。 **[閉じる]** をクリックします。

1. メニュー バーで **[ビルド]** > **[ソリューションのビルド]** の順に選択して、Game プロジェクトと Game Installer プロジェクトをビルドします。

1. ソリューション フォルダーで、Game Installer プロジェクトからビルドされた setup.exe プログラムを見つけて実行し、Game アプリケーションをコンピューターにインストールします。 このファイル (および GameInstaller.msi) をコピーして、アプリケーションとその必要なライブラリ ファイルを別のコンピューターにインストールできます。

## <a name="next-steps"></a>次の手順

**前へ:**[チュートリアル:プロジェクトのデバッグ (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>参照

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C/C++ プログラムのビルド](../build/building-c-cpp-programs.md)<br/>
[デスクトップ アプリケーションの配置](../ide/deploying-native-desktop-applications-visual-cpp.md)<br/>
