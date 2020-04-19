---
title: C++ でプログラミングする Windows の概要
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 96a03194059f59f57780bfd70cab3065d6a1aff0
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127195"
---
# <a name="overview-of-windows-programming-in-c"></a>C++ でプログラミングする Windows の概要

でC++作成できる Windows アプリケーションには、さまざまなカテゴリがあります。 それぞれに独自のプログラミングモデルと一連の Windows 固有のライブラリがありますC++が、標準ライブラリとサードC++パーティのライブラリはいずれのライブラリでも使用できます。 

このセクションでは、Visual Studio と MFC/ATL ラッパーライブラリを使用して Windows プログラムを作成する方法について説明します。 Windows プラットフォーム自体に関するドキュメントについては、 [windows のドキュメント](/windows/index)を参照してください。

## <a name="command-line-console-applications"></a>コマンドライン (コンソール) アプリケーション

C++コンソールアプリケーションは、コンソールウィンドウでコマンドラインから実行され、テキスト出力のみを表示できます。 詳細については、「 [ C++コンソールアプリプロジェクトの作成](../get-started/tutorial-console-cpp.md)」を参照してください。

## <a name="native-desktop-client-applications"></a>ネイティブデスクトップクライアントアプリケーション

*ネイティブデスクトップクライアントアプリケーション*は、元のネイティブC++ [Windows C Api またはコンポーネントオブジェクトモデル (COM) api](/windows/win32/apiindex/windows-api-list)を使用してオペレーティングシステムにアクセスする、C またはウィンドウアプリケーションです。 これらの Api 自体は、主に C で記述されています。ネイティブデスクトップアプリを作成する方法は複数あります。オペレーティングシステムイベントを処理する C スタイルのメッセージループを使用して、Win32 Api を直接使用してプログラミングすることができます。 または、Win32 をラップする軽いオブジェクト指向C++ライブラリである Microsoft Foundation Classes (MFC) を使用してプログラミングすることもできます。 どちらの方法も、ユニバーサル Windows プラットフォーム (UWP) と比較して "現代" とは見なされませんが、どちらも完全にサポートされており、今日の世界で何百万ものコードが実行されています。 ウィンドウで実行される Win32 アプリケーションでは、開発者が Windows プロシージャ関数内で Windows メッセージを明示的に操作する必要があります。 名前にかかわらず、Win32 アプリケーションは、32ビット (x86) または64ビット (x64) のバイナリとしてコンパイルできます。 Visual Studio IDE では、x86 と Win32 という用語は同義です。

従来の Windows C++プログラミングの概要については、「 [Win32 およびC++の概要](/windows/win32/LearnWin32/learn-to-program-for-windows)」を参照してください。 Win32 について理解を深めた後は、 [MFC デスクトップアプリケーション](../mfc/mfc-desktop-applications.md)について簡単に学習できます。 洗練されたグラフィックスをC++使用する従来のデスクトップアプリケーションの例[については、「hilo:C++ Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)用アプリケーションの開発。

### <a name="c-or-net"></a>C++または .NET?

一般に、のC# .net プログラミングは、複雑でエラーが発生しにくく、より最新のオブジェクト指向 API を WIN32 や MFC よりも多く備えています。 ほとんどの場合、パフォーマンスは十分ではありません。 .NET には、リッチグラフィックス用の Windows Presentation Foundation (WPF) が用意されており、Win32 と最新の Windows ランタイム API の両方を使用できます。 一般的な規則として、次C++のことを必要とする場合は、デスクトップアプリケーションにを使用することをお勧めします。

- メモリ使用量の詳細な制御
- 電力消費の最高経済
- 一般的なコンピューティングでの GPU の使用
- DirectX へのアクセス
- 標準C++ライブラリの大量使用

また、のC++パワーと効率を .net プログラミングと組み合わせることもできます。 でC#ユーザーインターフェイスを作成し、/cli をC++使用してアプリケーションがネイティブC++ライブラリを使用できるようにすることができます。 詳細については、「 [/cli C++を使用した .net プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)」を参照してください。

## <a name="com-components"></a>COM コンポーネント

[コンポーネントオブジェクトモデル (COM)](/windows/win32/com/the-component-object-model)は、さまざまな言語で記述されたプログラムが相互に通信できるようにするための仕様です。 多くの Windows コンポーネントは COM オブジェクトとして実装され、オブジェクトの作成、インターフェイスの検出、およびオブジェクトの破棄に関する標準的な COM 規則に従います。  デスクトップアプリケーションからC++ com オブジェクトを使用するのは比較的簡単ですが、独自の com オブジェクトを作成する方がより高度です。 [Active Template Library (ATL)](../atl/atl-com-desktop-components.md)には、COM 開発を簡略化するマクロとヘルパー関数が用意されています。 詳細については、「 [ATL COM デスクトップコンポーネント](../atl/atl-com-desktop-components.md)」を参照してください。

