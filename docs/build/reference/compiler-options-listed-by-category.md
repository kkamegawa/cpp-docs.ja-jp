---
title: カテゴリ別のコンパイラ オプション
description: Microsoft C/C++コンパイラのコマンドラインオプションのカテゴリ別の参照リスト。
ms.date: 02/09/2020
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: d29076e6eae4bcbd15a4bc50bb48477e3f93152d
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257716"
---
# <a name="compiler-options-listed-by-category"></a>カテゴリ別のコンパイラ オプション

この記事には、コンパイラ オプションのカテゴリ別の一覧が含まれています。 アルファベット順の一覧については、「[アルファベット順に表示されるコンパイラオプション](compiler-options-listed-alphabetically.md)」を参照してください。

## <a name="optimization"></a>Optimization

|オプション|目的|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|コードを最小化します。|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|コードを最速化します。|
|[/Ob](ob-inline-function-expansion.md)|関数のインライン展開を制御します。|
|[/Od](od-disable-debug.md)|最適化を無効にします。|
|[/Og](og-global-optimizations.md)|非推奨。 グローバル最適化を使用します。|
|[/Oi](oi-generate-intrinsic-functions.md)|組み込み関数を生成します。|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|実行可能ファイルで、サイズの小ささを優先させます。|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|実行可能ファイルで、実行速度を優先させます。|
|[/Ox](ox-full-optimization.md)|/GF または/gyを含まない/O2 のサブセット。|
|[/Oy](oy-frame-pointer-omission.md)|フレーム ポインターなし (x86 のみ)|
|[/favor](favor-optimize-for-architecture-specifics.md)|指定したアーキテクチャまたは一連のアーキテクチャ用に最適化されたコードを生成します。|

## <a name="code-generation"></a>コードの生成

|オプション|目的|
|------------|-------------|
|[/arch](arch-x86.md)|コード生成で SSE または SSE2 命令を使用します。 (x86 のみ)|
|[/clr](clr-common-language-runtime-compilation.md)|共通言語ランタイムで実行する出力ファイルを作成します。|
|[/EH](eh-exception-handling-model.md)|例外処理のモデルを指定します。|
|[/fp](fp-specify-floating-point-behavior.md)|浮動小数点の動作を指定します。|
|[/GA](ga-optimize-for-windows-application.md)|Windows アプリケーション用に最適化します。|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|`__cdecl` 呼び出し規約を使用します。 (x86 のみ)|
|[/Ge](ge-enable-stack-probes.md)|非推奨。 スタック プローブをアクティブにします。|
|[/GF](gf-eliminate-duplicate-strings.md)|文字列プールを有効にします。|
|[/Gh](gh-enable-penter-hook-function.md)|フック関数 `_penter`を呼び出します。|
|[/GH](gh-enable-pexit-hook-function.md)|フック関数 `_pexit`を呼び出します。|
|[/GL](gl-whole-program-optimization.md)|プログラム全体の最適化を有効にします。|
|[/Gm](gm-enable-minimal-rebuild.md)|非推奨。 簡易リビルドを有効にします。|
|[/GR](gr-enable-run-time-type-information.md)|ランタイム型情報 (RTTI: Run-Time Type Information) を有効にします。|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|`__fastcall` 呼び出し規約を使用します。 (x86 のみ)|
|[/GS](gs-buffer-security-check.md)|バッファーのセキュリティをチェックします。|
|[/Gs](gs-control-stack-checking-calls.md)|スタック プローブを制御します。|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|静的スレッド ローカル ストレージを使用して割り当てられたデータに対して、ファイバー保護をサポートします。|
|[/guard:cf](guard-enable-control-flow-guard.md)|制御フロー ガードのセキュリティ チェックを追加します。|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|`__vectorcall` 呼び出し規約を使用します。 (x86 と x64 のみ)。|
|[/Gw](gw-optimize-global-data.md)|プログラム全体のグローバル データの最適化を有効にします。|
|[/GX](gx-enable-exception-handling.md)|非推奨。 同期例外処理を有効にします。 代わりに [/EH](eh-exception-handling-model.md) を使用してください。|
|[/Gy](gy-enable-function-level-linking.md)|関数レベルのリンクを有効にします。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|非推奨。 高速チェックを有効にします ( [/RTC1](rtc-run-time-error-checks.md)と同等)。|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|`__stdcall` 呼び出し規約を使用します。 (x86 のみ)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|関数の実行に入ったときに、レジスタで渡されたパラメーターを、強制的にスタック内のその場所に書き込みます。 このコンパイラオプションは、x64 コンパイラ (ネイティブコンパイルおよびクロスコンパイル) に対してのみ使用できます。|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|ホットパッチ可能なイメージを作成します。|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|高速超越関数を生成します。|
|[/QIfist](qifist-suppress-ftol.md)|非推奨。 浮動小数点型から整数型への変換が必要なときには、ヘルパー関数 `_ftol` を呼び出しません。 (x86 のみ)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|`fwait` ブロックの中にある `try` コマンドを削除します。|
|[/QIntel-jcc-erratum](qintel-jcc-erratum.md)|Intel JCC erratum マイクロコード更新のパフォーマンスへの影響を軽減します。|
|[/Qpar](qpar-auto-parallelizer.md)|ループの自動並列化を有効にします。|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|自動並列化のレポート レベルを有効にします。|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|浮動小数点値の整数移動命令を使用し、特定の浮動小数点読み込み最適化を無効にします。|
|[/Qspectre](qspectre.md)|Spectre 攻撃のクラスについて、CVE 2017-5753 の軽減策を有効にします。|
|[/Qspectre-load](qspectre-load.md)|すべての読み込み命令のシリアル化命令を生成します。|
|[/Qspectre-load-cf](qspectre-load-cf.md)|メモリを読み込むすべての制御フロー命令のシリアル化命令を生成します。|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|自動ベクター化のレポート レベルを有効にします。|
|[/RTC](rtc-run-time-error-checks.md)|ランタイム エラー チェックを有効にします。|
|[/volatile](volatile-volatile-keyword-interpretation.md)|volatile キーワードの解釈方法を選択します。|

