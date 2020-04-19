---
title: '方法: -Clr に移行します。'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 9abc85227d6091005d7e097d3305150f4ca347a1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448092"
---
# <a name="how-to-migrate-to-clr"></a>方法: /Clr:pure に移行します。

このトピックでは、ネイティブ コードをコンパイルするときに発生する問題を説明 **/clr** (を参照してください[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)詳細については)。 **/clr**ネイティブの C++ コードを呼び出し、その他のネイティブ C++ コードだけでなく、.NET アセンブリから呼び出すことができます。 参照してください[混在 (ネイティブおよびマネージ) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)と[ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)を使用してコンパイルの利点の詳細についての **/clr**します。

## <a name="known-issues-compiling-library-projects-with-clr"></a>/clr でライブラリ プロジェクトをコンパイルする場合の既知の問題

Visual Studio がライブラリ プロジェクトをコンパイルするときに、既知の問題を含む **/clr**:

- コードが実行時に型を照会できます[で](../mfc/reference/cruntimeclass-structure.md#fromname)します。 ただし、MSIL .dll 内の型がある場合 (でコンパイルされた **/clr**)、呼び出し`FromName`(は表示されませんこの問題コードがある後に FromName 呼び出しが発生した場合、マネージ .dll で静的コンス トラクターが実行前に発生した場合に失敗する可能性があります実行されるマネージ .dll で)。 この問題を回避するには、マネージド静的コンストラクターを強制的に構築します。それには、マネージド .dll で関数を定義してエクスポートし、その関数をネイティブ MFC アプリケーションから呼び出します。 例:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Visual C++ でのコンパイル

使用する前に **/clr**プロジェクト内の任意のモジュールで最初にコンパイルし、ネイティブ プロジェクトを Visual Studio 2010 をリンクします。

最も簡単なパスを指定する順番では、その後に、次の手順を **/clr**コンパイルします。 これらの手順では、手順ごとにプロジェクトをコンパイルして実行することが重要です。

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 より前のバージョン

強化されたに関連するコンパイラ エラーが発生する可能性があります Visual Studio 2003 より前のバージョンから Visual Studio 2010 にアップグレードする場合C++Visual Studio 2003 で標準の準拠

### <a name="upgrading-from-visual-studio-2003"></a>Visual Studio 2003 からアップグレードします。

せず以前に Visual Studio 2003 で作成されたプロジェクトをコンパイルするときも、まず **/clr** ANSI/ISO 準拠といくつかの重大な変更に、Visual Studio が今すぐ増加はします。 最も注意が必要な可能性のある変更は[CRT のセキュリティ機能](../c-runtime-library/security-features-in-the-crt.md)します。 CRT を使用するコードでは、廃止警告が生成される可能性があります。 これらの警告は、抑制しますですが、新しい移行[セキュリティが強化されたバージョンの CRT 関数](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)はより強力なセキュリティを提供し、コードのセキュリティの問題を表示することがあります。

### <a name="upgrading-from-managed-extensions-for-c"></a>C++ マネージド拡張からのアップグレード

Visual Studio 2005 以降で c++ マネージ拡張で記述されたコードはコンパイルされません **/clr**します。

## <a name="convert-c-code-to-c"></a>C コードから C++ への変換

Visual Studio は C ファイルをコンパイルする必要がありますの C++ への乗り換え、 **/clr**コンパイルします。 実際のファイル名を変更する必要はありません。使用することができます **/Tp** (を参照してください[/Tc、/Tp、/TC、/TP (ソース ファイル タイプの指定)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md))。C++ ソース コード ファイルが必要な **/clr**、オブジェクト指向パラダイムを使用するコードをリファクタリングする必要はありません。

C コードは、C++ ファイルとしてコンパイルするときは変更を必要とする可能性があります。 C++ の型保証の規則は厳密なので、型の変換はキャストで明示的に行う必要があります。 たとえば、malloc は void ポインターを返しますが、キャストによる C では任意の型のポインターに割り当てることができます。

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

また C++ では関数ポインターの型も厳密に保証されているので、次のような C コードは変更が必要です。 C++ では、関数ポインターの型を定義する `typedef` を作成し、その後その型を使用して関数ポインターをキャストすることをお勧めします。

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

また C++ では、関数を参照したり呼び出すには、その前にプロトタイプを作成するか完全に定義する必要があります。

C++ のキーワードとなって発生する C コードで使用される識別子 (など**仮想**、**新しい**、**削除**、 **bool**、**は true。**、 **false**など) 名前を変更する必要があります。 これは一般的に、単純な検索置換操作だけで行うことができます。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>プロジェクト設定の再構成

プロジェクトをコンパイルして Visual Studio 2010 での実行後は、用に新しいプロジェクト構成を作成する必要があります **/clr**既定の構成を変更するのではなく。 **/clr**一部のコンパイラ オプションと互換性がないと、ネイティブまたはマネージとしてプロジェクトをビルドする別の構成を作成することができます。 ときに **/clr**プロパティ ページ ダイアログ ボックスと互換性のないプロジェクトの設定が選択されている **/clr**は無効になります (場合、無効なオプションが自動的に復元されないと **/clr**は後で選択されていません)。

### <a name="create-new-project-configurations"></a>新しいプロジェクト構成の作成

使用することができます**設定のコピー元**オプション、**新しいプロジェクト構成 ダイアログ ボックス**(**ビルド** > **のConfigurationManager** > **アクティブ ソリューション構成** > **新規**)、既存のプロジェクト設定に基づくプロジェクト構成を作成します。 これを、デバッグ構成に対して 1 回、リリース構成に対して 1 回実行してください。 それ以降の変更を適用できます、 **/clr** -特定の構成のみ、元のプロジェクト設定はそのままです。

カスタム ビルド規則を使用するプロジェクトには、特別な注意が必要な場合があります。

この手順は、メイクファイルを使用するプロジェクトにとって別の意味があります。 この場合、別のビルド ターゲットを構成するに固有のバージョンで **/clr**コンパイルは、元のコピーから作成できます。

### <a name="change-project-settings"></a>プロジェクトの設定の変更

**/clr**開発環境で次の手順で選択できる[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。 既に説明したように、この手順によって競合するプロジェクト設定は自動的に無効になります。

> [!NOTE]
>  マネージ ライブラリまたは web サービス プロジェクトを Visual Studio 2003 からアップグレードする場合、 **/Zl**に追加されたコンパイラ オプションは、**コマンドライン**プロパティ ページ。 これによって LNK2001 が発生します。 削除 **/Zl**から、**コマンドライン**解決するのには、プロパティ ページ。 参照してください[/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md)と[コンパイラを設定し、ビルド プロパティ](../build/working-with-project-properties.md)詳細についてはします。 または、msvcrt.lib および msvcmrt.lib をリンカーに追加**追加の依存関係**プロパティ。

メイクファイルでビルドされたプロジェクトでは、互換性のないコンパイラ オプションを後に手動で無効する必要があります **/clr**が追加されます。 参照してください/[/clr の制約](../build/reference/clr-restrictions.md)と互換性のないコンパイラ オプションについて **/clr**します。

### <a name="precompiled-headers"></a>プリコンパイル済みヘッダー

プリコンパイル済みヘッダーがサポートされている **/clr**します。 ただし、コンパイルするかどうかのみ、CPP ファイルの一部 **/clr** (残りをネイティブ コンパイル) いくつかの変更が必要になりますので、プリコンパイル済みヘッダーを使用して生成された **/clr**ものと互換性がありませんなしで生成 **/clr**します。 この非互換性が原因という事実に **/clr**を生成し、メタデータが必要です。 コンパイルされたモジュール **/clr**しないメタデータが含まれていないプリコンパイル済みヘッダーを使用できますしたがってと非 **/clr**モジュールは、メタデータを含むプリコンパイル済みヘッダー ファイルを使用できません。

一部のモジュールがコンパイルされる場所にプロジェクトをコンパイルする最も簡単な方法は、 **/clr**プリコンパイル済みヘッダーを完全に無効にします。 (プロジェクトの [プロパティ ページ] ダイアログで C/C++ ノードを開き、[プリコンパイル済みヘッダー] を選択します。 次に、[プリコンパイル済みヘッダーの作成/使用] プロパティを 「プリコンパイル済みヘッダーを使用しない」 に変更します)。

しかし、特に大きなプロジェクトの場合、プリコンパイル済みヘッダーを使用するとコンパイルの処理速度がかなり短縮されるので、この機能を無効化することはお勧めしません。 この場合に設定してください、 **/clr**と非 **/clr**別のプリコンパイル済みヘッダーを使用するファイル。 これによって 1 つの手順で実行できます複数選択することをコンパイルするのには、モジュール **/clr**を使用して**ソリューション エクスプ ローラー**グループを右クリックし、プロパティを選択します。 次に、[ファイルを使用して PCH を作成/使用] プロパティと [プリコンパイル済みヘッダー ファイル] プロパティの両方を変更し、それぞれ異なるヘッダー ファイル名と PCH ファイルを使用するように設定します。

## <a name="fixing-errors"></a>エラーの修正

使用してコンパイル **/clr**コンパイラ、リンカー、またはランタイム エラーが発生する可能性があります。 このセクションでは、最も一般的な問題について説明します。

### <a name="metadata-merge"></a>メタデータのマージ

データ型のバージョンが異なる場合、2 つの型に対して生成されるメタデータが一致しないため、リンカーのエラーが発生することがあります (通常、型のメンバーが条件付きで定義されているのに、その型を使用するすべての CPP ファイルの条件が同じでない場合に発生します)。このような場合、リンカーのエラーが発生し、シンボル名と、型が定義されている 2 番目の OBJ ファイルの名前だけが報告されます。 多くの場合、OBJ ファイルがリンカーに送られる順序を変更し、他のデータ型バージョンの位置がリンカーにわかるようにすると対処できます。

### <a name="loader-lock-deadlock"></a>ローダー ロックのデッドロック

「ローダー ロックのデッドロック」が発生する可能性しますが、決定的しが検出され、実行時に報告されます。 参照してください[混在アセンブリの初期化](../dotnet/initialization-of-mixed-assemblies.md)に関する背景、ガイダンス、およびソリューションの。

### <a name="data-exports"></a>データのエクスポート

DLL データのエクスポートはエラーの原因にもなりやすいため、お勧めしません。 これは、DLL のデータ セクションは、DLL のマネージド部分の一部が実行されるまで初期化されていると保証されないためです。 参照メタデータを[#using ディレクティブ](../preprocessor/hash-using-directive-cpp.md)します。

### <a name="type-visibility"></a>型の可視性

ネイティブ型は、既定ではプライベートです。 これで、ネイティブ型は DLL の外側では見えなくなります。 このエラーを解決するには、これらの型に `public` を追加します。

### <a name="floating-point-and-alignment-issues"></a>浮動小数点とアラインメントの問題

`__controlfp` 共通言語ランタイムでサポートされていません (を参照してください[_control87、_controlfp、 \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)詳細については)。 CLR は反映されませんも[align](../cpp/align-cpp.md)します。

### <a name="com-initialization"></a>COM の初期化

共通言語ランタイムは、モジュールが初期化されると自動的に COM を初期化します (自動的に初期化される場合、COM は MTA として初期化されます)。 その結果、明示的に COM を初期化すると、COM が既に初期化されていることを示すリターン コードが生成されます。 COM が CLR によって既にいずれかのスレッド モデルに初期化されている場合、別のスレッド モデルを使用して明示的に COM を初期化しようとすると、アプリケーションが失敗するおそれがあります。

共通言語ランタイムは、既定では MTA として COM を開始します。使用して、 [/CLRTHREADATTRIBUTE (CLR スレッド属性の設定)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)これを変更します。

### <a name="performance-issues"></a>パフォーマンスの問題

MSIL に対して生成されたネイティブの C++ メソッドが (仮想関数呼び出し、または関数ポインターの使用によって) 間接的に呼び出されると、パフォーマンスが低下することがあります。 これに関する詳細についてを参照してください。[ダブル サンキング](../dotnet/double-thunking-cpp.md)します。

ネイティブから MSIL に移動すると、ワーキング セットのサイズが増加することがわかります。 これは、共通言語ランタイムが、プログラムを正しく実行するための多くの機能を提供するためです。 場合、 **/clr**アプリケーションが正しく実行されていない、C4793 を有効にすることがあります (既定でオフ) を参照してください[コンパイラの警告 (レベル 1 および 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)詳細についてはします。

### <a name="program-crashes-on-shutdown"></a>シャットダウン時のプログラムの衝突

場合によっては、マネージド コードが実行を終了する前に CLR がシャットダウンすることがあります。 `std::set_terminate` と `SIGTERM` を使用すると、この問題が発生します。 参照してください[signal 定数](../c-runtime-library/signal-constants.md)と[set_terminate](../c-runtime-library/abnormal-termination.md)詳細についてはします。

## <a name="using-new-visual-c-features"></a>Visual C++ の新機能の使用

アプリケーションのコンパイル、リンク、および実行をした後でコンパイルされたモジュールで .NET 機能の使用を開始できます **/clr**します。 詳細については、「[Component Extensions for Runtime Platforms](../extensions/component-extensions-for-runtime-platforms.md)」を参照してください。

C++ のマネージド拡張を使用していた場合は、新しい構文を使用してコードを変換できます。 C++ マネージ拡張を変換する方法の詳細については、次を参照してください。 [C +/cli 移行ガイド](../dotnet/cpp-cli-migration-primer.md)します。

Visual C++ での .NET プログラミングの詳細については、以下の項目を参照してください。

- [C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)

- [ランタイム プラットフォームのコンポーネントの拡張機能](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>関連項目

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
