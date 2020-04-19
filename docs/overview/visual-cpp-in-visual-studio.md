---
title: Visual Studio での C++
description: Visual C++ とは、Microsoft C++ のコンパイラ、コード エディターおよび Visual Studio IDE の関連ツールの名称です。 Visual C++ を使用すると、Windows、Linux、Android および iOS 用のプログラムを開発できます。
ms.date: 07/02/2019
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
ms.openlocfilehash: 0a4093860c7d06e8240e03b1487546f80da24b88
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416102"
---
# <a name="c-in-visual-studio"></a>Visual Studio での C++

> [!NOTE]
> この開発者向けドキュメントは、Visual Studio 2015 以降に適用されます。 自分の Visual Studio のバージョンと合わせるには、ページの左上にあるバージョン セレクターを使います。
>
> プログラムを実行するために Visual C++ 再頒布可能パッケージを探している場合、[Microsoft ダウンロード センター](https://www.microsoft.com/download/)にアクセスして検索ボックスに「**Visual C++** 」と入力してください。

Microsoft Visual C++ (通常は短縮形で Visual C++ または MSVC と表現される) とは、Windows 上で Visual Studio の一部として利用できる C++、C、およびアセンブリ言語の開発ツールおよびライブラリの名前です。 これらのツールとライブラリでは、ユニバーサル Windows プラットフォーム (UWP) アプリ、ネイティブ Windows デスクトップおよびサーバー アプリケーション、Windows、Linux、Android、iOS 上で実行されるクロスプラットフォーム ライブラリおよびアプリに加えて、.NET Framework を使用する管理対象のアプリおよびライブラリを作成できます。 Visual C++ を使用すると、単純なコンソール アプリから最も高度で複雑な Windows デスクトップ用アプリまで、またデバイス ドライバーやオペレーティング システムのコンポーネントからモバイル デバイス用のクロスプラットフォーム ゲームまで、さらに最小の IoT デバイスから Azure クラウドにおけるマルチ サーバー ハイ パフォーマンス コンピューティングに至るまであらゆるアプリを記述することができます。

Visual Studio 2015、2017、および 2019 は、サイド バイ サイドでインストールできます。 Visual Studio 2019 (コンパイラ ツールセット v142) を使い、Visual Studio 2015 (v140) と Visual Studio 2017 (v141) のツールセットを使ってプログラムの編集とビルドを行えます。

## <a name="whats-new-and-conformance-history"></a>新機能および準拠の履歴

[Visual Studio での C++ の新機能](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
Visual C++ の新機能を紹介します。

[Visual Studio 2003 から 2015 の C++ の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Visual Studio 2003 から 2015 までの C++ の新機能をバージョンごとに紹介します。

[Visual Studio の C++ 準拠の強化](cpp-conformance-improvements.md)<br/>
Visual Studio の C++ 準拠の強化について説明します。

[Microsoft C++ 言語の準拠表](visual-cpp-language-conformance.md)<br/>
MSVC C++ コンパイラの各機能の準拠状態を一覧にしています。

[2003 から 2015 の Visual C++ の履歴の変更](../porting/visual-cpp-change-history-2003-2015.md)<br/>
前のバージョンの互換性に影響する変更点について説明します。

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Visual Studio をインストールして、以前のバージョンからアップグレードする

[Visual Studio での C++ サポートのインストール](../build/vscpp-step-0-installation.md)<br/>
Visual Studio 2017 または Visual Studio 2019 をダウンロードして、Visual C++ ツールセットをインストールします。

[Visual C++ 移植とアップグレードのガイド](../porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
より高度な C++ 標準へのコンパイラの準拠および大幅に向上したコンパイル時間とセキュリティ機能 (Spectre の軽減策など) を活用するために、コードを移植してプロジェクトを Visual Studio 2015 以降にアップグレードするためのガイダンスです。

[さまざまな Visual Studio エディションの Visual C++ ツールおよび機能](visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
さまざまな Visual Studio のエディションに関する情報を提供します。

[サポートされているプラットフォーム](supported-platforms-visual-cpp.md)<br/>
サポート対象プラットフォームに関する情報を提供します。

## <a name="learn-c"></a>C++ について

[C++ へようこそ](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
高速で安全なコードを記述し、C スタイルのプログラミングの多くの潜在的な危険を回避するための、C++11 以降に基づく現代的な C++ プログラミング手法に関する情報を提供します。

[標準 C++](https://isocpp.org/)<br/>
C++ について説明しながら、最新の C++ の概要を示すとともに、書籍、記事、講演、イベントなどへのリンクを提供します。

[Visual C++ に関する詳細情報](../build/vscpp-step-1-create.md)<br/>
C++ について導入的に説明します。

[Visual C++ のサンプル](visual-cpp-samples.md)<br/>
サンプルに関する情報です。

## <a name="c-development-tools"></a>C++ 開発ツール

[Visual Studio での C++ 開発の概要](overview-of-cpp-development.md)<br/>
Visual Studio IDE を使用し、プロジェクトの作成、コードの編集、ライブラリへのリンク、コンパイル、デバッグ、単体テストの作成、静的分析の実行、配置などを行う方法です。

[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
MSVC のコンパイラ オプションとリンカー オプションを使用し、Visual Studio C++ プロジェクト、CMake プロジェクト、その他のプロジェクトを作成し、構成する方法です。

[C++ コードの作成とリファクタリング](../ide/writing-and-refactoring-code-cpp.md)<br/>
C++ エディターの生産性機能を使用し、コードのリファクタリング、理解、記述を行う方法です。

[ネイティブ コードのデバッグ](/visualstudio/debugger/debugging-native-code)<br/>
C++ プロジェクトで Visual Studio デバッガーを使用します。

[C/C++ のコード分析の概要](/cpp/code-quality/code-analysis-for-c-cpp-overview)<br/>
静的な分析を行うために、SAL 注釈または C++ Core Guidelines チェッカーを使用します。

[Visual Studio で C/C++ 用の単体テストを作成する](/visualstudio/test/writing-unit-tests-for-c-cpp)<br/>
C++ 用の Microsoft 単体テスト フレームワーク、Google Test、Boost.Test または CTest を使用して、単体テストを作成します。

## <a name="write-applications-in-c"></a>C++ でアプリケーションを作成する

[ユニバーサル Windows アプリ (C++)](../cppcx/universal-windows-apps-cpp.md)<br/>
Windows Developer Center 内にあるガイドとリファレンス コンテンツを探します。 UWP アプリの開発の詳細については、[ユニバーサル Windows プラットフォームの紹介](/windows/uwp/get-started/universal-application-platform-guide)に関するページと、[C++ を使用した最初の UWP アプリの作成](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)に関するページを参照してください。

[デスクトップ アプリケーション (C++)](../windows/desktop-applications-visual-cpp.md)<br/>
Windows 向けの従来のネイティブ C++ デスクトップ アプリケーションの作成方法について説明します。

[C++/CLI による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
ネイティブの C++ と、C# や Visual Basic などの言語で記述されている .NET プログラムの間の相互運用を可能にする DLL の作成方法について説明します。

[Linux でのプログラミング](../linux/index.md)<br/>
GCC でコンパイルするためにリモートの Linux マシンにコードを記述し配置するために Visual Studio IDE を使用します。

[Visual Studio での C/C++ Dll の作成](../build/dlls-in-visual-cpp.md)<br/>
Win32、ATL、および MFC を使用して Windows のデスクトップ DLL を作成する方法と、DLL をコンパイルおよび登録する方法を説明します。

[並列プログラミング](../parallel/parallel-programming-in-visual-cpp.md)<br/>
並列パターン ライブラリ、C++ AMP、OpenMP、その他 Windows 上でのマルチスレッド化に関連する機能を使用する方法を説明します。

[セキュリティ推奨事項](../security/security-best-practices-for-cpp.md)<br/>
悪意のあるコードや不正使用からアプリケーションを保護する方法を説明します。

[クラウドおよび Web プログラミング](../cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
C++ では、Web とクラウドに接続するためのいくつかの方法があります。

[データ アクセス](../data/data-access-in-cpp.md)<br/>
ODBC と OLE DB を使用してデータベースに接続します。

[テキストと文字列](../text/text-and-strings-in-visual-cpp.md)<br/>
さまざまなテキスト形式および文字列形式の処理、およびローカルおよび国際対応の開発におけるエンコーディングの処理について説明します。

## <a name="languages-reference"></a>言語リファレンス

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)

[C/C++ プリプロセッサ リファレンス](../preprocessor/c-cpp-preprocessor-reference.md)

[C 言語リファレンス](../c-language/c-language-reference.md)

[コンパイラの組み込みとアセンブリ言語](../intrinsics/compiler-intrinsics-and-assembly-language.md)

## <a name="c-libraries-in-visual-studio"></a>Visual Studio での C++ ライブラリ

以下のセクションでは、Visual Studio に含まれるさまざまな C および C++ ライブラリについて説明します。

[C ランタイム ライブラリ リファレンス](../c-runtime-library/c-run-time-library-reference.md)<br/>
セキュリティ上の問題が発生することがわかっている関数に対する、セキュリティを強化された代替品が含まれています。

[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
C++ 標準ライブラリ。

[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)<br/>
COM コンポーネントとアプリのサポート。

[Microsoft Foundation Class (MFC) ライブラリ](../mfc/mfc-desktop-applications.md)<br/>
従来型または Office スタイルのユーザー インターフェイスを持つデスクトップ アプリケーションの作成のサポート。

[並列パターン ライブラリ (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
CPU で実行する非同期および並列アルゴリズム。

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
GPU で実行する膨大な並列アルゴリズム。

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
ユニバーサル Windows プラットフォーム (UWP) アプリとコンポーネント。

[C++/CLI による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
共通言語ランタイム (CLR) のプログラミング。

## <a name="third-party-open-source-c-libraries"></a>サード パーティ製オープン ソースの C++ ライブラリ

クロスプラットフォームの **vcpkg** コマンドライン ツールを使用すると、900 を超える C++ オープンソース ライブラリの探索およびインストールを大幅に簡略化することができます。 [Windows 用の C++ パッケージ マネージャー vcpkg に関する記事を参照してください](../build/vcpkg.md)。

## <a name="feedback-and-community"></a>フィードバックとコミュニティ

[Visual C++ ツールセットで問題を報告する方法](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
Visual C++ ツールセット (コンパイラ、リンカー、その他のツール) に対して効果的なエラー レポートを作成する方法とレポートの提出方法について説明します。

Microsoft [C++ チーム ブログ](https://devblogs.microsoft.com/cppblog/)<br/>
Visual Studio の C++ ツールの開発者による新機能と最新の情報に関する詳細を示します。

[Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)<br/>
Visual Studio のサポート、バグの報告、提案に関する情報を提供します。

## <a name="see-also"></a>関連項目

- [C 言語リファレンス](../c-language/c-language-reference.md)
- [C ランタイム ライブラリ リファレンス](../c-runtime-library/c-run-time-library-reference.md)
- [コンパイラの組み込みとアセンブリ言語](../intrinsics/compiler-intrinsics-and-assembly-language.md)
