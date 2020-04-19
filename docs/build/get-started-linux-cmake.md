---
title: Visual Studio で C++ クロスプラットフォーム プロジェクトを作成する
description: Visual Studio で、Linux と Windows の両方をC++対象とするオープンソースの cmake プロジェクトをセットアップ、コンパイル、およびデバッグする方法について説明します。
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: 83d71d3078e892a51aef159b225fecec2b581f20
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791764"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>チュートリアル: Visual C++ Studio でクロスプラットフォームプロジェクトを作成する

Visual Studio での C と C++ の開発は、Windows だけではなくなっています。 このチュートリアルでは、Windows および Linux でC++のクロスプラットフォーム開発に Visual Studio を使用する方法について説明します。 これは CMake に基づいているため、Visual Studio プロジェクトを作成または生成する必要はありません。 CMakeLists .txt ファイルが含まれているフォルダーを開くと、Visual Studio によって IntelliSense とビルド設定が自動的に構成されます。 Windows では、コードの編集、ビルド、およびデバッグをローカルですぐに開始できます。 次に、Linux でも同じように構成を切り替えます。すべて Visual Studio 内から実行します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * GitHub からオープンソースの CMake プロジェクトを複製する
> * Visual Studio でプロジェクトを開く
> * Windows 上で実行可能ターゲットをビルドしてデバッグする
> * Linux マシンへの接続を追加する
> * Linux 上で同じターゲットをビルドしてデバッグする

## <a name="prerequisites"></a>[前提条件]