## <a name="universal-windows-platform-apps"></a>ユニバーサル Windows プラットフォーム アプリ

ユニバーサル Windows プラットフォーム (UWP) は、最新の Windows API です。 UWP アプリは、任意の Windows 10 デバイスで実行され、ユーザーインターフェイスに XAML を使用し、完全にタッチ対応になっています。 UWP の詳細については、「[ユニバーサル Windows プラットフォーム (uwp) アプリとは](/windows/uwp/get-started/whats-a-uwp)」と「[ユニバーサル Windows プラットフォーム ガイド](/windows/uwp/get-started/universal-application-platform-guide)」を参照してください。

UWP のC++元のサポートは、(1) C++/cx、構文拡張をC++使用した言語、または (2) 標準C++と COM に基づく Windows ランタイムライブラリ (wrl) で作成されました。 /Cx C++と wrl は両方ともサポートされています。 新しいプロジェクトの場合は、標準C++に基づいていて、より高速なパフォーマンスを提供する、 [ C++WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)をお勧めします。

## <a name="desktop-bridge"></a>デスクトップブリッジ

Windows 10 では、既存のデスクトップアプリケーションまたは COM オブジェクトを UWP アプリとしてパッケージ化し、touch などの UWP 機能を追加したり、最新の Windows API セットから Api を呼び出したりすることができます。 また、UWP アプリを Visual Studio のデスクトップソリューションに追加し、1つのパッケージにまとめてパッケージ化し、Windows Api を使用してそれらの間で通信を行うこともできます。

Visual Studio 2017 バージョン15.4 以降では、Windows アプリケーションパッケージプロジェクトを作成して、既存のデスクトップアプリケーションをパッケージ化する作業を大幅に簡略化できます。 デスクトップアプリケーションで使用できるレジストリ呼び出しまたは Api には、いくつかの制限が適用されます。 ただし、多くの場合、代替コードパスを作成して、アプリパッケージでの実行中に同様の機能を実現できます。 詳細については、[デスクトップ ブリッジ](/windows/uwp/porting/desktop-to-uwp-root)に関するページをご覧ください。

## <a name="games"></a>ゲーム

DirectX ゲームは、PC または Xbox で実行できます。 詳細については、「 [DirectX のグラフィックスとゲーム](/windows/win32/directx)」を参照してください。

## <a name="sql-server-database-clients"></a>SQL Server データベースクライアント

ネイティブコードから SQL Server データベースにアクセスするには、ODBC または OLE DB を使用します。 詳細については、「 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)」を参照してください。

## <a name="windows-device-drivers"></a>Windows デバイス ドライバー

ドライバーは、ハードウェアデバイスからのデータをアプリケーションやその他のオペレーティングシステムコンポーネントからアクセスできるようにするための下位レベルのコンポーネントです。 詳細については、「 [Windows Driver Kit (WDK)](/windows-hardware/drivers/index)」を参照してください。

## <a name="windows-services"></a>Windows サービス

Windows*サービス*は、ユーザーの操作をほとんどまたはまったく行わずにバックグラウンドで実行できるプログラムです。 これらのプログラムは、UNIX システムでは*デーモン*と呼ばれています。 詳細については、「[サービス](/windows/win32/services/services)」を参照してください。

## <a name="sdks-libraries-and-header-files"></a>Sdk、ライブラリ、およびヘッダーファイル

Visual Studio には、C ランタイムライブラリ (CRT)、 C++標準ライブラリ、およびその他の Microsoft 固有のライブラリが含まれています。 これらのライブラリのヘッダーファイルが含まれているインクルードフォルダーのほとんどは、Visual Studio のインストールディレクトリの \ VC\ フォルダーに配置されています。 Windows および CRT のヘッダーファイルは、Windows SDK インストールフォルダーにあります。

[Vcpkg package manager](../build/vcpkg.md)を使用すると、多数のサードパーティ製のオープンソースライブラリ (Windows 用) を簡単にインストールできます。

Microsoft ライブラリには次のものが含まれます。

- Microsoft Foundation Classes (MFC):従来の Windows プログラム (特にエンタープライズアプリケーション) を作成するためのオブジェクト指向フレームワーク。機能ボタン、リストボックス、ツリービュー、およびその他のコントロールを備えた豊富なユーザーインターフェイスを備えています。 詳細については、「 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)」を参照してください。

- Active Template Library (ATL):COM コンポーネントを作成するための強力なヘルパーライブラリ。 詳細については、「 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)」を参照してください。

- C++AMP (C++高速で大規模な並列処理):GPU での高パフォーマンスの一般的な計算作業を可能にするライブラリ。 詳細については、「 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)」を参照してください。

