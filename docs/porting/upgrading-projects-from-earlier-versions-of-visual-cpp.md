---
title: 以前C++のバージョンの Visual Studio からのプロジェクトのアップグレード
description: 旧バージョンの Visual Studio からの Microsoft C++ プロジェクトのアップグレード方法。
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: bc9fb5628c1a628b91f306c346f2bbb1dea13de8
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416109"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>以前C++のバージョンの Visual Studio からのプロジェクトのアップグレード

以前のバージョンの Visual Studio で作成されたプロジェクトをアップグレードするには、最新バージョンの Visual Studio でプロジェクトを開きます。 Visual Studio では、プロジェクトを現在のスキーマにアップグレードすることができます。

**[いいえ]** を選択した場合、プロジェクトはアップグレードされません。 Visual Studio 2010 以降で作成されたプロジェクトの場合でも、新しいバージョンの Visual Studio でプロジェクトを使用できます。 プロジェクトのプロパティを設定して、引き続き古いツールセットを対象にします。 以前のバージョンの Visual Studio をコンピューターに残しておくと、そのツールセットは、以降のバージョンで使用できるようになります。 たとえば、プロジェクトを引き続き Windows XP で実行する必要がある場合は、Visual Studio 2019 にアップグレードできます。 次に、プロジェクトのプロパティで v141_xp またはそれ以前のツールセットを指定します。 詳細については、「[Visual Studio でネイティブ マルチ ターゲットを利用し、古いプロジェクトを作成する](use-native-multi-targeting.md)」を参照してください。

**[はい]** を選択すると、プロジェクトはインプレースアップグレードされます。 以前のバージョンに変換することはできません。 アップグレードシナリオでは、既存のプロジェクトファイルとソリューションファイルのバックアップコピーを作成することをお勧めします。

## <a name="upgrade-reports"></a>レポートのアップグレード

プロジェクトをアップグレードすると、アップグレードレポートが表示できます。 レポートは、UpgradeLog .htm としてプロジェクトフォルダーにも保存されます。 アップグレードレポートには、変換中に検出された問題の概要が表示されます。 次のような変更に関する情報が一覧表示されます。

- プロジェクトのプロパティ。

- インクルードファイル。

- コンパイラ準拠の改善または標準における変更のために、正常にコンパイルされなくなったコード。

- 使用できなくなった Visual Studio または Windows の機能に依存するコード。 または、Visual Studio の既定のインストールに含まれていないか、または製品から削除されたヘッダーファイル。

- Api の名前変更、関数シグネチャの変更、非推奨の関数など、Api の変更によってコンパイルされなくなったコード。

- 警告がエラーになるなど、診断の変更によってコンパイルされなくなったコード

- /NODEFAULTLIB が使用されている場合は特に、変更されたライブラリが原因でリンカーエラーが発生しました。

- 動作の変更により、実行時エラーまたは予期しない結果が発生した。

- ツールで導入されたエラー。 問題が見つかった場合は、通常のサポートチャネルC++を通じて、または[visual Studio C++開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/62/index.html)ページを使用して、ビジュアルチームに報告してください。

アップグレードされたプロジェクトおよびソリューションの中には、変更せずに正常にビルドできるものがあります。 ただし、ほとんどのプロジェクトでは、プロジェクト設定とソースコードの両方を変更する必要が生じる可能性があります。 これらの問題を修正するための1つの正しい方法はありませんが、段階的なアプローチを使用することをお勧めします。 開始する前に、発生する[可能性のあるアップグレードの問題の概要](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)を確認して、さまざまな種類の一般的なエラーの詳細を確認してください。

1. プラットフォームツールセット、 C++言語標準、および Windows SDK バージョン (該当する場合) を優先するバージョンに設定します。 (**プロジェクト** > **プロパティ** > **構成プロパティ** > **全般**)

1. 多数のエラーが発生した場合は、修正中にいくつかのオプションを一時的にオフにすることができます。 [/Permissive-](../build/reference/permissive-standards-conformance.md)オプションをオフにするには、[**プロジェクト** > の**プロパティ** > **構成プロパティ**] > [ **C/C++**  > **言語**] を使用します。 [コード分析](/cpp/code-quality/code-analysis-for-c-cpp-overview)オプションをオフにするには、 **[コード分析]**  > [**プロジェクト** > の**プロパティ** > **構成プロパティ**] を使用します。

1. すべての依存関係が存在し、インクルードパスまたはライブラリの場所が正しいことを確認します。 (**プロジェクト** > **プロパティ** > **VC + + ディレクトリ** > の**構成プロパティ**)

1. 存在しなくなった Api への参照によって発生したエラーを特定し、修正します。

1. コンパイルを妨げる残りのエラーを修正します。 一般的なエラーの修正については、 [「アップグレードに関する潜在的な問題の概要」](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)を参照してください。

1. 以前に MSVC でコンパイルした準拠していないコードによって発生した新しいエラーを修正して、 **/permissive-** を再び有効にします。

1. コード分析を有効にして、許容できない可能性がある潜在的な問題または古くなったコーディングパターンを特定します。 コード分析によって多くのエラーにフラグが設定されている場合は、いくつかの警告をオフにして、最も重要なものを最初に絞り込むことができます。 IDE は、いくつかの種類の問題をすばやく修正するのに役立ちます。

1. コードを最新化する他の機会を検討してください。 たとえば、カスタムデータ構造とアルゴリズムをC++標準ライブラリのものに置き換えるか、オープンソースライブラリをブーストします。 標準機能を使用すると、他のユーザーがコードを簡単に管理できるようになります。 このコードが十分にテストされており、多くの専門家によって標準化委員会や幅広いC++コミュニティでレビューされていることを確信することができます。

修復エラーが発生した場合は、Stack Overflow または[ C++開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/62/index.html)で質問を検索または投稿してみてください。

## <a name="in-this-section"></a>このセクションの内容

[アップグレードに関する潜在的な問題の概要](overview-of-potential-upgrade-issues-visual-cpp.md)\
[コードをユニバーサル CRT にアップグレード](upgrade-your-code-to-the-universal-crt.md)\
[WINVER と _WIN32_WINNT の更新](modifying-winver-and-win32-winnt.md)\
[ライブラリ内部の依存関係を修正](fix-your-dependencies-on-library-internals.md)\
[浮動小数点の移行に関する問題](floating-point-migration-issues.md)\
[Visual Studio 2019 で非推奨の機能\ C++ ](features-deprecated-in-visual-studio.md)
[VCBuild と MSBuild の](build-system-changes.md)\
[ポートサードパーティライブラリ](porting-third-party-libraries.md)

## <a name="see-also"></a>参照

[Visual Studio の Visual C++ の新機能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[ビジュアルC++の変更履歴 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[非標準の動作](../cpp/nonstandard-behavior.md)\
[ポートデータアプリケーション](../data/data-access-programming-mfc-atl.md)