* クロスプラットフォームの C++ 開発用に Visual Studio をセットアップする
  * まず、 [Visual Studio をインストール](https://visualstudio.microsoft.com/vs/)し、**ワークロードを使用C++** してと Linux 開発を行う **C++デスクトップ開発**を選択します。 この最小インストールは 3 GB のみです。 ダウンロードの速度によっては、インストールに10分以上かかることはありません。

* クロスプラットフォームの C++ 開発用に Linux マシンをセットアップする
  * Visual Studio に Linux の特定のディストリビューションは必要ありません。 OS は、物理マシン、VM、またはクラウドで実行できます。 Windows Subsystem for Linux (WSL) を使用することもできます。 ただし、このチュートリアルでは、グラフィカルな環境が必要です。 WSL は、主にコマンドライン操作のためのものであるため、ここでは推奨されません。
  * Visual Studio には、 C++コンパイラ、gdb、ssh、rsync、zip の各ツールが必要です。 Debian ベースのシステムでは、次のコマンドを使用してこれらの依存関係をインストールできます。

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync zip
    ```

  * Visual Studio では、サーバーモードが有効になっている Linux コンピューターでの CMake の最新バージョンが必要です (少なくとも 3.8)。 Microsoft が生成した CMake のユニバーサル ビルドを、任意の Linux ディストリビューションにインストールできます。 このビルドを使用して、最新の機能があることを確認することをお勧めします。 CMake のバイナリは、GitHub の [CMake リポジトリの Microsoft フォーク](https://github.com/Microsoft/CMake/releases)から入手できます。 そのページにアクセスして、Linux マシンのシステムアーキテクチャに一致するバージョンをダウンロードし、実行可能ファイルとしてマークします。

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * スクリプトを実行するためのオプションは、`-–help` で確認できます。 `–prefix` オプションを使用して、 **/usr**パスでのインストールを指定することをお勧めします。これは、Visual Studio が cmake を検索する既定の場所で**あるためです**。 次の例では Linux-x86_64 スクリプトを示します。 別のターゲットプラットフォームを使用している場合は、必要に応じて変更します。

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Windows マシンにインストールされている Git for Windows。
* GitHub アカウント。

## <a name="clone-an-open-source-cmake-project-from-github"></a>GitHub からオープンソースの CMake プロジェクトを複製する

このチュートリアルでは、GitHub のブレット物理 SDK を使用します。 多くのアプリケーションに対して、衝突の検出と物理的なシミュレーションを提供します。 SDK には、追加のコードを記述しなくてもコンパイルして実行できる実行可能プログラムのサンプルが含まれています。 このチュートリアルでは、ソースコードもビルドスクリプトも変更しません。 開始するには、Visual Studio がインストールされているコンピューターで GitHub から*bullet3*リポジトリを複製します。

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Visual Studio のメインメニューで、ファイル を選択し **> CMake > 開き**ます。 ダウンロードした bullet3 リポジトリのルートにある CMakeLists .txt ファイルに移動します。

    ![Visual Studio の [ファイル] > [開く] > [CMake] メニュー](media/cmake-open-cmake.png)

    フォルダーを開くとすぐに、**ソリューションエクスプローラー**にフォルダー構造が表示されるようになります。

    ![Visual Studio のソリューション エクスプローラーのフォルダー ビュー](media/cmake-bullet3-solution-explorer.png)

    このビューには、論理的なビューやフィルター処理されたビューではなく、ディスク上にあるものがそのまま表示されます。 既定では、隠しファイルは表示されません。

1. **[すべてのファイルを表示]** ボタンをクリックして、フォルダー内のすべてのファイルを表示します。

    ![Visual Studio のソリューション エクスプローラーの [すべてのファイルを表示] ボタン](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>ターゲット ビューに切り替える

CMake を使用しているフォルダーを開くと、Visual Studio で CMake キャッシュが自動的に生成されます。 プロジェクトのサイズによっては、この操作にしばらくかかる場合があります。

1. **[出力ウィンドウ]** で **[Show output from]\(出力元\)** を選択してから、 **[CMake]** を選択して、キャッシュ生成処理の状態を監視します。 操作が完了すると、"ターゲット情報の抽出が完了しました" というメッセージが表示されます。

   ![CMake からの出力が表示された Visual Studio の出力ウィンドウ](media/cmake-bullet3-output-window.png)

   この操作が完了すると、IntelliSense が構成されます。 プロジェクトをビルドし、アプリケーションをデバッグできます。 Visual Studio では、CMakeLists ファイルで指定されたターゲットに基づいて、ソリューションの論理ビューが表示されるようになりました。

1. **ソリューション エクスプローラー**の **[ソリューションおよびフォルダー]** ボタンを使用して、CMake のターゲット ビューに切り替えます。

   ![CMake のターゲット ビューを表示するためのソリューション エクスプローラーの [ソリューションおよびフォルダー] ボタン](media/cmake-bullet3-show-targets.png)

   Bullet SDK でのビューの表示は次のようになります。

   ![ソリューション エクスプローラーの CMake ターゲット ビュー](media/cmake-bullet3-targets-view.png)

   ターゲット ビューでは、このソース ベースの内容に関するさらに直感的なビューが提供されます。 一部のターゲットはライブラリで、他は実行可能ファイルであることがわかります。

1. CMake ターゲット ビューでノードを展開すると、そのソース コード ファイルが表示されます。それらのファイルがディスク上のどこにあってもかまいません。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>明示的な Windows x64-Debug 構成を追加する

Visual Studio によって、Windows の既定の**X64 デバッグ**構成が作成されます。 構成により、Visual Studio は CMake に使用するプラットフォーム ターゲットを認識します。 既定の構成は、ディスク上では表されません。 構成を明示的に追加すると、Visual Studio によって*Cmakesettings. json*というファイルが作成されます。 指定したすべての構成の設定が表示されます。

1. 新しい構成を追加します。 ツールバーの **[構成]** ドロップダウンを開き、 **[構成の管理]** を選択します。

   ![[構成の管理] ドロップダウン](media/cmake-bullet3-manage-configurations.png)

   [Cmake 設定エディター](customize-cmake-settings.md)が開きます。 エディターの左側にある緑色のプラス記号を選択して、新しい構成を追加します。 **[CMakeSettings への構成の追加]** ダイアログボックスが表示されます。

   ![[構成を CMakeSettings に追加する] ダイアログ](media/cmake-bullet3-add-configuration-x64-debug.png)

   このダイアログボックスには、Visual Studio に含まれているすべての構成に加えて、作成したカスタム構成が表示されます。 **X64 デバッグ**構成を引き続き使用する場合は、最初に追加したものを選択する必要があります。 **[X64-デバッグ]** を選択し、 **[選択]** をクリックします。 Visual Studio は、 **x64-Debug**用の構成を使用して CMakeSettings. json ファイルを作成し、ディスクに保存します。 CMakeSettings.json で名前パラメーター直接変更することで、構成に好きな名前を使用できます。

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Windows でのブレークポイントの設定、ビルド、および実行

このステップでは、Bullet Physics ライブラリのデモを行うサンプル プログラムをデバッグします。
  
1. **ソリューション エクスプローラー**で AppBasicExampleGui を選択して展開します。

1. `BasicExample.cpp` ファイルを開きます。

1. 実行中のアプリケーションをクリックしたときにヒットするブレークポイントを設定します。 クリック イベントは、ヘルパー クラスのメソッドで処理されます。 すばやく移動するには:

   1. 構造 `BasicExample` の派生元の `CommonRigidBodyBase` を選択します。 これは30行目にあります。

   1. 右クリックし、 **[定義へ移動]** を選択します。 これで、CommonRigidBodyBase ヘッダーが作成されました。

   1. ソースの上にあるブラウザービューで、`CommonRigidBodyBase`にあることがわかります。 右側で、調べるメンバーを選択できます。 ドロップダウンを開き、[`mouseButtonCallback`] を選択して、ヘッダー内のその関数の定義に移動します。

      ![Visual Studio のメンバーの一覧ツール バー](media/cmake-bullet3-member-list-toolbar.png)

1. この関数の最初の行にブレークポイントを設定します。 Visual Studio デバッガーで実行されている場合、アプリケーションのウィンドウ内でマウスボタンをクリックするとヒットします。

1. アプリケーションを起動するには、ツールバーの [起動] ドロップダウンを選択します。 これは、"スタートアップ項目の選択" という緑色の再生アイコンが付いたものです。 ドロップダウンで、[Appbasic] を選択します。 実行可能ファイルの名前が起動ボタンに表示されます。

   ![Visual Studio ツール バーの [スタートアップ アイテムの選択] の起動ドロップダウン](media/cmake-bullet3-launch-button.png)

1. [起動] をクリックして、アプリケーションと必要な依存関係をビルドし、Visual Studio デバッガーがアタッチされた状態で起動します。 しばらくすると、実行中のアプリケーションが表示されます。

   ![Windows アプリケーションをデバッグしている Visual Studio](media/cmake-bullet3-launched.png)

1. アプリケーション ウィンドウ内にマウスを移動し、ボタンをクリックしてブレークポイントをトリガーします。 ブレークポイントによって Visual Studio がフォアグラウンドに戻り、エディターは実行が一時停止されている行を表示します。 アプリケーション変数、オブジェクト、スレッド、メモリを検査したり、コードを対話形式でステップ実行したりできます。 **[続行]** を選択してアプリケーションを再開し、正常に終了します。 または、[停止] ボタンを使用して、Visual Studio 内での実行を停止します。

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Linux の構成を追加してリモート コンピューターに接続する

1. Linux 構成を追加します。 **ソリューション エクスプローラー** ビューで CMakeSettings.json ファイルを右クリックし、 **[構成の追加]** を選択します。 前と同じ [構成を CMakeSettings に追加する] ダイアログが表示されます。 **[Linux-デバッグ]** を選択し、次に CMakeSettings. json ファイルを保存します (ctrl + s)。

1. 構成 ドロップダウンで  **Linux-デバッグ** を選択します。

   ![X64-Debug オプションと Linux-Debug オプションが含まれる起動構成ドロップダウン](media/cmake-bullet3-linux-configuration-item.png)

   Linux システムに初めて接続する場合は、 **[リモートシステムへの接続]** ダイアログボックスが表示されます。

   ![Visual Studio の [リモート システムへの接続] ダイアログ](media/cmake-bullet3-connection-manager.png)

   リモート接続を既に追加している場合は、[ツール] > [**オプション] > [クロスプラットフォーム > 接続マネージャー**] の順に移動して、このウィンドウを開くことができます。

1. [Linux マシンに接続情報](/cpp/linux/connect-to-your-remote-linux-computer)を入力し、 **[接続]** を選択します。 Visual Studio は、 **Linux-Debug**の既定の接続として、そのマシンを CMakeSettings. json に追加します。 また、リモートコンピューターからヘッダーを取得するので、[そのリモート接続に固有の IntelliSense](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense)を利用できます。 次に、Visual Studio によってファイルがリモートコンピューターに送信され、リモートシステムに CMake キャッシュが生成されます。 これらの手順は、ネットワークの速度とリモートコンピューターの機能によっては、時間がかかることがあります。 CMake 出力ウィンドウに "ターゲット情報の抽出が完了しました" というメッセージが表示されたら、それが完了していることがわかります。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Linux でブレークポイントを設定し、ビルドし、実行する

これはデスクトップアプリケーションであるため、デバッグ構成にいくつかの追加の構成情報を提供する必要があります。

1. CMake ターゲット ビューで、Appbasic Gui を右クリックし、**デバッグ設定と起動設定** を選択して、非表示の**vs**サブフォルダーにある Launch ファイルを開きます。 このファイルは、開発環境に対してローカルに存在します。 チームでファイルをチェックインおよび保存したい場合は、プロジェクトのルートにそれを移動できます。 このファイルには、Appbasicon Gui 用の構成が追加されています。 これらの既定の設定はほとんどの場合に機能しますが、ここでは機能しません。 これはデスクトップアプリケーションであるため、プログラムを起動するための追加情報を提供して、Linux コンピューターで確認できるようにする必要があります。

1. Linux コンピューターで `DISPLAY` 環境変数の値を確認するには、次のコマンドを実行します。

   ```cmd
   echo $DISPLAY
   ```

   Appbasicon Gui の構成には、パラメーター配列 "pipeArgs" があります。 "$ {デバッガコマンド}" という行が含まれています。 これは、リモートコンピューターで gdb を起動するコマンドです。 このコマンドを実行する前に、Visual Studio は表示をこのコンテキストにエクスポートする必要があります。 たとえば、表示の値が `:1`場合は、次のようにその行を変更します。

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. アプリケーションを起動してデバッグします。 ツールバーの **[スタートアップ項目の選択**] ドロップダウンを開き、[ **Appbasic] gui**を選択します。 次に、ツールバーの緑色の再生アイコンを選択するか、 **F5**キーを押します。 アプリケーションとその依存関係は、リモートの Linux コンピューター上に構築され、Visual Studio デバッガーがアタッチされた状態で起動されます。 リモート Linux マシンに、アプリケーションのウィンドウが表示されます。

1. アプリケーションウィンドウにマウスポインターを移動し、ボタンをクリックします。 ブレークポイントにヒットします。 プログラムの実行が一時停止し、Visual Studio がフォアグラウンドに戻り、ブレークポイントが表示されます。 Visual Studio には Linux コンソール ウィンドウも表示されます。 このウィンドウには、リモートの Linux コンピューターからの出力が表示され、`stdin`の入力を受け取ることもできます。 任意の Visual Studio ウィンドウと同様に、好きな場所にドッキングして表示できます。 その位置は、今後のセッションで保持されます。

   ![Visual Studio の Linux コンソール ウィンドウ](media/cmake-bullet3-linux-console.png)

1. Visual Studio を使用して、アプリケーションの変数、オブジェクト、スレッド、メモリを調べたり、対話式にコードをステップ実行したりできます。 しかし今回は、ローカルの Windows 環境ではなく、リモートの Linux マシン上ですべてを実行しています。 **続行** を選択すると、アプリケーションを正常に再開して終了できます。または、ローカル実行の場合と同じように 停止 ボタンを選択することもできます。

1. Visual Studio では Linux 上のアプリケーションが起動されているため、[呼び出し履歴] ウィンドウを見ると、`x11OpenGLWindow` の呼び出しが表示されています。

   ![Linux の呼び出し履歴が表示されている [呼び出し履歴] ウィンドウ](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>学習内容

このチュートリアルでは、GitHub から直接コードベースを複製します。 変更せずに、Windows 上でビルド、実行、およびデバッグしました。 次に、構成を少し変更した同じコードベースを使用して、リモートの Linux マシンでビルド、実行、およびデバッグを行います。

## <a name="next-steps"></a>次のステップ:

Visual Studio での CMake プロジェクトの構成とデバッグについてさらに学習します。

> [!div class="nextstepaction"]
> [Visual Studio の CMake プロジェクト](cmake-projects-in-visual-studio.md)<br/><br/>
> [Linux CMake プロジェクトを構成する](../linux/cmake-linux-project.md)<br/><br/>
> [リモートの Linux コンピューターに接続する](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [CMake のビルド設定をカスタマイズする](customize-cmake-settings.md)<br/><br/>
> [CMake デバッグ セッションを構成する](configure-cmake-debugging-sessions.md)<br/><br/>
> [Linux プロジェクトの配置、実行、デバッグ](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 定義済み構成リファレンス](cmake-predefined-configuration-reference.md)
>