- 同時実行ランタイム:マルチコアおよび多コアデバイスの並列プログラミングと非同期プログラミングの作業を簡略化するライブラリ。 詳細については、「[コンカレンシー ランタイム](../parallel/concrt/concurrency-runtime.md)」を参照してください。

Windows プログラミングの多くのシナリオでは、Windows SDK も必要になります。これには、Windows オペレーティング システム コンポーネントへのアクセスを可能にするためのヘッダー ファイルが含まれています。 既定では、Visual Studio はC++デスクトップワークロードのコンポーネントとして Windows SDK をインストールします。これにより、ユニバーサル Windows アプリの開発が可能になります。 UWP アプリを開発するには、Windows SDK の Windows 10 バージョンが必要です。 詳細については、「 [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)」を参照してください。 (以前のバージョンの Windows 用 Windows Sdk の詳細については、「 [Windows SDK archive](https://developer.microsoft.com/windows/downloads/sdk-archive)」を参照してください)。

**Program Files (x86) \Windows kit**は、インストールした Windows SDK のすべてのバージョンの既定の場所です。

Xbox や Azure など、他のプラットフォームには、インストールを要する独自の SDK があります。 詳細については、DirectX デベロッパー センターおよび Azure デベロッパー センターを参照してください。

## <a name="development-tools"></a>開発ツール

Visual Studio には、ネイティブ コード用の強力なデバッガー、スタティック分析ツール、グラフィックス デバッグ ツール、フル装備のコード エディター、単体テストのサポート、その他多数のツールおよびユーティリティが含まれています。 詳細については、「 [Visual studio](/visualstudio/ide/get-started-developing-with-visual-studio)での開発の開始」と「 [visual studio での開発のC++概要](../overview/overview-of-cpp-development.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容
|Title|説明|
|-----------|-----------------|
|[チュートリアル: 標準 C++ プログラムの作成](walkthrough-creating-a-standard-cpp-program-cpp.md)| Windows コンソールアプリケーションを作成します。|
|[チュートリアル: Windows デスクトップ アプリケーション (C++) の作成](walkthrough-creating-windows-desktop-applications-cpp.md)|ネイティブ Windows デスクトップアプリケーションを作成します。|
|[Windows デスクトップ ウィザード](windows-desktop-wizard.md)|ウィザードを使用して、新しい Windows プロジェクトを作成します。|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|ATL ライブラリを使用して、でC++COM コンポーネントを作成します。|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|MFC を使用して、ダイアログとコントロールを含む大規模または小さい Windows アプリケーションを作成する|
|[ATL と MFC の共有クラス](../atl-mfc-shared/atl-mfc-shared-classes.md)|ATL や MFC で共有されている CString などのクラスを使用します。|
|[データ アクセス](../data/data-access-in-cpp.md)| OLE DB と ODBC|
|[テキストと文字列](../text/text-and-strings-in-visual-cpp.md)|Windows でのさまざまな文字列型。|
|[DirectX を使用するゲームを作成するためのリソース](resources-for-creating-a-game-using-directx.md)
|[方法: Windows デスクトップ アプリケーションでの Windows 10 SDK の使用](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[リソース ファイルの操作](working-with-resource-files.md)|画像、アイコン、文字列テーブル、およびその他のリソースをデスクトップアプリケーションに追加する方法。|
|[DirectX を使用してゲームを作成C++するためのリソース ()](resources-for-creating-a-game-using-directx.md)|でC++ゲームを作成するためのコンテンツへのリンク。|
|[方法: Windows デスクトップ アプリケーションでの Windows 10 SDK の使用](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows 10 SDK を使用してビルドするプロジェクトの設定手順が示されています。|
|[ネイティブ デスクトップ アプリケーションの配置](deploying-native-desktop-applications-visual-cpp.md)|Windows でネイティブアプリケーションを展開します。|

## <a name="related-articles"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md)|ビジュアルC++開発者向けコンテンツの親トピックです。|
[C++/CLI による .NET の開発](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|.NET アプリケーションおよびコンポーネントC++との通信を可能にするネイティブライブラリのラッパーを作成します。|
|[.NET および UWP でのコンポーネント拡張](../extensions/component-extensions-for-runtime-platforms.md)|/Cx とC++/cli によってC++共有される構文要素のリファレンス|
|[ユニバーサル Windows アプリ (C++)](../cppcx/universal-windows-apps-cpp.md)|/Cx または Windows ランタイムC++テンプレートライブラリ (wrl) を使用して UWP アプリケーションを作成します。|
|[COM および .NET の C++ の属性](attributes/cpp-attributes-com-net.md)|.NET または COM を使用した Windows のみのプログラミングの非標準属性。|
