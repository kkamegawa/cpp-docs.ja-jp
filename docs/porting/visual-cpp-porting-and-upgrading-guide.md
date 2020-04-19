---
title: Microsoft C++移植およびアップグレードガイド
description: Microsoft C++ code を最新バージョンの Visual Studio にアップグレードします。
ms.date: 11/18/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 723879ad03b9b66c7490804e890f07d6d55e9dae
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303347"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Microsoft C++移植およびアップグレードガイド

この記事では、Microsoft C++ code を最新バージョンの Visual Studio にアップグレードするためのガイドを提供します。 Visual Studio 2010 から2015で作成されたプロジェクトの場合は、Visual Studio 2019 でプロジェクトを開きます。 Visual Studio 2008 以前のプロジェクトをアップグレードするには、2つの手順を実行します。 Visual Studio 2010 を使用して、最初にプロジェクトを MSBuild 形式に変換します。 次に、Visual Studio 2019 でプロジェクトを開きます。 詳細な手順については、「[以前のバージョンの Visual Studio からのプロジェクトのアップグレードC++ ](upgrading-projects-from-earlier-versions-of-visual-cpp.md)」を参照してください。

Visual Studio 2015、Visual Studio 2017、および Visual Studio 2019 のツールセットは、バイナリと互換性があります。 これで、ライブラリの依存関係をアップグレードしなくても、より新しいバージョンのコンパイラにアップグレードできるようになりました。 詳細については、「 [ C++バイナリ互換性 2015-2019](binary-compat-2015-2017.md)」を参照してください。

オープンソースライブラリを使用するプロジェクトをアップグレードする場合、または複数のプラットフォームで実行する場合は、CMake ベースのプロジェクトに移行することをお勧めします。 詳細については、「 [Visual Studio での Cmake プロジェクト](../build/cmake-projects-in-visual-studio.md)」を参照してください。

## <a name="reasons-to-upgrade-c-code"></a>コードをアップグレードC++する理由

レガシアプリケーションが十分に実行されており、セキュリティで保護された環境で動作しておらず、アクティブな開発中でない場合は、アップグレードする必要がありません。 ただし、このような場合は、アプリケーションが継続的なメンテナンスを必要とする場合に備えて、アップグレードを検討してください。 または、新しい機能の開発を行ったり、パフォーマンスやセキュリティを向上させたりしています。 アップグレードには次のような利点があります。

- コンパイラの最適化が改善されたため、同じコードをより高速に実行できます。

- 最新C++の機能とプログラミング手法により、バグの一般的な原因が多くなくなり、以前の C スタイルの表現よりもはるかに簡単に保守できるコードが生成されます。

- コンパイラとリンカーのパフォーマンスが向上しているため、ビルド時間が短縮されます。

- 標準への準拠の向上。 [/Permissive-](../build/reference/permissive-standards-conformance.md)コンパイラオプションは、現在C++の標準に準拠していないコードを特定するのに役立ちます。

- より安全な[C ランタイムライブラリ](../c-runtime-library/security-features-in-the-crt.md)機能を含む、実行時のセキュリティが向上します。 また、[ガードチェック](../build/reference/guard-enable-guard-checks.md)やアドレス Sanitizers (Visual Studio 2019 バージョン16.4 の新機能) などのコンパイラ機能。

## <a name="multitargeting-vs-upgrading"></a>マルチターゲットとアップグレード

おそらく、コードベースを新しいツールセットにアップグレードすることはできません。 最新の Visual Studio を使用して、以前のツールセットとライブラリを使用するプロジェクトをビルドおよび編集することもできます。 Visual Studio 2019 では、次のような機能を利用できます。

- 主要なガイドラインチェッカーや Clang C++ -Tidy などの最新の静的分析ツールを使用すると、ソースコードの潜在的な問題を特定するのに役立ちます。

- 最新のスタイルの選択に応じてオートフォーマットを使用すると、従来のコードをより読みやすくするのに役立ちます。

詳細については、「[Visual Studio でネイティブ マルチ ターゲットを利用し、古いプロジェクトを作成する](use-native-multi-targeting.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

|タイトル|説明|
|-----------|-----------------|
|[以前C++のバージョンの Visual Studio からのプロジェクトのアップグレード](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|コードベースを Visual Studio 2019 および v142 のコンパイラにアップグレードする方法について説明します。|
|[コードをアップグレードC++するための IDE ツール](ide-tools-for-upgrading-code.md)|アップグレードプロセスに役立つ IDE の便利な機能。|
|[C++バイナリ互換性2015-2019](binary-compat-2015-2017.md)|V142 プロジェクトから、v140 と v141 のライブラリをそのように使用します。|
|[Visual Studio でネイティブ マルチ ターゲットを利用し、古いプロジェクトを作成する](use-native-multi-targeting.md)|以前のコンパイラとライブラリで Visual Studio 2019 を使用します。|
|[Visual C++ 2003 ～ 2015 の変更履歴](visual-cpp-change-history-2003-2015.md)|Visual Studio 2003 から2015の Microsoft C++ライブラリおよびビルドツールのすべての変更の一覧。コードの変更が必要になる場合があります。|
|[2003 ～ 2015 年の Visual C++ の新機能](visual-cpp-what-s-new-2003-through-2015.md)|Visual Studio 2003 から Visual studio 2015 までの Microsoft C++の "新機能" のすべての情報。|
|[移植およびアップグレード: 例とケース スタディ](porting-and-upgrading-examples-and-case-studies.md)|このセクションでは、いくつかのサンプルとアプリケーションを移植してアップグレードし、エクスペリエンスと結果について説明しました。 これらの記事では、移植とアップグレードのプロセスに何が関係しているかを理解できます。 プロセス全体を通して、アップグレードに関するヒントとテクニックについて説明し、特定のエラーを修正する方法を示します。|
|[ユニバーサル Windows プラットフォームへの移植](porting-to-the-universal-windows-platform-cpp.md)|コードを Windows 10 に移植する方法を説明します。|
|[Visual C++ の紹介 (UNIX ユーザー向け)](introduction-to-visual-cpp-for-unix-users.md)|Visual C++ を初めて使用し、生産性を向上したい UNIX ユーザー向けの情報を提供します。|
|[Windows での Linux プログラムの実行](porting-from-unix-to-win32.md)|UNIX アプリケーションを Windows に移行するためのオプションについて説明します。|

## <a name="see-also"></a>参照

[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[Visual Studio での C++ コンパイラの新機能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual Studio の C++ 準拠の強化](../overview/cpp-conformance-improvements.md)<br/>
