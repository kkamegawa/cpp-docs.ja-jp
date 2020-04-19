---
title: 'チュートリアル: コマンドラインでの C プログラムのコンパイル'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d91ee36d26e307577aa56560eb95bef5ed03305b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051527"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>チュートリアル: コマンドラインでの C プログラムのコンパイル

Visual C++には、基本的なコンソールプログラムから、完全な Windows デスクトップアプリケーションやモバイルアプリなどに至るまで、あらゆるものを作成するために使用できる C コンパイラが含まれています。

このチュートリアルでは、テキストエディターを使用して基本的な "Hello, World" スタイルの C プログラムを作成し、コマンドラインでコンパイルする方法について説明します。 コマンドラインを使用してC++作業する場合は、「[チュートリアル: コマンドラインでC++のネイティブプログラムのコンパイル](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)」を参照してください。 コマンドラインを使用せずに visual studio ide を試す場合は、「[チュートリアル: プロジェクトとソリューションの使用 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 」または「[デスクトップ開発用のC++ visual studio ide の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照してください。


## <a name="prerequisites"></a>必要条件

このチュートリアルを完了するには、Visual Studio とオプションのビジュアルC++コンポーネント、または visual Studio のビルドツールをインストールしておく必要があります。

Visual Studio は、豊富な機能を備えたエディター、リソースマネージャー、デバッガー、およびさまざまな言語とプラットフォームに対応したコンパイラをサポートする強力な統合開発環境です。 無料の Visual Studio Community エディションを含め、これらの機能と Visual Studio をダウンロードしてインストールする方法については、「 [Visual studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

Build Tools for Visual studio バージョンの Visual Studio では、C およびC++プログラムをビルドするために必要なコマンドラインツールセット、コンパイラ、ツール、およびライブラリのみがインストールされます。 これは、ビルドラボやクラスルームの演習や、比較的迅速なインストールに最適です。 コマンドラインツールセットのみをインストールするには、 [Visual studio のダウンロード](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)ページから Build Tools For visual studio をダウンロードし、インストーラーを実行します。 Visual Studio インストーラーで、 **[ C++ビルドツール]** ワークロードを選択し、 **[インストール]** を選択します。

C またはC++プログラムをコマンドラインでビルドする前に、ツールがインストールされていること、およびコマンドラインからアクセスできることを確認する必要があります。 ビジュアルC++には、コマンドライン環境が使用するツール、ヘッダー、およびライブラリを見つけるための複雑な要件があります。 準備を行わず**に、単純なコマンドプロンプトウィンドウでビジュアルC++を使用することはできません**。 *開発者コマンドプロンプト*ウィンドウが必要です。これは、必要なすべての環境変数が設定された通常のコマンドプロンプトウィンドウです。 さいわい、Visual C++は、コマンドラインビルド用に環境が設定されている開発者コマンドプロンプトを起動するためのショートカットをインストールします。 残念ながら、開発者コマンドプロンプトのショートカットの名前と配置場所は、ほぼすべてのバージョンのビジュアルC++と、異なるバージョンの Windows で異なります。 最初のチュートリアルタスクでは、使用する適切なショートカットを見つけます。

> [!NOTE]
> 開発者コマンドプロンプトのショートカットを使用すると、コンパイラおよびツールの正しいパス、および必要なヘッダーとライブラリが自動的に設定されます。 これらの値の一部は、ビルド構成ごとに異なります。 ショートカットのいずれかを使用しない場合は、これらの環境値を自分で設定する必要があります。 詳細については、[コマンド ライン ビルドのパスと環境変数の設定](setting-the-path-and-environment-variables-for-command-line-builds.md)に関するページを参照してください。 ビルド環境は複雑であるため、独自に構築するのではなく、開発者コマンドプロンプトのショートカットを使用することを強くお勧めします。

これらの手順は、使用している Visual Studio のバージョンによって異なります。 続行する前に、このページの左上にあるバージョンセレクターが正しく設定されていることを確認してください。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Visual Studio 2019 で開発者コマンドプロンプトを開く

Windows 10 に Visual Studio 2019 がインストールされている場合は、[スタート] メニューを開き、下にスクロールして、visual studio **2019**フォルダー (visual studio 2019 アプリではありません) を開きます。 **VS 2019 の開発者コマンドプロンプト**を選択して、コマンドプロンプトウィンドウを開きます。

別のバージョンの Windows を使用している場合は、[スタート] メニューまたは [スタート] ページで、開発者コマンドプロンプトのショートカットが含まれている Visual Studio tools フォルダーを探します。 また、Windows search 関数を使用して "developer command prompt" を検索し、インストールされている Visual Studio のバージョンに一致するものを選択することもできます。 ショートカットを使用して、コマンドプロンプトウィンドウを開きます。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Visual Studio 2017 で開発者コマンドプロンプトを開く

Windows 10 に Visual Studio 2017 がインストールされている場合は、[スタート] メニューを開き、下にスクロールして、visual studio **2017**フォルダー (visual studio 2017 アプリではありません) を開きます。 **VS 2017 の開発者コマンドプロンプト**を選択して、コマンドプロンプトウィンドウを開きます。

別のバージョンの Windows を実行している場合は、[スタート] メニューまたは [スタート] ページで、開発者コマンドプロンプトのショートカットが含まれている Visual Studio tools フォルダーを探します。 また、Windows search 関数を使用して "developer command prompt" を検索し、インストールされている Visual Studio のバージョンに一致するものを選択することもできます。 ショートカットを使用して、コマンドプロンプトウィンドウを開きます。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Visual Studio 2015 で開発者コマンドプロンプトを開く

Windows 10 に Microsoft Visual C++ Build tools 2015 がインストールされている場合は、 **[スタート]** メニューを開き、下にスクロールして、 **[Visual C++ build tools]** フォルダーを開きます。 **[Visual C++ 2015 x86 Native Tools コマンドプロンプト]** を選択して、コマンドプロンプトウィンドウを開きます。

別のバージョンの Windows を実行している場合は、[スタート] メニューまたは [スタート] ページで、開発者コマンドプロンプトのショートカットが含まれている Visual Studio tools フォルダーを探します。 また、Windows search 関数を使用して "developer command prompt" を検索し、インストールされている Visual Studio のバージョンに一致するものを選択することもできます。 ショートカットを使用して、コマンドプロンプトウィンドウを開きます。
   
::: moniker-end


次に、ビジュアルC++開発者コマンドプロンプトが正しくセットアップされていることを確認します。 コマンドプロンプトウィンドウで、「`cl`」と入力し、出力が次のようになっていることを確認します。

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Visual C++のバージョンとインストールされている更新プログラムによっては、現在のディレクトリまたはバージョン番号が異なる場合があります。 上記の出力が表示される場合は、コマンドラインで C またはC++プログラムをビルドする準備ができています。

> [!NOTE]
> "' Cl ' が内部または外部のコマンドとして認識されない、操作可能なプログラムまたはバッチファイル、" エラー C1034 "、または" エラー LNK1104 "などのエラーが表示された場合、 **cl**コマンドを実行すると、開発者コマンドプロンプトをC++使用していないか、またはビジュアルのインストールに問題があります。 続行するには、この問題を修正する必要があります。

[開発者コマンドプロンプト] ショートカットが見つからない場合、または `cl`を入力したときにエラーメッセージがC++表示された場合は、Visual のインストールに問題がある可能性があります。 Visual studio 2017 以降を使用している場合は、visual studio インストーラーでワークロード**を使用C++してデスクトップ開発**を再インストールしてみてください。 詳細については、「 [Visual Studio でサポートをインストールC++ ](vscpp-step-0-installation.md)する」を参照してください。 または、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/)ページからビルドツールを再インストールします。 これが機能するまでは、次のセクションに進んでください。 Visual Studio のインストールとトラブルシューティングの詳細については、「 [Visual studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

> [!NOTE]
> コンピューターの Windows のバージョンおよびシステムセキュリティ構成に応じて、右クリックして 開発者コマンドプロンプト ショートカットのショートカットメニューを開き、**管理者として実行** をクリックして、このチュートリアルに従って作成したプログラムを正常にビルドして実行する必要があります。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>C ソースファイルを作成し、コマンドラインでコンパイルします。

1. [開発者コマンドプロンプト] ウィンドウで `cd c:\` を入力して、現在の作業ディレクトリを C: ドライブのルートに変更します。 次に、`md c:\simple` を入力してディレクトリを作成し、`cd c:\simple` を入力してそのディレクトリに変更します。 このディレクトリには、ソースファイルとコンパイル済みプログラムが格納されます。

1. 開発者コマンドプロンプトで `notepad simple.c` を入力します。 メモ帳の警告ダイアログボックスが表示され**たら、[はい]** をクリックして、作業ディレクトリに新しい単純な .c ファイルを作成します。

1. メモ帳で、次のコード行を入力します。

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. メモ帳のメニューバーで、[**ファイル** > **保存**] を選択して、作業ディレクトリに単純な .c を保存します。

1. [開発者コマンドプロンプト] ウィンドウに戻ります。 コマンドプロンプトで「`dir`」と入力して、c:\ simple ディレクトリの内容を一覧表示します。 ディレクトリの一覧にソースファイル simple .c が表示されます。これは次のようになります。

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   コンピューターの日付とその他の詳細は異なります。 ソースコードファイルが表示されない場合は、作成した c:\ ディレクトリに変更したことを確認し、メモ帳で、ソースファイルをこのディレクトリに保存したことを確認します。 また、.txt 拡張子ではなく、.c のファイル名拡張子でソースコードを保存したことを確認します。

1. プログラムをコンパイルするには、開発者コマンドプロンプトで「`cl simple.c`」と入力します。

   コンパイラによって表示される出力情報の行には、実行可能プログラムの名前 (単純な .exe) が表示されます。

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > "' Cl ' は、内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチファイルとして認識されていません"、"エラー C1034"、または "エラー LNK1104" などのエラーが表示された場合は、開発者コマンドプロンプトが正しくセットアップされていません。 この問題を修正する方法の詳細については、「**開発者コマンドプロンプトを開く**」セクションに戻ってください。

   > [!NOTE]
   > 別のコンパイラまたはリンカーのエラーまたは警告が表示された場合は、ソースコードを確認してエラーを修正し、保存してからコンパイラを再度実行します。 特定のエラーの詳細については、このページの上部にある [検索] ボックスを使用して、エラー番号を確認してください。

1. プログラムを実行するには、コマンドプロンプトで「`simple`」と入力します。

   プログラムは、次のテキストを表示して終了します。

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   これで、コマンドラインを使用して C プログラムをコンパイルして実行しました。

## <a name="next-steps"></a>次のステップ

この "Hello, World" の例は、C プログラムで取得できるのと同じように単純です。 実際のプログラムには、ヘッダーファイルやその他のソースファイルがあり、ライブラリにリンクされているので、便利な作業を行うことができます。

このチュートリアルの手順を使用すると、表示されるサンプルコードを入力する代わりに、独自の C コードを作成できます。 また、他の場所から入手できる多くの C コードサンプルプログラムをビルドすることもできます。 追加のソースコードファイルが含まれているプログラムをコンパイルするには、コマンドラインで次のように入力します。

`cl file1.c file2.c file3.c`

コンパイラは、file1 というプログラムを出力します。 名前を program1 に変更するには、 [/out](reference/out-output-file-name.md)リンカーオプションを追加します。

`cl file1.c file2.c file3.c /link /out:program1.exe`

さらに多くのプログラミングミスを自動的にキャッチするには、 [/W3](reference/compiler-option-warning-level.md)または[/W4](reference/compiler-option-warning-level.md) warning level オプションを使用してコンパイルすることをお勧めします。

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

コンパイラ cl.exe には、コードのビルド、最適化、デバッグ、および分析に適用できる他にも多くのオプションが用意されています。 クイックリストについては、開発者コマンドプロンプトで「`cl /?`」と入力してください。 また、コンパイルとリンクを別々に行い、より複雑なビルドシナリオでリンカーオプションを適用することもできます。 コンパイラとリンカーのオプションと使用法の詳細については、「 [C/C++ビルリファレンス](reference/c-cpp-building-reference.md)」を参照してください。

NMAKE およびメイクファイル、MSBuild およびプロジェクトファイルを使用すると、コマンドラインでより複雑なプロジェクトを構成し、ビルドすることができます。 これらのツールの使用方法の詳細については、「 [NMAKE リファレンス](reference/nmake-reference.md)」および「 [MSBuild](msbuild-visual-cpp.md)」を参照してください。

C とC++言語は似ていますが、同じではありません。 Microsoft C/C++コンパイラ (MSVC) は、単純な規則を使用して、コードをコンパイルするときに使用する言語を決定します。 既定では、MSVC コンパイラは .c で終わるすべてのファイルを C ソースコードとして扱い、.cpp で終わるすべてのファイルC++をソースコードとして扱います。 すべてのファイルを、ファイル名拡張子に依存しない C として処理するようにコンパイラに強制するには、 [/tc](reference/tc-tp-tc-tp-specify-source-file-type.md)コンパイラオプションを使用します。

MSVC は ISO C99 標準と互換性がありますが、厳密には準拠していません。 ほとんどの場合、ポータブル C コードは正常にコンパイルされ、実行されます。 Visual C++では、ISO C11 のほとんどの変更がサポートされていません。 特定のライブラリ関数と POSIX 関数名は、MSVC によって非推奨とされます。 関数はサポートされていますが、優先名が変更されています。 詳細については、「 [CRT のセキュリティ機能](../c-runtime-library/security-features-in-the-crt.md)」および「[コンパイラの警告 (レベル 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)」を参照してください。

## <a name="see-also"></a>関連項目

[チュートリアル: 標準 C++ プログラム (C++) の作成](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 言語リファレンス](../c-language/c-language-reference.md)<br/>
[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)<br/>
[互換性](../c-runtime-library/compatibility.md)
