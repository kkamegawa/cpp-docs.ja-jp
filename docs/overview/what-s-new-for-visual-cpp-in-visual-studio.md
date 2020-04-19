---
title: Visual Studio での C++ の新機能
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: df7cf44831781086f1b36d32ea9ed773a5dff9a4
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415721"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Visual Studio での C++ の新機能

::: moniker range=">=vs-2019"

Visual Studio 2019 には、Microsoft C++ 環境に対する多くの更新プログラムと修正プログラムが導入されています。 コンパイラおよびツールの多くのバグと問題を修正しました。 多くの問題は、 **[フィードバックの送信]** の [[問題の報告]](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) および [[提案の送信]](https://developercommunity.visualstudio.com/spaces/62/index.html) オプションを通じてお客様から寄せられたものです。 バグ レポートをお寄せいただきありがとうございました。 Visual Studio 全体の新機能の詳細については、「[Visual Studio 2019 の新機能](/visualstudio/ide/whats-new-visual-studio-2019)」を参照してください。 Visual Studio 2017 での C++ の新機能については、「[Visual Studio 2017 での C++ の新機能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017)」を参照してください。 Visual Studio 2015 以前のバージョンでの C++ の新機能については、「[Visual Studio 2003 から 2015 の Visual C++ の新機能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)」を参照してください。

## <a name="c-compiler"></a>C++ コンパイラ

- C++17 機能と正確性の修正に関するサポート強化に加え、モジュールやコルーチンなど、C++20 機能の実験的サポート。 詳しくは、「[C++ Conformance Improvements in Visual Studio 2019](cpp-conformance-improvements.md)」(Visual Studio 2019 での C++ 準拠の強化) をご覧ください。

- `/std:c++latest` オプションには現在、3 方向比較のための C++20 演算子 \<=> ("宇宙船") の初期サポートなど、必ずしも完全ではない C++20 機能が含まれています。

- C++ コンパイラ スイッチ `/Gm` は現在、非推奨になっています。 ご自分のビルド スクリプト内の `/Gm` スイッチが明示的に定義されている場合は、それを無効にすることを検討してください。 ただし、"警告をエラーとして扱う" (`/WX`) を使用しているとき、`/Gm` の非推奨化に関する警告はエラーとして扱われないので無視してもかまいません。

- MSVC により、`/std:c++latest` フラグの下で C++20 標準ドラフトの機能の実装が開始されたため、`/std:c++latest` と `/clr` (すべてのフレーバー)、`/ZW`、`/Gm` との互換性がなくなりました。 Visual Studio 2019 では、`/clr`、`/ZW`、または `/Gm` を使ってコンパイルする場合は `/std:c++17` または `/std:c++14` モードを使ってください (ただし、前の項目を確認してください)。

- C++ コンソール アプリとデスクトップ アプリに対して、プリコンパイル済みヘッダーが既定では生成されなくなりました。

### <a name="codegen-security-diagnostics-and-versioning"></a>コード生成、セキュリティ、診断、バージョン管理

Spectre Variant 1 のリスク軽減サポートを提供するため、`/Qspectre` を使用した分析が強化されました (CVE-2017-5753)。 詳細については、「[Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/)」 (MSVC の Spectre 軽減策) を参照してください。

## <a name="c-standard-library-improvements"></a>C++ 標準ライブラリの機能強化

- 追加の C++17 と C++20 のライブラリ機能と正確性の修正の実装。 詳しくは、「[C++ Conformance Improvements in Visual Studio 2019](cpp-conformance-improvements.md)」(Visual Studio 2019 での C++ 準拠の強化) をご覧ください。

- Clang-Format が C++ 標準ライブラリのヘッダーに適用され、読みやすさが向上しました。

- Visual Studio で C++ の [マイ コードのみ] がサポートされるようになったため、同じ効果を実現するため標準ライブラリで `std::function` と `std::visit` のカスタム メカニズムを提供する必要がなくなりました。 そのメカニズムが削除されても、ユーザーが確認できる影響はほとんどありません。 ただし、コンパイラにより、\<type_traits> または \<variant> の行 15732480 または 16707566 上の問題を示す診断が生成されなくなります。

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>コンパイラと標準ライブラリでのパフォーマンス/スループットの向上

- リンカーによるファイル I/O の処理や PDB タイプのマージと作成のリンク時間など、ビルドのスループットが改善されました。

- OpenMP SIMD ベクター化の基本的なサポートが追加されました。 これは新しいコンパイラ スイッチ `-openmp:experimental` を使用して有効にできます。 このオプションにより、`#pragma omp simd` で注釈が付けられたループをベクター化できる可能性があります。 ベクター化は保証されておらず、注釈が付けられていてもベクター化されていないループに対しては警告が報告されます。 SIMD 句はサポートされていません。無視され、警告が報告されます。

- 新しいインライン展開コマンド ライン スイッチ `-Ob3` が追加されました。これは、`-Ob2` より積極的なバージョンです。 `-O2` (速さのためにバイナリを最適化) は引き続き、既定で `-Ob2` を意味します。 コンパイラのインライン展開が十分に積極的でない場合、`-O2 -Ob3` を渡すことを検討してください。

- 数値演算ライブラリ関数および整数除算などの他の特定の演算の呼び出しを含むループの手動ベクター化をサポートするため、Short Vector Math Library (SVML) 組み込み関数のサポートが追加されました。 これらの関数では、128 ビット、256 ビット、または 512 ビットの同等のベクターが計算されます。 サポートされている関数の定義については、[Intel 組み込みガイド](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML)をご覧ください。

- 新規および改良された最適化:

  - float と integer の両方の形式に対する、SIMD ベクター組み込み関数を使用する式の定数折りたたみと計算の簡略化。

  - 常に true または false になることがわかっている分岐を削除するために制御フロー (if/else/switch ステートメント) から情報を抽出するためのいっそう強力な分析。

  - SSE2 ベクター命令を使用するための memset アンローリングの向上。

  - 意味のない構造体/クラスのコピーの削除の向上、特に値渡しの C++ プログラムの場合。

  - `std::copy` または `std::vector` および `std::string` 構築など、`memmove` を利用したコードの最適化の改善。

- 標準ライブラリで直接インクルードされない部分のコンパイルを回避するよう、標準ライブラリの物理的設計を最適化しました。 この変更により、\<vector> しか含まれない空のファイルをビルドする時間が半分になります。 結果として、以前は間接的に含まれていたヘッダーの `#include` ディレクティブの追加が必要になることがあります。 たとえば、`std::out_of_range` を使うコードでは、`#include <stdexcept>` の追加が必要になることがあります。 ストリーム挿入演算子を使うコードでは、`#include <ostream>` の追加が必要になることがあります。 その利点は、実際に \<stdexcept> または \<ostream> コンポーネントを使う変換単位のみで、それらをコンパイルするスループットのコストがかかるようになることです。

- 標準ライブラリのさらに多くの場所で `if constexpr` が適用され、コピー操作、反転や回転のような順列、および並列アルゴリズムのライブラリにおいて、スループットが向上し、コードのサイズが削減されました。

- 標準ライブラリで内部的に `if constexpr` を使うようになり、C++14 モードであってもコンパイル時間が短縮されます。

- 並列アルゴリズムのライブラリの実行時の動的リンク検出で、関数ポインターの配列を格納するためにページ全体が使われなくなりました。 このメモリを読み取り専用にすることは、セキュリティのために重要だと見なされなくなりました。

- `std::thread` のコンストラクターでスレッドの開始が待機されなくなり、基になる C ライブラリ `_beginthreadex` と指定された呼び出し可能オブジェクトの間にそれほど多くの関数呼び出しのレイヤーが挿入されなくなりました。 以前の `std::thread` では、`_beginthreadex` と、指定された呼び出し可能オブジェクトの間に 6 個の関数が置かれていましたが、3 個だけに減りました (うち 2 個は単なる `std::invoke` です)。 また、この変更により、`std::thread` の作成とちょうど同じ時間にシステム クロックが変更された場合に `std::thread` のコンストラクターがハングするという、あいまいなタイミングのバグも解決されます。

- `std::hash<std::filesystem::path>` を実装する際に導入された `std::hash` のパフォーマンス低下を修正しました。

- 標準ライブラリのいくつかの場所で、正確性を実現するために catch ブロックの代わりにデストラクターが使われるようになりました。 この結果、デバッガーの操作性が向上します。標準ライブラリの影響を受けた場所を通じてスローした例外は、再スローではなく、その元のスロー サイトからスローされたものとして表示されるようになります。 標準ライブラリのすべての catch ブロックが削除されたわけではありません。MSVC の今後のリリースでは、catch ブロックの数を減らす予定です。

- noexcept 関数内の条件付きスローが原因となる `std::bitset` の準最適な codegen が、スローのパスを取り除くことで修正されました。

- `std::list` および `std::unordered_*` ファミリで、より多くの場所で内部的に非デバッグの反復子が使われます。

- `std::list` のいくつかのメンバーが変更され、リスト ノードを開放して再割り当てする代わりに、可能であればそれらを再利用するようになりました。 たとえば、既にサイズ 3 を持っている `list<int>` があるとします。`assign(4, 1729)` を呼び出すと、最初の 3 つのリスト ノードの整数値を上書きし、値 1729 と共に 1 つの新しいリスト ノードを割り当てるようになります。

- 標準ライブラリのすべての `erase(begin(), end())` 呼び出しが `clear()` に変更されました。

- `std::vector` で、特定のケースでより効率的に要素を初期化および消去できるようになりました。

- `std::variant` が改善され、最適化がより簡単になりました。結果的に、より良いコードが生成されます。 `std::visit` を利用することで、コードのインライン展開が改善されます。

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Live Share C++ サポート

[Live Share](/visualstudio/liveshare/) は C++ 対応になりました。Visual Studio または Visual Studio Code を使用する開発者はリアルタイムで共同作業できます。 詳細については、「[Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)」 (C++ 向け Live Share のお知らせ: リアルタイムの共有と共同作業) を参照してください

### <a name="intellicode-for-c"></a>C++ 向けの IntelliCode

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

IntelliCode はオプションの拡張機能であり、独自の広範囲なトレーニングとコード コンテキストを使用し、入力候補一覧の上部に使用頻度が高いものを配置します。 多くの場合、一覧を見るとき下にスクロールする必要がなくなります。 C++ の場合、標準ライブラリのような一般的なライブラリを使用しているときには、IntelliCode からほとんどのヘルプが提供されます。 インストーラーでワークロード コンポーネントとして使用できます。 詳細については、「[AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/)」 (AI によるコード入力支援機能が IntelliCode 経由で C++ でも利用可能に) を参照してください。

### <a name="template-intellisense"></a>テンプレート IntelliSense

**テンプレート バー**で、モーダル ウィンドウではなく**ピーク ウィンドウ** UI が使用され、入れ子になったテンプレートがサポートされ、**ピーク ウィンドウ**に既定の引数が設定されるようになりました。 詳細については、「[Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/)」 (Visual Studio 2019 プレビュー 2 のテンプレート IntelliSense 改善) を参照してください。 **テンプレート バー**の **[直前に使用]** ドロップダウンでは、前に使用したサンプル引数のセットを簡単に切り替えることができます。

### <a name="new-start-window-experience"></a>新しいスタート画面のエクスペリエンス

IDE を起動すると、新しい [開始] ウィンドウが開き、最近使用したプロジェクトを開くオプション、ソース管理からコードを複製するオプション、ソリューションまたはフォルダーとしてローカル コードを開くオプション、新しいプロジェクトを作成するオプションが表示されます。 [新しいプロジェクト] ダイアログも改善され、検索第一でフィルタリング可能になりました。

### <a name="new-names-for-some-project-templates"></a>一部のプロジェクト テンプレートの新しい名前

更新した [新しいプロジェクト] ダイアログ ボックスに合わせて、プロジェクト テンプレートの名前と説明をいくつか変更しました。

### <a name="various-productivity-improvements"></a>さまざまな生産性の向上

Visual Studio 2019 では、コードをもっと簡単に、もっと直観的に記述できるように次の機能が追加されました。

- クイック修正:
  - 不足している #include の追加
  - NULL を nullptr に
  - 不足しているセミコロンの追加
  - 不足している名前空間または範囲の解決
  - 無効な間接参照オペランドを置換 (\* を & に、& を \* に)
- 右括弧にカーソルを置くと、ブロックのクイック インフォが表示
- ヘッダー/コード ファイルの表示
- #include の [定義へ移動] でファイルが開く

詳細については、「[C++ Productivity Improvements in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/)」 (Visual Studio 2019 プレビュー 2 の C++ 生産性向上) を参照してください。

### <a name="quickinfo-improvements"></a>QuickInfo の機能強化

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

クイック ツールヒントで、エディターのセマンティクスの色づけが考慮されるようになりました。 また、 **[オンラインで検索]** リンクも新しくなりました。カーソルを置いたコード コンストラクターについて詳しく学習するためのオンライン ドキュメントを検索できます。 赤い波線が引かれているコードについては、クイック ヒントで提供されるリンクによってオンラインでエラーを検索します。 この方法では、自分のブラウザーにメッセージを再入力する必要はありません。 詳細については、「[Quick Info Improvements in Visual Studio 2019:Colorization and Search Online (Visual Studio 2019 のクイック ヒントの機能強化: 色づけとオンライン検索)](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/)」をご覧ください。

### <a name="intellicode-available-in-c-workload"></a>C++ ワークロードで使用できる IntelliCode

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

IntelliCode がオプションのコンポーネントとして**C++ によるデスクトップ開発**ワークロードに付属するようになりました。 詳細については、[Visual Studio 2019 に付属する強化された C++ IntelliCode](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/) に関するページをご覧ください。

## <a name="cmake-support"></a>CMake サポート

- CMake 3.14 のサポート

- Visual Studio では、CMakeGUI などの外部ツール、カスタマイズされたメタビルド システム、cmake.exe をそれ自体で呼び出すビルド スクリプトによって生成された既存の CMake キャッシュを開けるようになりました。

- 強化された IntelliSense パフォーマンス。

- 新しい設定エディターでは、CMakeSettings.json ファイルの手動編集の代わりになるもの、CMakeGUI と同等の機能が提供されます。

- Visual Studio では、Linux コンピューター上に互換性のある CMake のバージョンがあるかどうかが検出されることにより、Linux で CMake による C++ の開発を始めやすくなりました。 ない場合は、インストールすることができます。

- CMakeSettings での互換性のない設定 (アーキテクチャの不一致や、互換性のない CMake ジェネレーターの設定など) に対しては、JSON エディターおよびエラー一覧のエラーで波線が表示されます。

- `vcpkg integrate install` を実行した後は、vcpkg ツール チェーンが自動的に検出され、IDE で開かれる CMake プロジェクトに対して有効になります。 この動作は、CMakeSettings で空のツールチェーン ファイルを指定することによりオフにできます。

- CMake プロジェクトでは、"マイ コードのみ" デバッグが既定で有効になるようになりました。

- CMake プロジェクトのスタティック分析の警告をバックグラウンドで処理し、エディターに表示できるようになりました。

- CMake プロジェクトのビルドと構成の "開始" および "終了" に関するいっそう明確なメッセージと、Visual Studio のビルドの進行状況 UI のサポート。 さらに、出力ウィンドウに表示される CMake のビルドおよび構成に関するメッセージの詳細レベルをカスタマイズできる CMake の詳細さの設定が、 **[ツール] の [オプション]** に追加されました。

- CMake のコマンド ラインを手動で変更することなくツールチェーンを指定するための `cmakeToolchain` の設定が、CMakeSettings.json でサポートされるようになりました。

- 新しい **[すべてビルド]** メニューのショートカット **Ctrl+Shift+B**。

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

- Clang/LLVM を使った CMake プロジェクトの編集、ビルド、デバッグの統合サポート。 詳細については、「[Clang/LLVM Support in Visual Studio (Visual Studio での Clang/LLVM のサポート)](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/)」をご覧ください。

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux と Windows Subsystem for Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

- Linux および CMake クロスプラットフォーム プロジェクトでの [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) のサポート。 詳細については、「[AddressSanitizer (ASan) for the Linux Workload in Visual Studio 2019 (Visual Studio 2019 の Linux ワークロード用の AddressSanitizer (ASan))](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/)」をご覧ください。

- Windows Subsystem for Linux (WSL) で C++ を使うための統合された Visual Studio サポート。 詳細については、「[C++ with Visual Studio 2019 and Windows Subsystem for Linux (WSL) (Visual Studio 2019 と Windows Subsystem for Linux (WSL) を使った C++)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)」をご覧ください。

## <a name="incredibuild-integration"></a>IncrediBuild の統合

IncrediBuild がオプションのコンポーネントとして**C++ によるデスクトップ開発**ワークロードに含まれるようになりました。 IncrediBuild のビルド モニターは、Visual Studio IDE に完全に統合されています。 詳細については、「[Visualize your build with IncrediBuild’s Build Monitor and Visual Studio 2019 (IncrediBuild のビルド モニターと Visual Studio 2019 を使ってビルドを視覚化する)](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/)」をご覧ください。

## <a name="debugging"></a>デバッグ

- Windows 上で実行される C++ アプリケーションの場合、PDB ファイルは別個の 64 ビット プロセスで読み込まれるようになりました。 この変更では、モジュールと PDB ファイルが多数含まれているアプリケーションをデバッグするときにメモリ不足が原因で発生するさまざまなクラッシュに対処しています。

- **[ウォッチ]** 、 **[自動]** 、 **[ローカル]** ウィンドウで検索が有効になります。

## <a name="windows-desktop-development-with-c"></a>C++ による Windows デスクトップ開発

- 次の C++ ATL/MFC ウィザードは使用できなくなりました。

  - ATL COM+ 1.0 コンポーネント ウィザード
  - ATL Active Server Page コンポーネント ウィザード
  - ATL OLE DB プロバイダー ウィザード
  - ATL プロパティ ページ ウィザード
  - ATL OLE DB コンシューマー ウィザード
  - MFC ODBC コンシューマー
  - ActiveX コントロールの MFC クラス
  - TypeLib からの MFC クラス。

  これらのテクノロジのサンプル コードは、Microsoft Docs および VCSamples GitHub リポジトリにアーカイブされています。

- Visual Studio インストーラーでは Windows 8.1 SDK を使用できなくなりました。 最新の Windows 10 SDK に C++ プロジェクトをアップグレードすることをお勧めします。 8\.1 に対するハードな依存関係がある場合は、Windows SDK アーカイブからダウンロードできます。

- 最新の C++ ツールセットでは、Windows XP を対象にできなくなります。 VS 2017 レベルの MSVC コンパイラとライブラリによる VS の対象指定はまだサポートされており、[個別のコンポーネント] を使用してインストールできます。

- ドキュメントでは、Visual C++ ランタイムの配置に対してマージ モジュールを使用しないよう強く推奨されています。 このリリースでは、MSM を非推奨にするための追加手順が行われています。 VCRuntime の集中配置を MSM から再頒布可能パッケージに移行することを検討してください。

## <a name="mobile-development-with-c-android-and-ios"></a>C++ によるモバイル開発 (Android および iOS)

C++ Android エクスペリエンスは、既定では Android SDK 25 および Android NDK 16b となりました。

## <a name="clangc2-platform-toolset"></a>Clang/C2 プラットフォーム ツールセット

実験段階の Clang/C2 コンポーネントが削除されました。 `/permissive-` および `/std:c++17` に完全に準拠した C++ 用の MSVC ツールセットを使用するか、Windows 用の Clang/LLVM ツールチェーンを使用します。

## <a name="code-analysis"></a>コード分析

- コード分析がバックグラウンドで自動的に実行されるようになりました。 エディターでの入力時に緑色の波線で警告が表示されます。 詳細については、「[In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/)」 (Visual Studio 2019 プレビュー 2 のエディター内コード分析) を参照してください。

- \<mutex> ヘッダーのよく知られている Standard Library タイプのための新しい試験段階 ConcurrencyCheck 規則。 詳細については、「[Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/)」 (Visual Studio 2019 のコンカレンシー コード分析) を参照してください。

- [Lifetime プロファイル チェッカー](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/)の更新された部分的な実装。これは未解決のポインターと参照を検出します。 詳細については、「[Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/)」 (Visual Studio 2019 プレビュー 2 の Lifetime プロファイル更新) を参照してください。

- C26138、C26810、C26811、試験段階規則 C26800 など、コルーチン関連のチェックを増やしました。 詳細については、「[New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/)」 (Visual Studio 2019 の新しいコード分析チェック: use-after-move とコルーチン) を参照してください。

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 バージョン 16.1

- 初期化されていない変数のチェックに対する新しいクイック修正。 詳細については、「[New code analysis quick fixes for uninitialized memory (C6001) and use before init (C26494) warnings (初期化されていないメモリ (C6001) と初期化前の使用 (C26494) 警告に関するコード分析の新しいクイック修正)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/)」をご覧ください。

## <a name="unit-testing"></a>単体テスト

マネージド C++ テスト プロジェクト テンプレートは使用できなくなります。 既存のプロジェクトでは、マネージド C++ テスト フレームワークを引き続き使用できます。 新しい単体テストでは、Visual Studio でテンプレートが提供されているネイティブ テスト フレームワークのいずれか (MSTest、Google Test) またはマネージド C# テスト プロジェクト テンプレートの使用を検討してください。

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 には、C++ 環境に対する多くの更新プログラムと修正プログラムが導入されています。 コンパイラおよびツールの、250 以上のバグおよびレポートされた問題を修正してきました。その多くは、 **[フィードバックの送信]** の [[問題の報告] オプションおよび [提案の送信]](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) オプションを通じてお客様から寄せられたものです。 バグ レポートをお寄せいただきありがとうございました。 Visual Studio 全体の新機能の詳細については、「[Visual Studio 2017 の新機能](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017)」を参照してください。 Visual Studio 2019 での C++ の新機能については、「[Visual Studio での C++ の新機能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019)」を参照してください。 Visual Studio 2015 以前のバージョンでの C++ の新機能については、「[Visual Studio 2003 から 2015 の Visual C++ の新機能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)」を参照してください。

## <a name="c-compiler"></a>C++ コンパイラ

### <a name="c-conformance-improvements"></a>C++ 準拠の強化

このリリースでは、C++ コンパイラと標準ライブラリを更新して C++11 と C++14 機能のサポートを強化し、C++17 標準に組み込まれると予想される特定の機能について予備的なサポートを追加しました。 詳しくは、「[C++ Conformance Improvements in Visual Studio 2017](cpp-conformance-improvements.md)」(Visual Studio 2017 での C++ 準拠の強化) をご覧ください。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

コンパイラは C++17 の新機能の約 75% をサポートしています。その中には構造化バインド、`constexpr` ラムダ、`if constexpr`、インライン変数、フォールド式、型システムへの `noexcept` の追加が含まれます。 これらの機能は、 **/std:c++17** オプションの下にあります。 詳細については、[Visual Studio 2017 での C++ 準拠の強化](cpp-conformance-improvements.md)に関するページをご覧ください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

Visual Studio バージョン 15.7 の MSVC コンパイラ ツールセットが、C++ 標準に準拠となりました。 詳細については、「[Announcing: MSVC Conforms to the C++ Standard (発表: MSVC の C++ への準拠)](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/)」および [Microsoft C++ 言語の準拠](../visual-cpp-language-conformance.md)に関するページを参照してください。

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 バージョン 15.8

[/experimental:preprocessor](../build/reference/experimental-preprocessor.md) コンパイラ スイッチにより、適用可能なすべての C および C++ 標準に最終的に準拠する新しい実験的 MSVC プリプロセッサが有効になります。 詳細については、「[MSVC experimental preprocessor overview](../preprocessor/preprocessor-experimental-overview.md)」(MSVC の実験的なプリプロセッサの概要) を参照してください。

### <a name="new-compiler-options"></a>新しいコンパイラ オプション

- [/permissive -](../build/reference/permissive-standards-conformance.md): すべての厳密な標準準拠コンパイラ オプションを有効にして、ほとんどの Microsoft 固有コンパイラ拡張機能 (ただし、たとえば `__declspec(dllimport)` は除きます) を無効にします。 このオプションは、Visual Studio 2017 バージョン 15.5 では既定でオンになっています。  **/permissive-** 準拠モードは、2 フェーズの名前参照に対応しています。 詳細については、[Visual Studio での C++ 準拠の強化](cpp-conformance-improvements.md)に関するページをご覧ください。

- [/diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): 診断エラーまたは警告が検出された場所の、行番号、行番号と列、または行番号、列、コード行の下のカレットを表示できるようにします。

- [/debug:fastlink](../build/reference/debug-generate-debug-info.md): すべてのデバッグ情報を PDB ファイルにコピーしないことで、インクリメンタル リンク時間を最大で 30% 高速化します (Visual Studio 2015 と比較した場合)。 代わりに、PDB ファイルは実行可能ファイルの作成に使われたオブジェクトとライブラリ ファイルのデバッグ情報を参照します。 「[Faster C++ build cycle in VS "15" with /Debug:fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/)」 (VS "15" での /Debug:fastlink による C++ ビルド サイクルの高速化) および「[Recommendations to speed C++ builds in Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/)」(Visual Studio で C++ のビルドを高速化するための推奨事項) をご覧ください。

- Visual Studio 2017 では、[/sdl](../build/reference/sdl-enable-additional-security-checks.md) を [/await](../build/reference/await-enable-coroutine-support.md) と一緒に使うことができます。 コルーチンでの [/RTC](../build/reference/rtc-run-time-error-checks.md) の制限がなくなりました。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- [/std:c++14 および /std:c++latest](../build/reference/std-specify-language-standard-version.md): これらのコンパイラ オプションを使用すると、プロジェクトで ISO C++ プログラミング言語の特定のバージョンにオプトインできます。 ほとんどの新しいドラフト標準機能は、 **/std:c++latest** オプションによって保護されています。

- [/std:c++17](../build/reference/std-specify-language-standard-version.md) を使用すると、コンパイラによって実装された C++17 機能セットが有効になります。 このオプションによって、C++17 後の C++ 標準のワーキング ドラフトおよび不具合の更新のバージョンで変更または更新された機能に対するコンパイラと標準ライブラリのサポートが無効になります。 これらの機能を有効にするには、 **/std:c++latest** を使用します。

### <a name="codegen-security-diagnostics-and-versioning"></a>コード生成、セキュリティ、診断、バージョン管理

このリリースでは、最適化、コード生成、ツールセットのバージョン管理、診断に関して、いくつかの機能強化が行われています。 主な改良点は次のとおりです。

- ループのコード生成の向上: 定数整数の除算の自動ベクター化がサポートされるようになりました。また、memset パターンの識別機能が向上しています。
- コード セキュリティの向上: バッファー オーバーラン コンパイラ診断の出力が向上し、[/guard:cf](../build/reference/guard-enable-control-flow-guard.md) によりジャンプ テーブルを生成する switch ステートメントが保護されるようになりました。
- バージョン管理: 組み込みプリプロセッサ マクロ **\_MSC\_VER** の値が、Visual C++ ツールセットの更新のたびに単調に更新されるようになりました。 詳しくは、「[Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/)」(Visual C++ コンパイラのバージョン) をご覧ください。
- 新しいツールセット レイアウト: 開発用コンピューターでのコンパイラおよび関連するビルド ツールの場所とディレクトリ構造が新しくなりました。 新しいレイアウトでは、複数のバージョンのコンパイラのサイド バイ サイド インストールが可能です。 詳細については、「[Compiler Tools Layout in Visual Studio 2017 (Visual Studio 2017 でのコンパイラ ツール レイアウト)](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/)」をご覧ください。
- 改善された診断機能: 出力ウィンドウにエラーが発生した列が表示されるようになりました。 詳細については、「[C++ compiler diagnostics improvements in VS "15" Preview 5 (VS "15" Preview 5 での C++ コンパイラの診断の機能強化)](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/)」をご覧ください。
- コルーチンを使用する場合、試験的キーワード **yield** ( **/await** オプションによって使用可能) は削除されています。 代わりにコードを書き直し、`co_yield` を使用する必要があります。 詳しくは、「[`yield` keyword to become `co_yield` in VS 2017 (yield キーワードが VS 2017 では co_yield になる)](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/)」をご覧ください。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

コンパイラでの診断の機能をさらに強化。 詳細については、「[Diagnostic Improvements in Visual Studio 2017 15.3.0 (Visual Studio 2017 15.3.0 での診断機能の強化)](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/)」をご覧ください。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

Visual C++ ランタイムの性能が継続的に上がります。生成されたコードの質が良くなるためです。 コードを再コンパイルするだけで、アプリをさらに高速にできます。 コンパイラ最適化の一部はまったく新しい機能です。たとえば、条件付きスカラー ストアをベクター化する、`sin(x)` と `cos(x)` の呼び出しを組み合わせて新しい `sincos(x)` を作る、SSA オプティマイザーから冗長命令を除去するなどです。 その他のコンパイラ最適化は、既存の機能の改善になります。条件式のベクター化ヒューリスティック、ループ最適化の改善、float min/max codegen などです。 リンカーには新しくて速い **/OPT:ICF** が実装されました。結果的に、リンク時間が最大 9% スピードアップします。インクリメンタル リンクに他のパフォーマンス修正があります。 詳細については、「[/OPT (最適化)](../build/reference/opt-optimizations.md)」と「[/INCREMENTAL (インクリメンタル リンクを行う)](../build/reference/incremental-link-incrementally.md)」を参照してください。

Microsoft C++ コンパイラは Intel の AVX-512 に対応しています。これに含まれるベクトルの長さ命令は AVX-512 の新しい関数を 128 ビット長と 256 ビット長のレジスタに与えます。

[/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) オプションを利用すれば、全般的に C++17 モードを使用しながら、C++14 バージョンの `noexcept` に戻すことができます。 このオプションでソース コードを更新し、C++17 に準拠できます。すべての `throw()` コードを同時に書き直す必要がありません。 詳細については、「[動的例外指定の削除と noexcept](cpp-conformance-improvements.md#noexcept_removal)」を参照してください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

- 予測実行サイドチャネルからの攻撃を緩和する、新しいコンパイラ スイッチの [/Qspectre](../build/reference/qspectre.md)。 詳細については、「[Spectre mitigations in MSVC (MSVC の Spectre 軽減策)](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/)」を参照してください。
- Spectre 軽減策用の新しい診断警告。 詳細については、「[Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4 (Visual Studio 2017 バージョン 15.7 プレビュー 4 での Spectre 診断)](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/)」を参照してください。
- C++ 標準のサポートの正しい報告を有効にする、/Zc の新しい値の **/Zc:__cplusplus**。 たとえば、スイッチが設定され、コンパイラが /std:c++17 モードである場合、値は **201703L** に拡張されます。 詳細については、「[MSVC now correctly reports __cplusplus (__cplusplus の MSVC での正しい報告)](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/)」を参照してください。

## <a name="c-standard-library"></a>C++ 標準ライブラリ

### <a name="correctness-improvements"></a>正確性についての改善

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (バージョン 15.0)

- `basic_string``_ITERATOR_DEBUG_LEVEL != 0` の診断は若干改良されました。 文字列構造の IDL チェックが失敗すると、その失敗の原因となった特定の動作が報告されるようになりました。 たとえば、"string iterator not dereferencable (文字列反復子を逆参照できません)" の代わりに、"cannot dereference string iterator because it is out of range (e.g. an end iterator) (範囲外のため文字列反復子を逆参照できません (例: 終了反復子))" が報告されます。
- 以前はコードが永続的にブロックされていた `std::promise` の移動代入演算子が修正されました。
- `atomic<T*>` の `T*` への暗黙の変換でコンパイラのエラーが修正されました。
- `pointer_traits<Ptr>` で `Ptr::rebind<U>` が適切に検出されるようになりました。
- `const` の減算演算子に不足した `move_iterator` 修飾子が修正されました。
- `propagate_on_container_copy_assignment` および `propagate_on_container_move_assignment` を要求するステートフルなユーザー定義アロケーターのサイレントかつ不適切な codegen が修正されました。
- `atomic<T>` でオーバーロードされた `operator&()` が許容されるようになりました。
- 間違った `bind()` 呼び出しのコンパイラ診断が若干向上しています。

Visual Studio 2017 RTM での標準ライブラリの改善に関する完全な一覧については、C++ チーム ブログのエントリ「[Standard Library Fixes In VS 2017 RTM (Visual Studio 2017 RTM での標準ライブラリの修正)](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/)」をご覧ください。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- 標準ライブラリのコンテナーでは、`max_size()` を `size_type` の `max()` ではなく、`numeric_limits<difference_type>::max()` にクランプするようになりました。 この変更により、そのコンテナーからの反復子における `distance()` の結果が、`distance()` の戻り値の型で表現できるようになります。
- 特殊化 `auto_ptr<void>` が欠落する不具合を修正しました。
- 以前は、length 引数が整数型ではない場合、`for_each_n()`、`generate_n()`、および `search_n()` アルゴリズムはコンパイルに失敗していました。現在は、整数型ではない length 引数から反復子の `difference_type` への変換が試みられるようになりました。
- `normal_distribution<float>` では、double から float への縮小について、標準ライブラリ内で警告を出力しないようになりました。
- 最大サイズのオーバーフローをチェックするときに、`max_size()` ではなく `npos` を使っていた一部の `basic_string` 操作を修正しました。
- `condition_variable::wait_for(lock, relative_time, predicate)` では、疑似ウェイクが発生した場合、相対時間全体にわたって待機していました。 現在は、相対時間の単一間隔の間のみ待機します。
- 標準での必要性に応じて、`future::get()` は `future` を無効化するようになりました。
- `iterator_traits<void *>` は `void&` を形成しようとするため、ハード エラーとして使用されていましたが、これが明確に空の構造体となり、"is iterator" SFINAE 条件で `iterator_traits` が使用できるようになりました。
- Clang **-Wsystem-headers** によって報告される警告の一部を修正しました。
- Clang -**Wmicrosoft-exception-spec** によって報告された "宣言での例外指定が以前の宣言と一致しない" 問題も修正しました。
- Clang と C1XX によって報告された mem-initializer-list 順序付けの警告も修正しました。
- 順序なしのコンテナーは、コンテナー自体がスワップされるときにハッシュ関数や述語のスワップを行っていませんでした。 現在は行うようになりました。
- 多くのコンテナー スワップ操作は、マークされた `noexcept` となりました (標準ライブラリが non-`propagate_on_container_swap` non-equal-allocator の未定義の動作条件を検出したときに、例外をスローすることがないため)。
- 多くの `vector<bool>` 操作が、マークされた `noexcept` になりました。
- 標準ライブラリは、アロケーター `value_type` (C++17 モードで) の照合をオプトアウト エスケープ ハッチで強制するようになりました。
- `basic_string` への self-range-insert が文字列の内容をスクランブルする場合の条件の一部を修正しました。 (注: ベクターへの self-range-insert は、標準によって引き続き禁止されています。)
- `basic_string::shrink_to_fit()` は、アロケーターの `propagate_on_container_swap` によって影響を受けることがなくなりました。
- `std::decay` では、煩雑な関数の型 (cv-qualified や ref-qualified などの関数型) が処理されるようになりました。
- include ディレクティブを変更した結果、正しい大文字小文字の区別とスラッシュの使用が可能となり、移植性が向上させました。
- 警告 C4061 "列挙型 '*enumeration*' の switch 文内の列挙子 ’*enumerator*’ は、case ラベルによって明示的に扱われていません" を修正しました。 この警告は既定ではオフになっており、標準ライブラリの警告の全般的なポリシーに対する例外として修正されました。 (標準ライブラリは **/W4** クリーンですが、 **/Wall** クリーンにしようとはしません。 既定でオフである警告の多くは、非常にノイズが多く、日常的に使用するためのものではありません。)
- `std::list` のデバッグ チェックが強化されました。 リストの反復子は `operator->()` をチェックし、`list::unique()` では反復子を無効としてマークするようになりました。
- `tuple` 内の uses-allocator メタプログラミングを修正しました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- `std::partition` は標準で要求される N + 1 回ではなく、N 回述語を呼び出すようになりました。
- バージョン 15.3 で見られた、静的マジックを回避する試みがバージョン 15.5 で修正されました。
- `std::atomic<T>` では、既定で構造化可能になることが `T` に要求されなくなりました。
- 対数時間をとるヒープ アルゴリズムは、反復子デバッグが有効なとき、入力は実際、ヒープであるとする線形時間アサーションを行わなくなりました。
- `__declspec(allocator)` は今後、C1XX の場合のみ、この declspec を理解しない Clang からの警告を防ぐ目的で保護されます。
- `basic_string::npos` は今後、コンパイル時間定数として利用できます。
- C++17 モードの `std::allocator` は、アラインメントが `max_align_t` を超える、オーバーアラインされている型の割り当てを適切に処理するようになりました ( **/Zc:alignedNew-** によって無効にされていない限り)。  たとえば、SSE および AVX 命令で、アラインメントが 16 バイトまたは 32 バイトのオブジェクトのベクトルが正しく調整されるようになりました。

### <a name="conformance-improvements"></a>準拠の強化

- \<any\>、\<string_view\>、`apply()`、`make_from_tuple()` が追加されました。
- \<optional\>、\<variant\>、`shared_ptr::weak_type`、および \<cstdalign\> が追加されました。
- `min(initializer_list)`、`max(initializer_list)`、および `minmax(initializer_list)` で、さらに `min_element()`、`max_element()`、および `minmax_element()` で C++14 `constexpr` が有効になりました。

詳細については、「[Microsoft C++ 言語の準拠表](../visual-cpp-language-conformance.md)」を参照してください。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- C++17 の追加機能がいくつか実装されました。 詳細については、「[Microsoft C++ 言語の準拠表](cpp-conformance-improvements.md#improvements_153)」を参照してください。
- P0602R0 "variant と optional は自明的にコピー/移動を伝達する必要がある" を実装しました。
- 標準ライブラリでは、[/GR-](../build/reference/gr-enable-run-time-type-information.md) オプションで無効にされた動的 RTTI が正式に許容されるようになりました。 `dynamic_pointer_cast()` と `rethrow_if_nested()` には本質的に `dynamic_cast` が必要なため、標準ライブラリでは **/GR-** の指定時にこれらの関数が `=delete` としてマークされるようになりました。
- 動的 RTTI が **/GR-** で無効にされた場合でも、`typeid(SomeType)` の形式の "static RTTI" は引き続き使用可能で、標準ライブラリの一部のコンポーネントを強化します。 標準ライブラリでは、 **/D\_HAS\_STATIC\_RTTI=0** でこの機能の無効化もサポートされるようになりました。 このフラグでは、`std::any`、`std::function` の `target()` および `target_type()` メンバー関数、さらに `std::shared_ptr` および `std::weak_ptr` の `get_deleter()` フレンド メンバー関数も無効になることに注意してください。
- 標準ライブラリでは、条件付きで定義されたマクロではなく、無条件で C++14 `constexpr` を使用するようになりました。
- 標準ライブラリでは、エイリアス テンプレートを内部で使用するようになりました。
- 標準ライブラリでは、`nullptr_t{}` ではなく、`nullptr` を内部で使用するようになりました。 (NULL は内部で使用できなくなりました。 0 を null として内部で使用している箇所は、徐々に削除されています。)
- 標準ライブラリでは、様式上 `std::forward()` を誤用するのではなく、`std::move()` を内部で使用するようになりました。
- `static_assert(false, "message")` を `#error message` に変更しました。 この変更により、`#error` でコンパイルが即時中止されるため、コンパイラによる診断が向上します。
- 標準ライブラリでは、関数を `__declspec(dllimport)` としてマークしなくなりました。 最新のリンカー テクノロジでは、それが不要になりました。
- SFINAE を既定のテンプレート引数に抽出するため、戻り値型と関数引数型に比べて、煩雑さが軽減されました。
- \<random\> のデバッグ チェックでは、`fputs()` を **stderr** に呼び出す内部関数 `_Rng_abort()` ではなく、標準ライブラリの通常のメカニズムが使用されるようになりました。 この関数の実装は、バイナリ互換性のために保持されているものの、標準ライブラリの次のバイナリ非互換バージョンでは削除されています。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- 標準ライブラリの機能がいくつか、C++17 標準に合わせて追加、非推奨、削除されました。 詳細については、「[Visual Studio の C++ 準拠の強化](cpp-conformance-improvements.md#improvements_155)」をご覧ください。
- 次の並列アルゴリズムが試験的にサポートされます。
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- 次の並列アルゴリズムのシグネチャが追加されていますが、現時点では並列化されていません。要素を移動または置換するだけのアルゴリズムの並列化には利点がないことがプロファイリングで示されました。
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 バージョン 15.6

- \<memory_resource>
- ライブラリ基礎 V1
- `polymorphic_allocator` の割り当ての削除
- クラス テンプレート引数の推論の機能強化

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

- 並列アルゴリズムのサポートが試験段階ではなくなった
- \<filesystem> の新しい実装
- 基本文字列変換 (部分的)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- 不要な decay の回避
- 数学的特殊関数
- `constexpr char_traits`
- 標準ライブラリの推論ガイド

詳細については、「[Microsoft C++ 言語の準拠表](../visual-cpp-language-conformance.md)」を参照してください。

### <a name="performance-and-throughput-fixes"></a>パフォーマンスやスループットの修正

- `basic_string::find(char)` オーバーロードで `traits::find` が 1 回だけ呼び出されるようになりました。 これまでは、長さ 1 の文字列の一般的な文字列検索として実装されていました。
- `basic_string::operator==` では、文字列の内容を比較する前に文字列のサイズがチェックされるようになりました。
- コンパイラ オプティマイザーによる分析が困難であった `basic_string` でのコントロールの結合が削除されました。 短い文字列では、`reserve` を呼び出すと、処理は何も行われませんがコストは 0 ではありません。
- `std::vector` が正確性とパフォーマンスについて徹底的に見直されました。挿入および配置操作中のエイリアシングが標準に従って適切に処理されるようになりました。強固な例外保証が、標準で求められるときに `move_if_noexcept()` およびその他のロジックを介して提供されるようになりました。挿入および配置に伴う要素の操作が少なくなりました。
- C++ 標準ライブラリでは、手の込んだ null ポインターの逆参照が回避されるようになりました。
- `weak_ptr::lock()` パフォーマンスが向上しました。
- コンパイラのスループットを上げるため、C++ 標準ライブラリ ヘッダーで不要なコンパイラ組み込みの宣言を含むことが回避されるようになりました。
- `std::string` および `std::wstring` の移動コンストラクターのパフォーマンスが 3 倍以上に向上しました。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- 構造化例外処理 (SEH) を使用する関数に `std::atomic` の実装をインライン展開することを防ぐ `noexcept` との相互作用を回避しました。
- 標準ライブラリの `_Deallocate()` 内部関数を変更してより小さなコードに最適化し、より多くの場所にインライン化できるようにしました。
- `std::try_lock()` を変更し、再帰の代わりにパック展開を使用するようにしました。
- `std::lock()` のデッドロック回避アルゴリズムを改善し、すべてのロックで `try_lock()` を使用するのではなく、`lock()` 操作を使用するようにしました。
- `system_category::message()` で名前付きの戻り値の最適化を有効にしました。
- `conjunction` および `disjunction` が、2N + 2 型ではなく、N + 1 型をインスタンス化するようになりました。
- `std::function` が各々の型消去呼び出しのアロケーター サポート メカニズムをインスタンス化しなくなり、多くの異なるラムダを `std::function` に渡すプログラムでスループットが向上し、.obj サイズが縮小しました。
- `allocator_traits<std::allocator>` に手動でインライン化された `std::allocator` 操作が含まれたことにより、`allocator_traits` のみで `std::allocator` とやり取りするコード (つまりほとんどのコード) のコード サイズが縮小されます。
- C++ 11 の最小アロケーター インターフェイスは、内部クラス `_Wrap_alloc` 内のアロケーターをラップするのでなく、直接 `allocator_traits` を呼び出す標準ライブラリによって処理されるようになりました。 この変更により、アロケーター サポートに対して生成されるコード サイズが小さくなり、オプティマイザーの機能が向上して標準ライブラリのコンテナーを推測できる場合があり、デバッグ エクスペリエンスが向上します (デバッガーで `_Wrap_alloc<your_allocator_type>` ではなくアロケーター型を表示するようになりました)。
- カスタマイズされた `allocator::reference` のメタプログラミングを削除しました。実際にアロケーターをカスタマイズすることは許可されていないものです。 (アロケーターは、コンテナーが手の込んだポインターを使用するようにできますが、手の込んだ参照を使用するようにはできません。)
- コンパイラのフロントエンドが、範囲ベースの for ループでデバッグ反復子のラップを解除するようにしてあり、デバッグ ビルドのパフォーマンスを向上させます。
- `shrink_to_fit()` と `reserve()` への `basic_string` の内部圧縮パスは再割り当て操作のパスではなくなったため、変化を伴うすべてのメンバーのコード サイズが減少します。
- `basic_string` の内部拡張パスが、`shrink_to_fit()` のパスからなくなりました。
- `basic_string` の変更操作が、非割り当て高速パスと割り当て低速パスの関数に含まれるようになり、一般的な非割り当てのケースが呼び出し元にインライン化されやすくなりました。
- `basic_string` の変化を伴う操作が、インプレースでサイズ変更するのではなく、目的の状態で、再割り当てバッファーを構築するようになりました。 たとえば、文字列の先頭への挿入は、再割り当ての場合に 2 回 (新しく割り当てられたバッファーへ、そして下へ) 移動するのではなく、一度 (下へ、または新しく割り当てられたバッファーへ) 完全に挿入した後にコンテンツを移動させます。
- \<string\> 内の C 標準ライブラリを呼び出す操作では、`errno` のアドレスをキャッシュに格納することで、TLS でのやり取りを繰り返さないようになりました。
- `is_pointer` の実装を簡素化しました。
- 関数ベースの SFINAE 式から `struct` および `void_t` ベースへの変更が完了しました。
- 標準ライブラリのアルゴリズムで、ポスト インクリメントの反復子を使用しないようになりました。
- 64 ビット システムで 32 ビットのアロケーターを使用した場合の切り捨ての警告を修正しました。
- non-POCMA non-equal-allocator の場合に、バッファーが使用可能な場合は再利用することによって、`std::vector` 移動割り当てがより効率的になるようになりました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- `basic_string<char16_t>` は、`basic_string<wchar_t>` が連動するのと同じ `memcmp`、`memcpy`、および類似の最適化と連動するようになりました。
- オプティマイザーに制約があり、Visual Studio 2015 更新プログラム 3 の "関数のコピーを避ける" で関数ポインターがインライン公開されることが妨げられていましたが、それが回避されました。`lower_bound(iter, iter, function pointer)` のパフォーマンスが元に戻ります。
- 反復子デバッグで、`includes`、`set_difference`、`set_symmetric_difference`、`set_union` への入力の順序を検証するためのオーバーヘッドは、順序の確認前に反復子の折り返しを解除することで減らされました。
- `std::inplace_merge` は、既に定位置にある要素をスキップするようになりました。
- `std::random_device` の構築では、`std::string` を構築し、その後破棄することがなくなりました。
- `std::equal` と `std::partition` でジャンプスレッドという最適化に成功しました。この最適化で反復子比較が省かれます。
- `std::reverse` に普通にコピー可能な `T` のポインターが渡されると、手書きのベクター化された実装にディスパッチします。
- `std::fill`、`std::equal`、`std::lexicographical_compare` は、`std::byte` と `gsl::byte` (さらに、その他の char などの列挙型と enum クラス) の `memset` および `memcmp` にディスパッチする方法を学習しました。 `std::copy` では `is_trivially_copyable` を使ってディスパッチするので、いかなる変更も必要ありませんでした。
- 標準ライブラリにはもう、唯一の行動が型を non-trivially-destructible (普通に破棄できない) にすることであった空のかっこのデストラクターが含まれていません。

## <a name="other-libraries"></a>他のライブラリ

### <a name="open-source-library-support"></a>オープンソース ライブラリのサポート

**Vcpkg** は、Visual Studio でオープンソースの C++ スタティック ライブラリと DLL を取得してビルドするプロセスを大幅に単純化するオープンソースのコマンド ライン ツールです。 詳細については、[vcpkg: C++ 用のパッケージ マネージャー](../build/vcpkg.md)に関する記事を参照してください。

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

C++ 用のクロスプラットフォーム Web API である CPPRestSDK が、バージョン 2.9.0 に更新されました。 詳しくは、「[CppRestSDK 2.9.0 is available on GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/)」(CppRestSDK 2.9.0 が GitHub で入手可能) をご覧ください。

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- もう 1 つの名前検索の適合性が解決しました
- 既存の移動コンストラクターと移動代入演算子が非スローとして正しくマークされるようになりました。
- atlstr.h のローカルな静的変数のスレッド セーフな init に関する有効な警告 (C4640) の抑制が解除されました。
- ATL を使って DLL をビルドするとき、XP ツールセットで、ローカルな静的変数のスレッドセーフな初期化が自動的に無効になっていましたが、そうではなくなりました。 スレッドセーフな初期化をオフにすることを希望する場合は、[プロジェクト] 設定で **/Zc:threadSafeInit-** を追加することができます。

### <a name="visual-c-runtime"></a>Visual C++ ランタイム

- コントロール フロー ガード シンボルに新しいヘッダー "cfguard.h" が追加されました。

## <a name="c-ide"></a>C++ IDE

- C++ ネイティブ プロジェクトの構成変更が簡単になりました。C++/CLI プロジェクトの場合、さらに簡単です。 ソリューション構成を初めて有効にするとき、そのプロセスが以前より速やかに進行し、そのソリューション構成の後続のアクティベーションがすべて即座に完了します。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- プロジェクトとコードのいくつかのウィザードを署名ダイアログのスタイルで書き直しました。
- **[クラスの追加]** でクラス追加ウィザードが直接起動されるようになりました。 以前ここにあったその他の項目はすべて、 **[追加] > [新しい項目]** に移動しています。
- **[新しいプロジェクト]** ダイアログで、Win32 プロジェクトが **[Windows デスクトップ]** カテゴリに表示されるようになりました。
- **Windows コンソール**のテンプレートと **Windows デスクトップ アプリケーション**のテンプレートで、ウィザードなしでプロジェクトを作成するようになりました。 以前の **Win32 コンソール アプリケーション** ウィザードと同じオプションを表示する同じカテゴリに新しい **Windows デスクトップ ウィザード**が追加されました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

リファクタリングとコード ナビゲーションに IntelliSense エンジンを使用する C++ 演算のいくつかがより速く実行されます。 次の数値は Visual Studio Chromium ソリューションと 3500 件のプロジェクトに基づきます。

|||
|-|-|
|機能|パフォーマンス改善|
|名前の変更|5.3x|
|シグネチャの変更 |4.5x|
|[すべての参照の検索]|4.7x|

C++ では、Ctrl を押しながら **[定義へ移動]** をクリックできるようになりました。マウス操作で簡単に定義に移動できます。 Productivity Power Tools パックの構造ビジュアライザーが既定で製品にも含まれるようになりました。

## <a name="intellisense"></a>IntelliSense

- SQLite ベースの新しいデータベース エンジンが、既定で使用されるようになりました。 これにより、 **[定義に移動]** や **[すべての参照を検索]** などのデータベース操作が高速化され、ソリューションの初期解析時間も大幅に短縮されます。 設定は、 **[ツール]、[オプション]、[テキスト エディター]、[C/C++]、[詳細設定]** に移動しました (以前は、... [C/C++]、[試験的] の下)。

- プリコンパイル済みヘッダーを使用していないプロジェクトやファイルでの IntelliSense のパフォーマンスが向上しました。現在のファイルのヘッダーに対して自動プリコンパイル済みヘッダーが作成されます。

- エラー一覧の IntelliSense エラーに対するフィルター処理とヘルプが追加されました。 エラー列をクリックするとフィルター処理を実行できます。 また、特定のエラーをクリックするか F1 キーを押すと、エラー メッセージのオンライン検索が開始します。

  ![エラー一覧](media/ErrorList1.png "エラー一覧")

  ![フィルター処理されたエラー一覧](media/ErrorList2.png "フィルター処理されたエラー一覧")

- メンバー リストの項目を種類別にフィルターする機能が追加されました。

  ![メンバー一覧のフィルター処理](media/mlfiltering.png "メンバー リストのフィルター処理")

- メンバー リストの表示項目のコンテキストに応じたフィルター処理を提供する新しい実験的な予測 IntelliSense 機能が追加されました。 詳しくは、「[C++ IntelliSense Improvements - Predictive IntelliSense & Filtering (C++ IntelliSense の機能改善 - 予測 IntelliSense とフィルター処理)](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/)」を参照してください。
- **[すべての参照の検索]** (Shift + F12) を使って、複雑なコードベースでも簡単に参照できるようになりました。 高度なグループ化、フィルター処理、並べ替え、結果内の検索と色づけ (一部の言語) が提供され、参照を明確に理解できます。 C++ では、新しい UI に、変数から読み取っているのか、または変数に書き込んでいるのかに関する情報が含まれます。
- Dot-to-Arrow IntelliSense 機能が試験段階から進んだ段階に移り、既定で有効になっています。 エディターの **[Expand Scopes]\(スコープの展開\)** および **[Expand Precedence]\(優先順位の展開\)** 機能が試験段階から進んだ段階に移ります。
- 試験的なリファクタリング機能である **署名の変更** および **関数の抽出** が既定で使用可能になりました。
- C++ プロジェクトの "迅速なプロジェクトの読み込み" の試験的機能が追加されました。 C++ プロジェクトを次回に開いた際に、読み込みが速くなり、またそれ以降、読み込みが "*さらに*" 速くなります。
- 他の言語と共通の機能と、C++ に固有の機能があります。 これらの新機能について詳しくは、「[Announcing Visual Studio "15" Preview 5 (Visual Studio "15" プレビュー 5 のご案内)](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/)」をご覧ください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

- ClangFormat のサポートが追加されました。 詳細については、「[ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/)」 (Visual Studio 2017 での ClangFormat のサポート) を参照してください。

## <a name="non-msbuild-projects-with-open-folder"></a>非 MSBuild プロジェクトと [フォルダーを開く]

Visual Studio 2017 で導入された **[フォルダーを開く]** 機能を使うと、ソリューションまたはプロジェクトを作成することなく、ソース コードを含むフォルダーでコーディング、ビルド、デバッグを行うことができます。 現在は、プロジェクトが MSBuild ベースではない場合でも、Visual Studio を簡単に使い始めることができます。 **[フォルダーを開く]** では、Visual Studio で MSBuild プロジェクトに対して既に提供されている、強力なコード理解、編集、ビルド、デバッグの機能にアクセスできます。 詳細については、「[Open Folder projects for C++](../build/open-folder-projects-cpp.md)」 (C++ の [フォルダーを開く] プロジェクト) をご覧ください。

- [フォルダーを開く] のエクスペリエンスが改善されました。 以下の json ファイルを使って、エクスペリエンスをカスタマイズできます。
  - CppProperties.json: IntelliSense および参照エクスペリエンスをカスタマイズします。
  - Tasks.json: ビルド ステップをカスタマイズします。
  - Launch.json: デバッグ エクスペリエンスをカスタマイズします。

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- MinGW や Cygwin といった、別のコンパイラとビルド環境のサポートを強化しました。 詳細については、「[Using MinGW and Cygwin with Visual C++ and Open Folder (Visual C++ と [フォルダーを開く] で MinGW と Cygwin を使用する)](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/)」をご覧ください。
- CppProperties.json と CMakeSettings.json でグローバル環境変数と構成固有の環境変数を定義するためのサポートが追加されました。 この環境変数は、launch.vs.json に定義されているデバッグ構成と tasks.vs.json のタスクで利用されます。 詳細については、「[Customizing your Environment with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/)」 (Visual C++ と [フォルダーを開く] で環境をカスタマイズする) をご覧ください。
- 簡単に 64 ビット プラットフォームを対象とする機能など、CMake の Ninja generator のサポートを強化しました。

## <a name="cmake-support-via-open-folder"></a>[フォルダーを開く] での CMake のサポート

Visual Studio 2017 では、MSBuild プロジェクト ファイル (.vcxproj) を変換しなくても、CMake プロジェクトを使用できるようになりました。 詳細については、「[CMake projects in Visual Studio](../build/cmake-projects-in-visual-studio.md)」 (Visual Studio の CMake プロジェクト) をご覧ください。 **[フォルダーを開く]** で CMake プロジェクトを開くと、C++ の編集、ビルド、およびデバッグ用の環境が自動的に構成されます。

- C++ の IntelliSense は、ルート フォルダーに CppProperties.json ファイルを作成しなくても動作します。 また、CMake に用意された構成と CppProperties.json ファイルをユーザーが簡単に切り替えることができるように新しいドロップダウンが追加されました。

- CMakeLists.txt ファイルと同じフォルダーに配置される CMakeSettings.json ファイルにより、追加の構成がサポートされます。

  ![CMake の [フォルダーを開く]](media/cmake-cpp.png "CMake の [フォルダーを開く]")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- CMake Ninja generator のサポートが追加されました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- 既存の CMake キャッシュをインポートするためのサポートが追加されました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- CMake 3.11、CMake プロジェクトでのコード分析、ソリューション エクスプローラーのターゲット ビュー、キャッシュ生成用のオプション、および単一ファイルのコンパイルのためのサポートが追加されました。 詳細については、[Visual Studio での CMake のサポート](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/)に関するページと、「[Visual Studio の CMake プロジェクト](../build/cmake-projects-in-visual-studio.md)」をご覧ください。

## <a name="windows-desktop-development-with-c"></a>C++ による Windows デスクトップ開発

元の C++ ワークロードのインストールに対して、より詳細なインストール エクスペリエンスを提供します。 必要なツールだけをインストールできる選択可能なコンポーネントが追加されました。 インストーラーの UI のコンポーネント一覧で示されるインストール サイズは正確ではなく、合計サイズが少なめに表示されます。

C++ デスクトップ ワークロードで Win32 プロジェクトを作成するには、ツールセットと Windows SDK の両方をインストールする必要があります。 推奨される (選択されている) コンポーネント **VC++ 2017 v141 toolset (x86, x64)** と **Windows 10 SDK (10.0.nnnnn)** をインストールすれば、確実に実行できます。 必要なツールがインストールされていない場合、プロジェクトは正常に作成されず、ウィザードがハングします。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

Visual C++ Build ツール (以前はスタンドアロン製品として入手できた) は現在、Visual Studio インストーラーにワークロードとして含まれています。 このワークロードは、C++ プロジェクトの構築に必要なツールだけをインストールします。Visual Studio IDE はインストールしません。 v140 と v141 のいずれのツールセットも含まれます。 v141 ツールセットには Visual Studio 2017 バージョン 15.5 の最新の機能強化が含まれています。 詳細については、「[Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/)」 (Visual Studio Build Tools に VS2017 および VS2015 MSVC ツールセットが追加されました) を参照してください。

## <a name="linux-development-with-c"></a>C++ による Linux 開発

よく利用される拡張機能である [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) が Visual Studio に組み込まれます。 このインストールでは、Linux 環境で実行する C++ アプリケーションの開発とデバッグに必要なすべてのものが提供されます。

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 バージョン 15.2

クロスプラットフォームのコード共有と型の視覚化の機能強化が行われました。 詳細については、「[Linux C++ improvements for cross-platform code sharing and type visualization (Linux C++ の、クロスプラットフォームのコード共有と型の視覚化の機能強化)](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/)」をご覧ください。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- Linux ワークロードでは、リモート Linux マシンにファイルを同期するための **sftp** の代替として **rsync** が使えるようになりました。
- ARM マイクロコントローラーを対象とするクロス コンパイルのサポートが追加されました。 インストールでそれを有効にするには、**C++ による Linux 開発**ワークロードを選び、**埋め込みおよび IoT 開発**のオプションを選びます。 このオプションでは、ARM GCC クロス コンパイル ツールと Make がインストールに追加されます。 詳細については、「[ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/)」 (Visual Studio の ARM GCC クロス コンパイル) を参照してください。
- CMake のサポートが追加されました。 Visual Studio プロジェクトに変換しなくても、既存の CMake コード ベースで作業できるようになりました。 詳細については、「[Configure a Linux CMake Project](../linux/cmake-linux-project.md)」 (Linux CMake プロジェクトを構成する) を参照してください。
- リモート タスクを実行するためのサポートが追加されました。 この機能により、Visual Studio の接続マネージャーに定義されているリモート システムであらゆるコマンドを実行できます。 リモート タスクでは、リモート システムにファイルをコピーすることもできます。
詳細については、「[Configure a Linux CMake Project](../linux/cmake-linux-project.md)」 (Linux CMake プロジェクトを構成する) を参照してください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

- Linux ワークロードのシナリオへのさまざまな機能強化。 詳細については、「[Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/)」(プロジェクト システム、Linux コンソール ウィンドウ、rsync およびプロセスへのアタッチに対する Linux C++ ワークロードの機能改善) を参照してください。
- リモート Linux 接続のヘッダーでの IntelliSense。 詳細については、「[IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/)」 (リモート Linux ヘッダーでの IntelliSense) および「[Linux CMake プロジェクトを構成する](../linux/cmake-linux-project.md)」を参照してください。

## <a name="game-development-with-c"></a>C++ によるゲーム開発

C++ を最大限に活用して DirectX または Cocos2d で駆動するプロフェッショナルなゲームを構築します。

## <a name="mobile-development-with-c-android-and-ios"></a>C++ によるモバイル開発 (Android および iOS)

Android および iOS を対象とするモバイル アプリを、Visual Studio を使用して作成およびデバッグできるようになりました。

## <a name="universal-windows-apps"></a>ユニバーサル Windows アプリ

ユニバーサル Windows アプリ ワークロードのオプション コンポーネントとして、C++ が提供されます。  C++ プロジェクトのアップグレードは、現在のところ、手動で行う必要があります。 v140 をターゲットとするユニバーサル Windows プラットフォーム プロジェクトを Visual Studio 2017 で開くときに、Visual Studio 2015 がインストールされていない場合はプロジェクト プロパティ ページで v141 プラットフォーム ツールセットを選択する必要があります。

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>ユニバーサル Windows プラットフォーム (UWP) での C++ の新しいオプション

ユニバーサル Windows プラットフォームおよび Windows ストア用の C++ アプリケーションを記述およびパッケージ化するための新しいオプションが追加されました。デスクトップ ブリッジ インフラストラクチャを使うと、Windows ストアまたはサイドローディングを経由した既存のチャネルを通してデプロイできるように、既存のデスクトップ アプリケーションまたは COM オブジェクトをパッケージ化できます。 Windows 10 の新機能を使用すると、さまざまな方法で、デスクトップ アプリケーションに UWP 機能を追加できます。 詳細については、[デスクトップ ブリッジ](/windows/uwp/porting/desktop-to-uwp-root)に関するページをご覧ください。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

**Windows アプリケーション パッケージ プロジェクト**というプロジェクト テンプレートが追加されました。このテンプレートでは、デスクトップ ブリッジでのデスクトップ アプリケーションのパッケージ化が大幅に簡略化されます。 **[ファイル] > [新規] > [プロジェクト] > [インストール] > [Visual C++] > [ユニバーサル Windows プラットフォーム]** の下にあります。 詳細については、「[Visual Studio を使ったアプリのパッケージ化 (デスクトップ ブリッジ)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)」をご覧ください。

新しいコードを作成するときに、ヘッダー ファイルだけに実装される Windows ランタイム向けの標準 C++ 言語プロジェクションである C++/WinRT を使うことができるようになりました。 これにより、標準準拠の任意の C++ コンパイラを使って、Windows ランタイム API を作成および使用できます。 C++/WinRT は、C++ の開発者が最新の Windows API に最適にアクセスできるように設計されています。 詳しくは、「[C++/WinRT: Modern C++ for the Windows Runtime (C++/WinRT: Windows ランタイム用の最新の C++)](https://moderncpp.com/)」をご覧ください。

Windows SDK Insider Preview のビルド 17025 より、C++/WinRT が Windows SDK に含まれるようになりました。 詳細については、「[C++/WinRT is now included the Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/)」 (C++/WinRT が Windows SDK に追加されました) を参照してください。

## <a name="clangc2-platform-toolset"></a>Clang/C2 プラットフォーム ツールセット

Visual Studio 2017 に同梱されている Clang/C2 ツールセットが **/bigobj** スイッチをサポートするようになりました。これは、大規模なプロジェクトを構築する際に重要です。 また、コンパイラのフロントエンドとバックエンドの両方について、いくつかの重要なバグ修正が組み込まれました。

## <a name="c-code-analysis"></a>C++ コードの分析

[C++ コア ガイドライン](https://github.com/isocpp/CppCoreGuidelines)を適用するための C++ コア チェッカーが Visual Studio で配布されています。 プロジェクトのプロパティ ページの **[Code Analysis Extensions]\(コード分析の拡張機能\)** ダイアログでチェックを有効にするだけで、拡張機能がコード分析の実行時に含まれます。 詳細については、「[Using the C++ Core Guidelines checkers (C++ Core ガイドラインのチェッカーを使用する)](/cpp/code-quality/using-the-cpp-core-guidelines-checkers)」をご覧ください。

![CppCoreCheck](media/CppCoreCheck.png "CppCoreCheck のプロパティ ページ")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 バージョン 15.3

- リソース管理に関連するルールのサポートが追加されました。

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

- 新しい C++ Core Guidelines チェックでは、スマート ポインターが正しいこと、グローバル初期化子の使い方が正しいこと、コンストラクトのフラグ使用 (`goto` や不良キャストなど) が確認されます。

- 15.3 で使われていた警告番号の一部は 15.5 では使われなくなりました。 より具体的なチェックに置換されました。

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 バージョン 15.6

- 単一ファイルの分析、および分析実行時のパフォーマンス向上のサポートの追加。 詳細については、「[C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)」 (Visual Studio 2017 15.6 プレビュー 2 での C++ スタティック分析の改善) を参照してください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

- 実行するコード分析ルールを指定できる [/analyze: ruleset](../build/reference/analyze-code-analysis.md) のサポートの追加。
- 追加の C++ Core Guidelines ルールのサポートの追加。  詳細については、「[Using the C++ Core Guidelines checkers (C++ Core ガイドラインのチェッカーを使用する)](/cpp/code-quality/using-the-cpp-core-guidelines-checkers)」をご覧ください。

## <a name="unit-testing"></a>単体テスト

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 バージョン 15.5

Google Test Adapter と Boost.Test Adapter は **C++ ワークロードによるデスクトップ開発**のコンポーネントとして入手できるようになりました。**テスト エクスプローラー**と統合されています。 Cmake プロジェクト ([フォルダーを開く] を使用) のための CTest サポートが追加されました。ただし、**テスト エクスプローラー**との完全統合はまだ利用できません。 詳細については、「[C/C++ 用の単体テストの記述](/visualstudio/test/writing-unit-tests-for-c-cpp)」を参照してください。

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 バージョン 15.6

- Boost.Test ダイナミック ライブラリのサポートの追加。
- 現在、Boost.Test 項目テンプレートは IDE にあります。

詳細については、「[Boost.Test Unit Testing:Dynamic Library support and New Item Template](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/)」(Boost.Test 単体テスト: 動的ライブラリのサポートと新しい項目テンプレート) を参照してください。

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 バージョン 15.7

C++ 単体テスト プロジェクトへの [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) のサポートの追加。 詳細については、「[Announcing CodeLens for C++ Unit Testing](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/)」 (C++ 単体テスト用の CodeLens の発表) を参照してください。

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio グラフィックス診断

Visual Studio のグラフィックス診断は、Direct3D アプリのレンダリングとパフォーマンスを記録し、問題を分析するためのツール セットです。 グラフィックス診断機能は、Windows PC でローカルに実行されているアプリ、Windows デバイス エミュレーターで実行されているアプリ、あるいはリモート PC またはデバイスで実行されているアプリに対して使用できます。

- **頂点シェーダーとジオメトリ シェーダーの入力と出力:** 頂点シェーダーとジオメトリ シェーダーの入力と出力を表示する機能は、最も要求の多かった機能の 1 つであり、ツールでサポートされるようになりました。 パイプライン ステージ ビューで VS または GS ステージを選ぶだけで、次の表の入力と出力を調べることができます。

  ![シェーダーの入力/出力](media/io-shaders.png)

- **オブジェクト テーブルでの検索とフィルター:** 探しているリソースを検索する迅速かつ簡単な手段を提供します。

  ![検索](media/search.png)

- **リソース履歴:** この新しいビューは、キャプチャされたフレームのレンダリング時に使われたリソースの全体の変更履歴を表示する簡単な手段を提供します。 リソースの履歴を呼び出すには、リソースのハイパーリンクの横にある時計のアイコンをクリックします。

  ![リソース履歴](media/resource-history.png)

  新しい**リソース履歴**ツール ウィンドウに、リソースの変更履歴が表示されます。

  ![リソース履歴の変更](media/resource-history-change.png)

  完全な呼び出し履歴のキャプチャを有効にしてフレームをキャプチャした場合 ( **[グラフィックス診断]** で **[Visual Studio] > [ツール] > [オプション]** の順に選択)、Visual Studio プロジェクト内の各変更イベントのコンテキストを簡単に推測および検査できます。

- **API 統計情報:** フレームでの API の使用の概要を表示します。 行っていることにまったく気付いていない呼び出しまたは多すぎる呼び出しを発見するのに便利です。 このウィンドウは、Visual Studio Graphics Analyzer の **[表示] > [API 統計情報]** から表示できます。

  ![API 統計情報](media/api-stats.png)

- **メモリ統計情報:** フレームで作成されたリソースにドライバーが割り当てているメモリの量を表示します。 このウィンドウは、**Visual Studio Graphics Analyzer** の **[表示]、[メモリ統計情報]** から表示できます。 右クリックして **[すべてコピー]** を選ぶことで、データを CSV ファイルにコピーしてスプレッドシートで表示できます。

  ![メモリ統計情報](media/memory-stats.png)

- **フレームの検証:** 新しいエラーと警告の一覧は、Direct3D デバッグ レイヤーで検出された潜在的な問題を基に、イベント リストを移動する簡単な方法を提供します。 ウィンドウを開くには、Visual Studio Graphics Analyzer で **[表示]、[フレームの検証]** をクリックします。 次に、 **[検証の実行]** をクリックして分析を開始します。 フレームの複雑さによっては、完了するまでに数分かかることがあります。

  ![フレームの検証](media/frame-validation.png)

- **D3D12 のフレーム分析:** フレーム分析を使って、指示された "what-if" 実験で描画呼び出しのパフォーマンスを分析します。 [フレーム分析] タブに切り替え、分析を実行してレポートを表示します。 詳細については、「[GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool)」(GoingNative 25: Visual Studio のグラフィックス フレーム分析) のビデオをご覧ください。

  ![フレーム分析](media/frame-analysis.png)

- **GPU 使用率の改善:** GPU ビューまたは Windows パフォーマンス アナライザー (WPA) ツールを使って Visual Studio の GPU 使用率プロファイラーで取得されたトレースを開き、詳細な分析を行うことができます。 Windows パフォーマンス ツールキットがインストールされている場合、セッション概要の右下に WPA と GPU ビューの 2 つのハイパーリンクが表示されます。

  ![GPU 使用率](media/gpu-usage.png)

  このリンクから GPU ビューで開かれるトレースは、VS と GPU ビューの間で同期されたタイムラインのズームとパンをサポートします。 VS 内のチェック ボックスは、同期の有効/無効を制御するために使われます。

  ![GPU ビュー](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Visual Studio 2015 更新プログラム 3 での新機能の完全な一覧については、「[Visual Studio 2003 から 2015 の Visual C++ の新機能](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)」を参照してください。 すべての Visual Studio 2015 での新機能について詳しくは、「[Visual Studio 2015 リリース ノート履歴](/visualstudio/releasenotes/vs2015-version-history)」からリンクされているリリース ノートをご覧ください。 Visual Studio 2019 での C++ の新機能については、「[Visual Studio での C++ の新機能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019)」を参照してください。 Visual Studio 2017 での C++ の新機能については、「[Visual Studio 2017 での C++ の新機能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017)」を参照してください。

::: moniker-end
