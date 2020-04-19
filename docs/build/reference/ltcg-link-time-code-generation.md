---
title: /LTCG (リンク時のコード生成)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 1e33d62694fe782b1a1719fa3c5a36c6fb04670a
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400627"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (リンク時のコード生成)

**/LTCG** を使用して、プログラム全体の最適化を実行するか、またはガイド付き最適化のプロファイル (PGO) インストルメンテーションを作成し、トレーニングを実行して、ガイド付き最適化のプロファイルによるビルドを作成します。

## <a name="syntax"></a>構文

> **/LTCG**[ **:** {**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]

これらのオプションは、Visual Studio 2015 から非推奨とされます。

> **/LTCG:** {**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}

### <a name="arguments"></a>引数

**INCREMENTAL**<br/>
(省略可能) プロジェクト全体ではなく、編集によって影響を受けたファイル セットにのみ、リンカーによってプログラム全体の最適化またはリンク時のコード生成 (LTCG) を適用することを指定します。 既定では、 **/LTCG** が指定されるとこのフラグは設定されず、プログラム全体の最適化を使用してプロジェクト全体がリンクされます。

**NOSTATUS** &#124; **STATUS**<br/>
(省略可能) リンクの何パーセントが完了したかを示す進行状況のインジケーターをリンカーによって表示するかどうかを指定します。 既定では、この状態情報は表示されません。

**OFF**<br/>
(省略可能) リンク時のコード生成を無効にします。 この動作は、コマンド ラインで **/LTCG** が指定されていない場合と同じです。

**PGINSTRUMENT**<br/>
(省略可能) このオプションは、Visual Studio 2015 から非推奨とされます。 代わりに、 **/LTCG** と [/GENPROFILE または /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) を使用して、ガイド付き最適化のプロファイル用にインストルメント化されたビルドを生成します。 インストルメント化された実行から収集されるデータは、最適化されたイメージの作成に使用されます。 詳細については、「[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)」を参照してください。 このオプションの短い形式は **/LTCG:PGI** です。

**PGOPTIMIZE**<br/>
(省略可能) このオプションは、Visual Studio 2015 から非推奨とされます。 代わりに、 **/LTCG** と [/USEPROFILE](useprofile.md) を使用して、最適化されたイメージを作成します。 詳細については、「[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)」を参照してください。 このオプションの短い形式は **/LTCG:PGO** です。

**PGUPDATE**<br/>
(省略可能) このオプションは、Visual Studio 2015 から非推奨とされます。 代わりに、 **/LTCG** と **/USEPROFILE** を使用して、最適化されたイメージを再作成します。 詳細については、「[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)」を参照してください。 このオプションの短い形式は **/LTCG:PGU** です。

## <a name="remarks"></a>Remarks

**/LTCG** オプションでは、コンパイラを呼び出してプログラム全体の最適化を実行するようにリンカーに指示します。 または、ガイド付きプロファイルの最適化を実行することもできます。 詳細については、「[ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)」を参照してください。

次の例外を除き、以前の PGO 初期化の組み合わせである **/LTCG** オプションと **/GENPROFILE** オプションで指定されていないリンカー オプションを、PGO の組み合わせである **/LTCG** と **/USEPROFILE** に追加することはできません。

- [/BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

**/LTCG** と **/USEPROFILE** を使用してビルドする際に、PGO の初期化のために **/LTCG** オプションおよび **/GENPROFILE** オプションと共に指定されているリンカー オプションを指定する必要はありません。これらは暗黙的に指定されます。

この記事ではこれ以降、リンク時のコード生成の観点から **/LTCG** について説明します。

**/LTCG** は [/GL](gl-whole-program-optimization.md) で暗黙的に指定されます。

**/GL** モジュールまたは MSIL モジュールを使用してコンパイルされたモジュールを渡された場合、リンカーにより、リンク時のコード生成が呼び出されます (「[リンカー入力としての .netmodule ファイル](netmodule-files-as-linker-input.md)」を参照)。 明示的に **/LTCG** を指定せずに **/GL** モジュールまたは MSIL モジュールをリンカーに渡すと、最終的にリンカーによってこれが検出され、 **/LTCG** を使用してリンクが再実行されます。 明示的に **/LTCG** を指定した上で **/GL** モジュールや MSIL モジュールをリンカーに渡すと、最大限に高速のパフォーマンスでビルドが実行されます。

パフォーマンスをさらに高速にするには、 **/LTCG:INCREMENTAL** を使用します。 このオプションを指定すると、リンカーは、プロジェクト全体ではなく、ソース ファイルの変更によって影響を受ける一連のファイルのみを再び最適化します。 これにより、リンクに必要な時間を大幅に削減できます。 これは、インクリメンタル リンクと同じオプションではありません。

**/LTCG** は、[/INCREMENTAL](incremental-link-incrementally.md) では使用できません。

[/Og](og-global-optimizations.md)、[/O1](o1-o2-minimize-size-maximize-speed.md)、[/O2](o1-o2-minimize-size-maximize-speed.md)、または [/Ox](ox-full-optimization.md) を使用してコンパイルされたモジュールを、 **/LTCG** を使用してリンクすると、次の最適化が実行されます。

- クロス モジュールのインライン化

- プロシージャ間のレジスタ割り当て (64 ビット オペレーティング システムのみ)

- カスタムの呼び出し規約 (x86 のみ)

- 小規模な TLS 変位 (x86 のみ)

- スタックの二重配置 (x86 のみ)

- メモリのあいまいさ排除の強化 (グローバル変数および入力パラメーターの干渉情報の改善)

> [!NOTE]
> リンカーにより、各関数のコンパイルにどの最適化が使用されたかが判断され、リンク時に同じ最適化が適用されます。

**/LTCG** と **/Ogt** を使用すると、二重配置の最適化が適用されます。

**/LTCG** と **/Ogs** を指定すると、二重配置は実行されません。 アプリケーション内のほとんどの関数が速度を対象としてコンパイルされ、数個の関数がサイズを対象としてコンパイルされている (たとえば、[optimize](../../preprocessor/optimize.md) プラグマを使用) 場合、コンパイラにより、二重配置を必要とする関数が呼び出されると、サイズを対象として最適化された関数が二重配置されます。

コンパイラで関数のすべての呼び出しサイトを特定できる場合、コンパイラでは関数に対する明示的な呼び出し規約の修飾子が無視され、関数の呼び出し規約の最適化が試行されます。

- レジスタでパラメーターを渡す

- 配置のためにパラメーターを並べ替える

- 使用されていないパラメーターを削除する

関数ポインターを介して関数が呼び出された場合、または **/GL** を使用してコンパイルされたモジュールの外部から関数が呼び出された場合、コンパイラでは関数の呼び出し規約の最適化は試行されません。

> [!NOTE]
> **/LTCG** を使用して `mainCRTStartup` を再定義した場合、アプリケーションでは、グローバル オブジェクトの初期化前に実行されるユーザー コードに関連する、予期しない動作を生じる可能性があります。 この問題に対処するには次の 3 つの方法があります。`mainCRTStartup` を再定義しないこと、 **/LTCG** を使用して `mainCRTStartup` が含まれているファイルをコンパイルしないこと、グローバル変数とグローバル オブジェクトは静的に初期化すること。

### <a name="ltcg-and-msil-modules"></a>/LTCG モジュールと MSIL モジュール

[/GL](gl-whole-program-optimization.md) と [/clr](clr-common-language-runtime-compilation.md) を使用してコンパイルされたモジュールは、 **/LTCG** が指定されている場合にリンカーへの入力として使用できます。

- **/LTCG** では、ネイティブ オブジェクト ファイル、および混在ネイティブ/マネージド オブジェクト ファイル ( **/clr** を使用してコンパイルされる) を受け付けることができます。 **/clr:pure** および **/clr:safe** コンパイラ オプションは Visual Studio 2015 では非推奨とされており、Visual Studio 2017 以降ではサポートされていません。

- **/LTCG:PGI** では、 **/GL** や **/clr** を使用してコンパイルされたネイティブ モジュールは受け付けられません

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」を参照してください。

1. **[構成プロパティ]**  >  **[全般]** プロパティ ページを選択します。

1. **[プログラム全体の最適化]** プロパティを変更します。

または、 **/LTCG** を特定のビルドに適用するために、メニュー バーで **[ビルド]**  >  **[ガイド付き最適化のプロファイル]** を選択する、あるいは、プロジェクトのショートカット メニューから [ガイド付き最適化のプロファイル] のいずれかのオプションを選択するという方法もあります。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