## <a name="output-files"></a>出力ファイル

|オプション|目的|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|ドキュメント コメントを XML ファイルに出力します。|
|[/FA](fa-fa-listing-file.md)|アセンブリ リスト ファイルを構成します。|
|[/Fa](fa-fa-listing-file.md)|アセンブリ リスト ファイルを作成します。|
|[/Fd](fd-program-database-file-name.md)|プログラム データベース ファイルの名前を変更します。|
|[/Fe](fe-name-exe-file.md)|実行可能ファイルの名前を変更します。|
|[/Fi](fi-preprocess-output-file-name.md)|プリプロセス済みの出力ファイルの名前を指定します。|
|[/Fm](fm-name-mapfile.md)|マップファイルを作成します。|
|[/Fo](fo-object-file-name.md)|オブジェクト ファイルを作成します。|
|[/Fp](fp-name-dot-pch-file.md)|プリコンパイル済みヘッダー ファイルの名前を指定します。|
|[/FR、/Fr](fr-fr-create-dot-sbr-file.md)|ブラウザーファイル *`.sbr`* 生成された名前。|

## <a name="preprocessor"></a>プリプロセッサ

|オプション|目的|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|[#using](../../preprocessor/hash-using-directive-cpp.md) ディレクティブに渡されたファイル参照を解決するために検索するディレクトリを指定します。|
|[/C](c-preserve-comments-during-preprocessing.md)|プリプロセス時にコメントを保持します。|
|[/D](d-preprocessor-definitions.md)|定数とマクロを定義します。|
|[/E](e-preprocess-to-stdout.md)|プリプロセッサ出力を標準出力にコピーします。|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|プリプロセッサ出力を標準出力にコピーします。|
|[/FI](fi-name-forced-include-file.md)|指定したインクルード ファイルをプリプロセスします。|
|[/FU](fu-name-forced-hash-using-file.md)|[#using](../../preprocessor/hash-using-directive-cpp.md) ディレクティブに渡された場合と同じ方法でファイル名の使用を強制します。|
|[/Fx](fx-merge-injected-code.md)|挿入されたコードをソース ファイルとマージします。|
|[/I](i-additional-include-directories.md)|ディレクトリ内でインクルード ファイルを検索します。|
|[/P](p-preprocess-to-a-file.md)|プリプロセッサ出力をファイルに書き込みます。|
|[/U](u-u-undefine-symbols.md)|1 つの定義済みマクロを削除します。|
|[/u](u-u-undefine-symbols.md)|すべての定義済みマクロを削除します。|
|[/X](x-ignore-standard-include-paths.md)|標準のインクルード ディレクトリを無視します。|

## <a name="language"></a>言語

|オプション|目的|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|コンパイル時に**constexpr**の評価を制御します。|
|[/openmp](openmp-enable-openmp-2-0-support.md)|ソース コードで [#pragma omp](../../preprocessor/omp.md) を有効にします。|
|[/vd](vd-disable-construction-displacements.md)|隠し `vtordisp` クラス メンバーの無効と有効を切り替えます。|
|[/vmb](vmb-vmg-representation-method.md)|メンバーへのポインターに対して、最適なクラスを使用します。|
|[/vmg](vmb-vmg-representation-method.md)|メンバーへのポインターに対して、ジェネリック クラスを使用します。|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|多重継承を宣言します。|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|単一継承を宣言します。|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|仮想継承を宣言します。|
|[/Z7](z7-zi-zi-debug-information-format.md)|C 7.0 互換のデバッグ情報を生成します。|
|[/Za](za-ze-disable-language-extensions.md)|C89 言語拡張を無効にします。|
|[/Zc](zc-conformance.md)|[/Ze](za-ze-disable-language-extensions.md)の標準動作を指定します。|
|[/Ze](za-ze-disable-language-extensions.md)|非推奨。 C89 言語拡張を有効にします。|
|[/Zf](zf.md)|並列ビルドでの PDB 生成時間を改善します。|
|[/ZH](zh.md)|デバッグ情報のチェックサムに MD5、SHA-1、または SHA-256 を指定します。|
|[/ZI](z7-zi-zi-debug-information-format.md)|エディット コンティニュと互換性のあるプログラム データベースにデバッグ情報を含めます。 (x86 のみ)|
|[/Zi](z7-zi-zi-debug-information-format.md)|詳細なデバッグ情報を生成します。|
|[/Zl](zl-omit-default-library-name.md)|*`.obj`* ファイルから既定のライブラリ名を削除します。|
|[/Zp](zp-struct-member-alignment.md) *n*|構造体メンバーをパックします。|
|[/Zs](zs-syntax-check-only.md)|構文だけをチェックします。|
|[/ZW](zw-windows-runtime-compilation.md)|Windows ランタイムで実行する出力ファイルを作成します。|

## <a name="linking"></a>リンク

|オプション|目的|
|------------|-------------|
|[/F](f-set-stack-size.md)|スタック サイズを設定します。|
|[/LD](md-mt-ld-use-run-time-library.md)|ダイナミック リンク ライブラリを作成します。|
|[/LDd](md-mt-ld-use-run-time-library.md)|デバッグ バージョンのダイナミック リンク ライブラリを作成します。|
|[/link](link-pass-options-to-linker.md)|指定したオプションを LINK に渡します。|
|[/LN](ln-create-msil-module.md)|MSIL モジュールを作成します。|
|[/MD](md-mt-ld-use-run-time-library.md)|は、 *msvcrt.dll*を使用して、マルチスレッド DLL を作成するためにコンパイルします。|
|[/MDd](md-mt-ld-use-run-time-library.md)|*Msvcrtd.lib*を使用して、デバッグ用のマルチスレッド DLL をコンパイルして作成します。|
|[/MT](md-mt-ld-use-run-time-library.md)|*Libcmt.lib*を使用して、マルチスレッド実行可能ファイルをコンパイルして作成します。|
|[/MTd](md-mt-ld-use-run-time-library.md)|*Libcmtd*を使用して、デバッグ用のマルチスレッド実行可能ファイルを作成するためにコンパイルします。|

## <a name="miscellaneous"></a>その他

|オプション|目的|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|コンパイラ オプションのリストを出力します。|
|[@](at-specify-a-compiler-response-file.md)|応答ファイルを指定します。|
|[/analyze](analyze-code-analysis.md)|コード分析を有効にします。|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|.obj ファイル内のアドレス指定可能なセクションの数を増やします。|
|[/c](c-compile-without-linking.md)|リンクを行わないでコンパイルします。|
|[/cgthreads](cgthreads-code-generation-threads.md)|最適化およびコード生成に使用する*cl.exe*スレッド数を指定します。|
|[/errorReport](errorreport-report-internal-compiler-errors.md)| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|診断テキストで*cl.exe*に渡されるソースコードファイルの完全パスを表示します。|
|[/FS](fs-force-synchronous-pdb-writes.md)|は、Mspdbsrv によってシリアル化される PDB ファイルへの書き込みを強制*します。EXE*。|
|[/H](h-restrict-length-of-external-names.md)|非推奨。 外部名 (パブリック名) の長さを制限します。|
|[/HELP](help-compiler-command-line-help.md)|コンパイラ オプションのリストを出力します。|
|[/J](j-default-char-type-is-unsigned.md)|既定の `char` 型を変更します。|
|[/JMC](jmc.md)|ネイティブC++マイコードのみデバッグをサポートします。|
|[/kernel](kernel-create-kernel-mode-binary.md)|コンパイラとリンカーは、Windows カーネルで実行可能なバイナリを作成します。|
|[/MP](mp-build-with-multiple-processes.md)|複数のソース ファイルを同時にビルドします。|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|著作権情報を表示しません。|
|[/sdl](sdl-enable-additional-security-checks.md)|追加のセキュリティ機能と警告を有効にします。|
|[/showIncludes](showincludes-list-include-files.md)|コンパイル時にすべてのインクルード ファイルの一覧を表示します。|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|C ソース ファイルを指定します。|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|すべてのソースファイルが C であることを指定します。|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|C++ ソース ファイルを指定します。|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|すべてのソースファイルがC++であることを指定します。|
|[/V](v-version-number.md)|非推奨。 バージョン文字列を設定します。|
|[/w](compiler-option-warning-level.md)|すべての警告を無効にします。|
|[/W0、/W1、/W2、/W3、/W4](compiler-option-warning-level.md)|出力警告レベルを設定します。|
|[/w1、/w2、/w3、/w4](compiler-option-warning-level.md)|指定した警告の警告レベルを設定します。|
|[/Wall](compiler-option-warning-level.md)|既定で無効にされた警告も含めてすべての警告を有効にします。|
|[/wd](compiler-option-warning-level.md)|指定した警告を無効にします。|
|[/we](compiler-option-warning-level.md)|指定した警告をエラーとして扱います。|
|[/WL](wl-enable-one-line-diagnostics.md)|コマンド ラインから C++ ソース コードをコンパイルするときに、エラー メッセージと警告メッセージの 1 行診断を有効にします。|
|[/wo](compiler-option-warning-level.md)|指定した警告を 1 回だけ表示します。|
|[/Wv](compiler-option-warning-level.md)|新しいバージョンのコンパイラで導入された警告を無効にします。|
|[/WX](compiler-option-warning-level.md)|警告をエラーとして扱います。|
|[/Yc](yc-create-precompiled-header-file.md)|*`.PCH`* ファイルを作成します。|
|[/Yd](yd-place-debug-information-in-object-file.md)|非推奨。 すべてのオブジェクト ファイルに、詳細なデバッグ情報を取り込みます。 代わりに [/Zi](z7-zi-zi-debug-information-format.md) を使用してください。|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|デバッグ ライブラリの作成時に PCH の参照を挿入します。|
|[/Yu](yu-use-precompiled-header-file.md)|ビルド時にプリコンパイル済みヘッダー ファイルを使用します。|
|[/Y-](y-ignore-precompiled-header-options.md)|現在のビルドで、他のすべてのプリコンパイル済みヘッダー コンパイラ オプションを無視します。|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|プリコンパイル済みヘッダーのメモリ割り当て制限を指定します。|
|[/await](await-enable-coroutine-support.md)|コルーチン (再開可能な関数) の拡張機能を有効にします。|
|[/source-charset](source-charset-set-source-character-set.md)|ソース文字セットを設定します。|
|[/execution-charset](execution-charset-set-execution-character-set.md)|実行文字セットを設定します。|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|ソース文字セットと実行文字セットを UTF-8 に設定します。|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|互換性のある文字に対してのみ UTF-8 ファイルを検証します。|
|[/diagnostics](diagnostics-compiler-diagnostic-options.md)|診断メッセージの形式を制御します。|
|[/permissive-](permissive-standards-conformance.md)|標準準拠モードを設定します。|
|[/std](std-specify-language-standard-version.md)|C++標準バージョン互換性セレクター。|

## <a name="experimental-options"></a>試験的なオプション

試験的なオプションは、コンパイラの特定のバージョンでのみサポートされます。 また、コンパイラのバージョンによって動作が異なる場合もあります。 多くの場合、 [ C++ Microsoft チームのブログ](https://devblogs.microsoft.com/cppblog/)には、実験的なオプションについてのドキュメントが最適であるか、唯一のものです。

|オプション|目的|
|------------|-------------|
|[/実験的: モジュール](experimental-module.md)|実験的なモジュールのサポートを有効にします。|
|[/実験的: プリプロセッサ](experimental-preprocessor.md)|試験的に準拠するプリプロセッサのサポートを有効にします。|

## <a name="deprecated-and-removed-compiler-options"></a>非推奨のコンパイラオプションと削除されたコンパイラオプション

|オプション|目的|
|------------|-------------|
|[/clr:noAssembly](clr-common-language-runtime-compilation.md)|非推奨。 代わりに、 [/LN (Create MSIL Module)](ln-create-msil-module.md) を使用してください。|
|[/errorReport](errorreport-report-internal-compiler-errors.md)| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|[/Fr](fr-fr-create-dot-sbr-file.md)|非推奨。 ローカル変数を含まないブラウザー情報ファイルを作成します。|
|[/Ge](ge-enable-stack-probes.md)|非推奨。 スタック プローブをアクティブにします。 既定でオンになっています。|
|[/Gm](gm-enable-minimal-rebuild.md)|非推奨。 簡易リビルドを有効にします。|
|[/GX](gx-enable-exception-handling.md)|非推奨。 同期例外処理を有効にします。 代わりに [/EH](eh-exception-handling-model.md) を使用してください。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|非推奨。 高速チェックを有効にします 代わりに [/RTC1](rtc-run-time-error-checks.md) を使用してください。|
|[/H](h-restrict-length-of-external-names.md)|非推奨。 外部名 (パブリック名) の長さを制限します。|
|[/Og](og-global-optimizations.md)|非推奨。 グローバル最適化を使用します。|
|[/QIfist](qifist-suppress-ftol.md)|非推奨。 浮動小数点型から整数型に変換する方法を指定するために使われていました。|
|[/V](v-version-number.md)|非推奨。 *`.obj`* ファイルのバージョン文字列を設定します。|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|互換性のために残されています。 64 ビット移植性の問題を検出します。|
|[/Yd](yd-place-debug-information-in-object-file.md)|非推奨。 すべてのオブジェクト ファイルに、詳細なデバッグ情報を取り込みます。 代わりに [/Zi](z7-zi-zi-debug-information-format.md) を使用してください。|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|非推奨。 for ループ スコープの準拠を無効にします。|
|[/Ze](za-ze-disable-language-extensions.md)|非推奨。 言語拡張機能を有効にします。|
|[/Zg](zg-generate-function-prototypes.md)|Visual Studio 2015 で削除されました。 関数プロトタイプを生成します。|

## <a name="see-also"></a>参照

[C/C++ビルド参照](c-cpp-building-reference.md)\
[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
