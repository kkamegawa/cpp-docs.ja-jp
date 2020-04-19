---
title: Visual C++ ファイルの再配布
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: b64fac7086dcc22199ca359a163074b967c56f95
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450620"
---
# <a name="redistributing-visual-c-files"></a>Visual C++ ファイルの再配布

> [!NOTE]
> Visual C++ ランタイム ファイルのいずれかのダウンロードをお探しの場合は、 移動して、 [Microsoft web サイト](https://www.microsoft.com/)入力**Visual C Redistributable**検索ボックスにします。 次に、お使いのコンピューターのアーキテクチャ用の再頒布可能パッケージ (たとえば、64 ビット Windows を実行している場合は x64) と、必要な Visual C++ のバージョン (たとえば、2015) をダウンロードしてインストールします。

アプリケーションを配置する場合は、アプリケーションをサポートするために必要なすべてのファイルも配置する必要があります。 必要なファイルに Microsoft から提供されるファイルが含まれる場合、それを再配布する権限を持っているかどうか確認します。 Visual Studio のライセンス条項を確認するには、IDE の Microsoft Visual Studio のバージョン情報ダイアログ ボックスでライセンス条項リンクを参照するか、[マイクロソフト ソフトウェア ライセンス条項](https://visualstudio.microsoft.com/license-terms/mlt687465/)ファイルをダウンロードします。 Visual Studio の特定のエディションのマイクロソフト ソフトウェア ライセンス条項の「頒布可能コード」セクションで言及されている "再頒布リスト" を表示する場合は、「[Microsoft Visual Studio 2017 の頒布可能コード (ユーティリティ、機能拡張、および BuildServer ファイルを含む)](/visualstudio/productinfo/2017-redistribution-vs)」を参照してください。Visual Studio 2015 の場合は、「[Microsoft Visual Studio 2015 および Microsoft Visual Studio 2015 SDK の頒布可能コード (ユーティリティおよび BuildServer ファイルを含む)](/visualstudio/productinfo/2015-redistribution-vs)」を参照してください。 再頒布可能ファイルの詳細については、「[再配布する Dll の決定](determining-which-dlls-to-redistribute.md)」と「[配置例](deployment-examples.md)」を参照してください。

再頒布可能な Visual C++ ファイルを配置する場合は、Visual Studio に含まれている Visual C++ 再頒布可能パッケージ (VCRedist\_x86.exe、VCRedist\_x64.exe、または VCRedist\_arm.exe) を使用できます。 Visual Studio 2017 では、これらのファイルは Program Files[(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_ フォルダーにあります。ここで、_edition_ はインストールされている Visual Studio のエディション、_lib-version_ は再配布するライブラリのバージョンです。 Visual Studio 2015 では、これらのファイルは、Visual Studio インストール ディレクトリ (Program Files [(x86)]\Microsoft Visual Studio *バージョン*\VC\redist\\*locale*\\) にあります。 再頒布可能マージ モジュール (.msm ファイル) を使用することもできます。Visual Studio 2017 の場合、このモジュールは、Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_\\MergeModules\\ フォルダーにあります。 Visual Studio 2015 の場合は、Program Files [(x86)]\Common Files\Merge Modules\\ にあります。 実行可能なアプリケーション ファイルを含むフォルダーである、*アプリケーション ローカル フォルダー*に再頒布可能な Visual C++ DLL を直接インストールすることもできます。 サービス上の理由から、このインストール場所を使用することはお勧めしません。

Visual C++ 再頒布可能パッケージでは、すべての Visual C++ ライブラリがインストールされ、登録されます。 その 1 つを使用する場合は、アプリケーション インストールの必要条件として、インストール先のシステムでそれが実行されるように設定する必要があります。 配置ではこのパッケージを使用することをお勧めします。これにより、Visual C++ ライブラリの自動更新が有効になるためです。 例については、これらのパッケージを使用する方法は、次を参照してください。[チュートリアル。Visual C++ 再頒布可能パッケージを使用した Visual C++ アプリケーションの配置](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)」を参照してください。

各 Visual C++ 再頒布可能パッケージは、より新しいバージョンがコンピューター上に存在するかどうかを確認します。 より新しいバージョンが見つかった場合、パッケージはインストールされません。 Visual Studio 2015 以降では、再頒布可能パッケージのセットアップが失敗したことを示すエラー メッセージが表示されます。 **/quiet** フラグを使用してパッケージを実行した場合、エラー メッセージは表示されません。 いずれの場合も、Microsoft インストーラーによってエラーがログ記録され、エラー結果が呼び出し元に返されます。 Visual Studio 2015 パッケージ以降では、レジストリを確認して、より新しいバージョンがインストールされているかどうかを調べると、このエラーを回避できます。 現在インストールされているバージョンは HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_vs-version_\VC\Runtimes\\{x86|x64|ARM} キーに格納されています。ここで、_vs-version_ は Visual Studio のバージョン番号 (更新された 2017 再頒布可能パッケージは 2015 バージョンとバイナリ互換性があるため、Visual Studio 2015 と Visual Studio 2017 の両方とも 14.0)、キーはプラットフォームのインストールされている vcredist バージョンに応じて ARM、x86、または x64 となります (RegEdit を使用して x64 プラットフォームにインストールされている x86 パッケージのバージョンを表示する場合を除き、Wow6432Node サブキーの下を確認する必要はありません)。バージョン番号は REG_SZ 文字列値の **Version** に格納されています。また、**Major**、**Minor**、**Bld**、および **Rbld** REG_DWORD の値のセットで示されています。 インストール時のエラーを回避するため、現在インストールされているバージョンの方が新しい場合は、再頒布可能パッケージのインストールをスキップする必要があります。

Visual C++ DLL を含むマージ モジュールを使用する場合は、アプリケーションを配置するために使用する Windows インストーラー パッケージ (または同様のインストール パッケージ) にそのモジュール含める必要があります。 詳細については、「[マージ モジュールを使用した再配布](redistributing-components-by-using-merge-modules.md)」を参照してください。 例については、「[チュートリアル: セットアップ プロジェクトを Visual C++ を使ったアプリケーションを配置](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)、InstallShield Limited Edition を使用して、インストール パッケージを作成する方法も示しています。

## <a name="potential-run-time-errors"></a>発生する可能性のある実行時エラー

Windows 見つけられない場合、再頒布可能ライブラリ アプリケーションに必要な Dll のいずれか、次のようなメッセージが表示されます。"このアプリケーションは、ために、起動に失敗しました*ライブラリ*.dll が見つかりませんでした。 アプリケーションをインストールし直すとこの問題が解決される場合があります" のようなメッセージが表示される可能性があります。

この種のエラーを解決するには、アプリケーション インストーラーが正しくビルドされていることと、再頒布可能ライブラリがターゲット システムに正しく配置されていることを確認します。 詳細については、「[Visual C++ アプリケーションの依存関係の理解](understanding-the-dependencies-of-a-visual-cpp-application.md)」を参照してください。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[マージ モジュールを使用した再配布](redistributing-components-by-using-merge-modules.md)|Visual C++ 再頒布可能マージ モジュールを使用して、Visual C++ ランタイム ライブラリを共有 DLL として %windir%\system32\ フォルダーにインストールする方法について説明します。|
|[Visual C++ ActiveX コントロールの再頒布](redistributing-visual-cpp-activex-controls.md)|ActiveX コントロールを使用するアプリケーションを再配布する方法について説明します。|
|[MFC ライブラリの再頒布](redistributing-the-mfc-library.md)|MFC を使用するアプリケーションを再配布する方法について説明します。|
|[ATL アプリケーションの再頒布](redistributing-an-atl-application.md)|ATL を使用するアプリケーションを再頒布する方法について説明します。 Visual Studio 2012 以降では、ATL 用の再頒布可能ライブラリは必要ありません。|
|[配置例](deployment-examples.md)|Visual C++ アプリケーションを配置する方法の例にリンクします。|
|[デスクトップ アプリケーションの配置](deploying-native-desktop-applications-visual-cpp.md)|Visual C++ の配置の概念とテクノロジの概要です。|