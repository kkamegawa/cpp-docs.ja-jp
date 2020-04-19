---
title: 'Walkthrough: Compiling a Native C++ Program on the Command Line (チュートリアル: コマンド ラインでのネイティブ C++ プログラムのコンパイル)'
description: コマンドプロンプトからC++ Microsoft コンパイラを使用します。
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: d002fd4c4edc99775e62023dda7998fba2c6a44f
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518175"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Walkthrough: Compiling a Native C++ Program on the Command Line (チュートリアル: コマンド ラインでのネイティブ C++ プログラムのコンパイル)

Visual Studio には、基本的なC++コンソールアプリからユニバーサル Windows プラットフォームアプリ、デスクトップアプリ、デバイスドライバー、.net コンポーネントまで、すべてを作成するために使用できるコマンドラインコンパイラが含まれています。

このチュートリアルでは、"Hello, World"の基本的な作成-エディターでテキストを使用して C++ プログラムのスタイル設定し、それをコマンドラインでコンパイルします。 コマンドラインを使用せずに visual studio ide を試す場合は、「[チュートリアル: プロジェクトとソリューションの使用 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 」または「[デスクトップ開発用のC++ visual studio ide の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照してください。

このチュートリアルでは、表示されている Visual C++ プログラムを入力する代わりに独自の Visual C++ プログラムを使用するか、別のヘルプ記事の Visual C++ コード サンプルを使用できます。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルを完了するには、visual studio と、ワークロードを**使用C++** したオプションのデスクトップ開発、または visual studio 用のコマンドラインビルドツールをインストールしておく必要があります。

Visual Studio は、豊富な機能を備えたエディター、リソースマネージャー、デバッガー、および多くの言語とプラットフォームに対応したコンパイラをサポートする、強力な統合開発環境 (IDE) です。 無料の Visual Studio Community エディションを含む Visual Studio をダウンロードしてインストールする方法については、「 [Visual studio でサポートをインストールC++ ](vscpp-step-0-installation.md)するC++ 」を参照してください。

Build Tools for Visual Studio では、C およびC++プログラムをビルドするために必要なコマンドラインコンパイラ、ツール、およびライブラリのみがインストールされます。 これは、ビルドラボやクラスルームの演習や、比較的迅速なインストールに最適です。 コマンドラインツールのみをインストールするには、 [Visual studio のダウンロード](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)ページで [Build Tools For visual studio] を探します。

C またはC++プログラムをコマンドラインでビルドする前に、ツールがインストールされていること、およびコマンドラインからアクセスできることを確認する必要があります。 ビジュアルC++には、コマンドライン環境が使用するツール、ヘッダー、およびライブラリを見つけるための複雑な要件があります。 一部の準備を行わず**に、単純なコマンドプロンプトウィンドウでビジュアルC++を使用することはできません**。 さいわい、Visual C++は、コマンドラインビルド用に環境が設定されている開発者コマンドプロンプトを起動するためのショートカットをインストールします。 残念ながら、開発者コマンドプロンプトのショートカットの名前と配置場所は、ほぼすべてのバージョンのビジュアルC++と、異なるバージョンの Windows で異なります。 最初のチュートリアルタスクで、使用する適切なものを見つけます。

> [!NOTE]
> 開発者コマンドプロンプトのショートカットを使用すると、コンパイラおよびツールの正しいパス、および必要なヘッダーとライブラリが自動的に設定されます。 通常の**コマンドプロンプト**ウィンドウを使用する場合は、これらの環境値を自分で設定する必要があります。 詳細については、[コマンド ライン ビルドのパスと環境変数の設定](setting-the-path-and-environment-variables-for-command-line-builds.md)に関するページを参照してください。 独自に構築するのではなく、開発者コマンドプロンプトのショートカットを使用することをお勧めします。

### <a name="open-a-developer-command-prompt"></a>開発者コマンドプロンプトを開く

1. Windows 10 に Visual Studio 2017 以降がインストールされている場合は、スタート メニューを開き、**すべてのアプリ** を選択します。 下へスクロールし、 **visual studio フォルダー (** visual studio アプリケーションではありません) を開きます。 [ **VS] の [開発者コマンドプロンプト**] を選択して、コマンドプロンプトウィンドウを開きます。

   Windows 10 に Microsoft Visual C++ Build Tools 2015 がインストールされている場合は、 **[スタート]** メニューを開き、すべての **[アプリ]** を選択します。 下にスクロールし、 **[ C++ Visual Build Tools** ] フォルダーを開きます。 **[Visual C++ 2015 x86 Native Tools コマンドプロンプト]** を選択して、コマンドプロンプトウィンドウを開きます。

   また、Windows search 関数を使用して "developer command prompt" を検索し、インストールされている Visual Studio のバージョンに一致するものを選択することもできます。 ショートカットを使用して、コマンドプロンプトウィンドウを開きます。

1. 次に、ビジュアルC++開発者コマンドプロンプトが正しくセットアップされていることを確認します。 コマンドプロンプトウィンドウで、「`cl`」と入力し、出力が次のようになっていることを確認します。

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Visual C++のバージョンとインストールされている更新プログラムによっては、現在のディレクトリまたはバージョン番号が異なる場合があります。 上記の出力が表示される場合は、コマンドラインで C またはC++プログラムをビルドする準備ができています。

   > [!NOTE]
   > "' Cl ' が内部または外部のコマンドとして認識されない、操作可能なプログラムまたはバッチファイル、" エラー C1034 "、または" エラー LNK1104 "などのエラーが表示された場合、 **cl**コマンドを実行すると、開発者コマンドプロンプトをC++使用していないか、またはビジュアルのインストールに問題があります。 続行するには、この問題を修正する必要があります。

   [開発者コマンドプロンプト] ショートカットが見つからない場合、または `cl`を入力したときにエラーメッセージがC++表示された場合は、Visual のインストールに問題がある可能性があります。 Visual Studio でビジュアルC++コンポーネントを再インストールするか、Microsoft Visual C++ビルドツールを再インストールしてみてください。 これが機能するまでは、次のセクションに進んでください。 ビジュアルC++のインストールとトラブルシューティングの詳細については、「 [Visual Studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

   > [!NOTE]
   > コンピューターの Windows のバージョンおよびシステムセキュリティ構成に応じて、右クリックして 開発者コマンドプロンプト ショートカットのショートカットメニューを開き、**管理者として実行** をクリックして、このチュートリアルに従って作成したプログラムを正常にビルドして実行する必要があります。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Visual C++ source ファイルを作成し、コマンドラインでコンパイルします。

1. [開発者コマンドプロンプト] ウィンドウで、`md c:\hello` を入力してディレクトリを作成し、`cd c:\hello` を入力してそのディレクトリに変更します。 このディレクトリは、ソースファイルとコンパイル済みプログラムがで作成される場所です。

1. [コマンドプロンプト] ウィンドウに `notepad hello.cpp` を入力します。

   メモ帳でファイルを作成するように求めるメッセージが表示されたら、 **[はい]** を選択します。 この手順では、空のメモ帳ウィンドウが開き、hello .cpp という名前のファイルにコードを入力できるようになります。

1. メモ帳で、次のコード行を入力します。

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   このコードは、画面に1行のテキストを書き込み、終了する単純なプログラムです。 エラーを最小限に抑えるには、このコードをコピーし、メモ帳に貼り付けます。

1. 作業内容を保存します。 メモ帳で、 **[ファイル]** メニューの **[保存]** を選びます。

   これで、コンパイルの準備C++ができているソースファイルである hello .cpp が作成されました。

1. [開発者コマンドプロンプト] ウィンドウに戻ります。 コマンドプロンプトで「`dir`」と入力して、c:\ ディレクトリの内容を一覧表示します。 ディレクトリの一覧に、ソースファイルの hello .cpp が表示されます。次のようになります。

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   コンピューターの日付とその他の詳細は異なります。 ソースコードファイルが表示されない場合は、作成した c:\ ディレクトリに変更したことを確認し、メモ帳で、ソースファイルをこのディレクトリに保存したことを確認します。 また、.txt 拡張子ではなく、.cpp ファイル名拡張子を持つソースコードを保存したことを確認します。

1. 開発者コマンドプロンプトで、「`cl /EHsc hello.cpp`」と入力してプログラムをコンパイルします。

   cl.exe コンパイラによって、コンパイルされたコードを含む .obj ファイルが生成され、リンカーが実行されて hello.exe という名前の実行可能プログラムが作成されます。 この名前は、コンパイラによって表示される出力情報の行に表示されます。 コンパイラの出力は次のようになります。

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > "' Cl ' は、内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチファイルとして認識されていません"、"エラー C1034"、または "エラー LNK1104" などのエラーが表示された場合は、開発者コマンドプロンプトが正しくセットアップされていません。 この問題を修正する方法の詳細については、「**開発者コマンドプロンプトを開く**」セクションに戻ってください。

   > [!NOTE]
   > 別のコンパイラまたはリンカーのエラーまたは警告が表示された場合は、ソースコードを確認してエラーを修正し、保存してからコンパイラを再度実行します。 特定のエラーの詳細については、この MSDN ページの検索ボックスを使用して、エラー番号を確認してください。

1. hello.exe プログラムを実行するには、コマンド プロンプトで `hello`と入力します。

   プログラムは、次のテキストを表示して終了します。

   ```Output
   Hello, world, from Visual C++!
   ```

   これで、コマンドラインツールを使用C++してプログラムをコンパイルして実行できました。

## <a name="next-steps"></a>次のステップ:

この"Hello, World"の例は、単純な C++ プログラムを取得できます。 実際のプログラムではヘッダー ファイルとより多くのソース ファイルがあり、ライブラリにリンクし、有益な処理を実行します。

このチュートリアルの手順を使用すると、表示されるC++サンプルコードを入力する代わりに、独自のコードを作成できます。 他の場所にあるC++多くのコードサンプルプログラムをビルドすることもできます。 ソースコードを配置し、任意の書き込み可能なディレクトリにアプリを構築することができます。 既定では、visual studio IDE は、使用している Visual studio のバージョンに対してという名前の Visual Studio フォルダーの Projects サブフォルダー内にあるプロジェクトをドキュメントフォルダーに作成します。

追加のソースコードファイルが含まれているプログラムをコンパイルするには、コマンドラインで次のように入力します。

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` は、コンパイラに対して C++ 例外処理を有効化するよう指示するコマンド ライン オプションです。 詳細については、「[/EH (例外処理モデル)](reference/eh-exception-handling-model.md)」を参照してください。

追加のソースファイルを指定すると、コンパイラは最初の入力ファイルを使用してプログラム名を作成します。 この場合、file1 というプログラムが出力されます。 名前を program1 に変更するには、 [/out](reference/out-output-file-name.md)リンカーオプションを追加します。

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

さらに多くのプログラミングミスを自動的にキャッチするには、 [/W3](reference/compiler-option-warning-level.md)または[/W4](reference/compiler-option-warning-level.md) warning level オプションを使用してコンパイルすることをお勧めします。

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

コンパイラ cl.exe には、コードのビルド、最適化、デバッグ、および分析に適用できる他にも多くのオプションが用意されています。 クイックリストについては、開発者コマンドプロンプトで「`cl /?`」と入力してください。 また、コンパイルとリンクを別々に行い、より複雑なビルドシナリオでリンカーオプションを適用することもできます。 コンパイラとリンカーのオプションと使用法の詳細については、「 [C/C++ビルリファレンス](reference/c-cpp-building-reference.md)」を参照してください。

NMAKE およびメイクファイル、MSBuild およびプロジェクトファイルを使用すると、コマンドラインでより複雑なプロジェクトを構成し、ビルドすることができます。 これらのツールの使用方法の詳細については、「 [NMAKE リファレンス](reference/nmake-reference.md)」および「 [MSBuild](msbuild-visual-cpp.md)」を参照してください。

C とC++言語は似ていますが、同じではありません。 MSVC コンパイラは、単純なルールを使用して、コードをコンパイルするときに使用する言語を決定します。 既定では、MSVC コンパイラは .c で終わるすべてのファイルを C ソースコードとして扱い、.cpp で終わるすべてのファイルC++をソースコードとして扱います。 すべてのファイルをファイル名拡張子に依存C++しないものとして扱うようにコンパイラに強制するには、 [/tp](reference/tc-tp-tc-tp-specify-source-file-type.md)コンパイラオプションを使用します。

MSVC コンパイラには、ISO C99 標準と互換性があるが厳密に準拠していない C ランタイムライブラリ (CRT) が含まれています。 ほとんどの場合、移植性の高いコードは正常にコンパイルされ、実行されます。 Visual C++は、ISO C11 の一部の CRT 変更をサポートしていません。 特定のライブラリ関数と POSIX 関数名は、MSVC コンパイラによって非推奨とされます。 関数はサポートされていますが、優先名が変更されています。 詳細については、「 [CRT のセキュリティ機能](../c-runtime-library/security-features-in-the-crt.md)」および「[コンパイラの警告 (レベル 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)<br/>
[MSVC コンパイラ オプション](reference/compiler-options.md)
