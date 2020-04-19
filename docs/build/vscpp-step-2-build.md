---
title: C++ コンソール アプリ プロジェクトのビルドと実行
description: Visual C での Hello World コンソール アプリをビルドおよび実行します。
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: 59813a553a9034503d8bf432400db31e6e3d9478
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314272"
---
# <a name="build-and-run-a-c-console-app-project"></a>C++ コンソール アプリ プロジェクトのビルドと実行

C++ コンソール アプリケーション プロジェクトを作成しコードを入力すれば、Visual Studio 内でビルドおよび実行できます。そして、コマンドラインからスタンドアロンのアプリとしても実行できます。

## <a name="prerequisites"></a>前提条件

- コンピューターに C++ によるデスクトップ開発のワークロードを備えた Visual Studio をインストールして実行します。 まだインストールされていない場合は、「[Visual Studio での C++ のインストール サポート](vscpp-step-0-installation.md)」の手順に従います。

- 「Hello, World!」プロジェクトを作成し、 そのソース コードを入力します。 まだ行っていない場合は、「[C++ コンソール アプリケーション プロジェクトを作成](vscpp-step-1-create.md)」の手順に従います。

もし Visual Studio が次のような外観なら、アプリをビルドして実行する準備はできています。

   ![新しいプロジェクトをビルドする準備ができて](media/vscpp-ready-to-build.png "新しいプロジェクトを構築する準備")

## <a name="build-and-run-your-code-in-visual-studio"></a>Visual Studio でのビルドおよびコードの実行

1. プロジェクトをビルドするには、**ビルド** メニューから **ソリューションのビルド** を選択します。 **出力** ウィンドウは、ビルド プロセスの結果を示しています。

   ![プロジェクトのビルド](media/vscpp-build-solution.gif "プロジェクトのビルド")

1. コードを実行するには、メニュー バー上にある **デバッグ** を選び、それから **デバッグなしで開始** を選んでください。

   ![プロジェクトの開始](media/vscpp-start-without-debugging.gif "プロジェクトの開始")

   コンソール ウィンドウが開かれ、アプリが実行されます。 Visual Studio 内でコンソール アプリを開始すると、コードが実行され、「続行するには、任意のキーを押してください...」 . " と表示されますので、出力の表示を確認できます。

おめでとうございます! 初めての「Hello, world!」 コンソール アプリが Visual Studio で作成されました。 任意のキーを押せば、コンソール ウィンドウが閉じられ、Visual Studio に戻ります。

[問題が発生した場合](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>コマンド ウィンドウで、コードを実行します。

通常、コンソール アプリは Visual Studio ではなく、コマンド プロンプトで実行します。 一度 Visual Studio でアプリがビルドされたら、任意のコマンド ウィンドウから実行できます。 コマンド プロンプト ウィンドウで新しいアプリを検索し実行する方法を次に示します。

1. **[ソリューション エクスプ ローラー]** で、HelloWorld ソリューションを選択し、右クリックしてコンテキスト メニューを開きます。 **[エクスプローラーでフォルダーを開く]** を選択し、HelloWorld ソリューション フォルダーで **[エクスプローラー]** ウィンドウを開きます。

1. **[ファイル エクスプ ローラー]** ウィンドウで [デバッグ] フォルダーを開きます。 これには、アプリ、HelloWorld.exe、および他のいくつかのデバッグ ファイルが含まれています。 HelloWorld.exe を選択し、Shift キーを押しながら右クリックしてコンテキスト メニューを開きます。 **[パスとしてコピー]** を選択し、アプリへのパスをクリップボードにコピーします。

1. コマンド プロンプト ウィンドウを開くには、Windows-R キーを押して、**実行**ダイアログ。 入力*cmd.exe*で、**オープン** ボックスに、選択し、 **ok**コマンド プロンプト ウィンドウを実行します。

1. コマンド プロンプト ウィンドウで右クリックし、コマンド プロンプトに、アプリへのパスを貼り付けます。 アプリを実行するには、enter キーを押します。

   ![コマンド プロンプトで、アプリを実行](media/vscpp-run-in-cmd.gif "コマンド プロンプトで、アプリの実行")

これで、ビルドし、Visual Studio でコンソール アプリを実行しました。

[問題が発生した場合](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>次の手順

この簡単なアプリを構築し実行したら、より複雑なプロジェクトに備えられます。 Visual Studio 内の Visual C++ の機能に関する詳細なチュートリアルについては、「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照してください。

## <a name="troubleshooting-guide"></a>トラブルシューティング ガイド

最初の C++ プロジェクトの作成での一般的な問題の発生時のソリューションは、ここを参照してください。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>ビルドし、Visual Studio の問題でコードを実行

ソース コード エディターで赤い波線が下に表示される場合、ビルドにエラーまたは警告があります。 コードが、スペル、句読点、および大文字小文字の例と一致することを確認してください。

[戻る](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>コマンド ウィンドウで、コードを実行の問題

アプリを実行するコマンドラインでソリューションのデバッグ フォルダーに移動することもできます。 アプリへのパスを指定せず、その他のディレクトリからアプリを実行することはできません。 ただし、アプリを別のディレクトリにコピーでき、そこから実行できます。

表示されない場合**パスとしてコピー**ショートカット メニューで、メニューを閉じるし、Shift キーを押しながら、もう一度開きます。 これは、利便性。 ファイル エクスプ ローラーの検索バーから、フォルダーにパスをコピーしてに貼り付けることができます、**実行**ダイアログ ボックスで、最後に、実行可能ファイルの名前を入力します。 ほんの少し詳細入力ですが、同じ結果があります。

[戻る](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
