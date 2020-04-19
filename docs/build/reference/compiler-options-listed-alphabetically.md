---
title: アルファベット順のコンパイラ オプション
description: Microsoft C/C++コンパイラのコマンドラインオプションのアルファベット順の一覧です。
ms.date: 02/09/2020
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 6b3412378aa4bb36ea861a81758d2227df3432c6
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257742"
---
# <a name="compiler-options-listed-alphabetically"></a>アルファベット順のコンパイラ オプション

このテーブルには、コンパイラオプションのアルファベット順の一覧が含まれています。 カテゴリ別のコンパイラオプションの一覧については、「[カテゴリ別のコンパイラオプション](compiler-options-listed-by-category.md)の一覧」を参照してください。

## <a name="compiler-options"></a>コンパイラ オプション

|オプション|目的|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|応答ファイルを指定します。|
|[/?](help-compiler-command-line-help.md)|コンパイラ オプションのリストを出力します。|
|[/AI](ai-specify-metadata-directories.md)|[#using](../../preprocessor/hash-using-directive-cpp.md) ディレクティブに渡されたファイル参照を解決するために検索するディレクトリを指定します。|
|[/analyze](analyze-code-analysis.md)|コード分析を有効にします。|
|[/arch](arch-minimum-cpu-architecture.md)|コード生成のアーキテクチャを指定します。|
|[/await](await-enable-coroutine-support.md)|コルーチン (再開可能な関数) の拡張機能を有効にします。|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|.obj ファイル内のアドレス指定可能なセクションの数を増やします。|
|[/C](c-preserve-comments-during-preprocessing.md)|プリプロセス時にコメントを保持します。|
|[/c](c-compile-without-linking.md)|リンクを行わないでコンパイルします。|
|[/cgthreads](cgthreads-code-generation-threads.md)|最適化およびコード生成に使用する cl.exe スレッド数を指定します。|
|[/clr](clr-common-language-runtime-compilation.md)|共通言語ランタイムで実行する出力ファイルを作成します。|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|コンパイル時に**constexpr**の評価を制御します。|
|[/D](d-preprocessor-definitions.md)|定数とマクロを定義します。|
|[/diagnostics](diagnostics-compiler-diagnostic-options.md)|診断メッセージの形式を制御します。|
|[/doc](doc-process-documentation-comments-c-cpp.md)|ドキュメント コメントを XML ファイルに出力します。|
|[/E](e-preprocess-to-stdout.md)|プリプロセッサ出力を標準出力にコピーします。|
|[/EH](eh-exception-handling-model.md)|例外処理のモデルを指定します。|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|プリプロセッサ出力を標準出力にコピーします。|
|[/errorReport](errorreport-report-internal-compiler-errors.md)| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|[/execution-charset](execution-charset-set-execution-character-set.md)|実行文字セットを設定します。|
|[/実験的: モジュール](experimental-module.md)|実験的なモジュールのサポートを有効にします。|
|[/実験的: プリプロセッサ](experimental-preprocessor.md)|試験的に準拠するプリプロセッサのサポートを有効にします。|
|[/F](f-set-stack-size.md)|スタック サイズを設定します。|
|[/favor](favor-optimize-for-architecture-specifics.md)|特定の x64 アーキテクチャ用に最適化されたコードを生成します。 または、AMD64 アーキテクチャと EM64T アーキテクチャの両方で、特定のマイクロアーキテクチャに対応します。|
|[/FA](fa-fa-listing-file.md)|リスティング ファイルを作成します。|
|[/Fa](fa-fa-listing-file.md)|リスティング ファイル名を設定します。|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|診断テキストで cl.exe に渡されるソース コード ファイルの完全パスを表示します。|
|[/Fd](fd-program-database-file-name.md)|プログラム データベース ファイルの名前を変更します。|
|[/Fe](fe-name-exe-file.md)|実行可能ファイルの名前を変更します。|
|[/FI](fi-name-forced-include-file.md)|指定したインクルード ファイルをプリプロセスします。|
|[/Fi](fi-preprocess-output-file-name.md)|プリプロセス済みの出力ファイル名を設定します。|
|[/Fm](fm-name-mapfile.md)|マップファイルを作成します。|
|[/Fo](fo-object-file-name.md)|オブジェクト ファイルを作成します。|
|[/fp](fp-specify-floating-point-behavior.md)|浮動小数点の動作を指定します。|
|[/Fp](fp-name-dot-pch-file.md)|プリコンパイル済みヘッダー ファイルの名前を指定します。|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/Fr](fr-fr-create-dot-sbr-file.md)|ブラウザー ファイルを生成します。 **/Fr** は非推奨とされました。|
|[/FS](fs-force-synchronous-pdb-writes.md)|MSPDBSRV を使用してプログラムデータベース (PDB) ファイルへのすべての書き込みを強制的にシリアル化します。EXCEL.EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|[#using](../../preprocessor/hash-using-directive-cpp.md) ディレクティブに渡された場合と同じ方法でファイル名の使用を強制します。|
|[/Fx](fx-merge-injected-code.md)|挿入されたコードをソース ファイルとマージします。|
|[/GA](ga-optimize-for-windows-application.md)|Windows アプリケーション用にコードを最適化します。|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|`__cdecl` 呼び出し規約を使用します (x86 のみ)。|
|[/Ge](ge-enable-stack-probes.md)|非推奨。 スタック プローブをアクティブにします。|
|[/GF](gf-eliminate-duplicate-strings.md)|文字列プールを有効にします。|
|[/GH](gh-enable-pexit-hook-function.md)|フック関数 `_pexit`を呼び出します。|
|[/Gh](gh-enable-penter-hook-function.md)|フック関数 `_penter`を呼び出します。|
|[/GL](gl-whole-program-optimization.md)|プログラム全体の最適化を有効にします。|
|[/Gm](gm-enable-minimal-rebuild.md)|非推奨。 簡易リビルドを有効にします。|
|[/GR](gr-enable-run-time-type-information.md)|ランタイム型情報 (RTTI: Run-Time Type Information) を有効にします。|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|`__fastcall` 呼び出し規約を使用します (x86 のみ)。|
|[/GS](gs-buffer-security-check.md)|バッファーのセキュリティをチェックします。|
|[/Gs](gs-control-stack-checking-calls.md)|スタック プローブを制御します。|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|静的スレッド ローカル ストレージを使用して割り当てられたデータに対して、ファイバー保護をサポートします。|
|[/guard:cf](guard-enable-control-flow-guard.md)|制御フロー ガードのセキュリティ チェックを追加します。|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|`__vectorcall` 呼び出し規約を使用します。 (x86 と x64 のみ)。|
|[/Gw](gw-optimize-global-data.md)|プログラム全体のグローバル データの最適化を有効にします。|
|[/GX](gx-enable-exception-handling.md)|非推奨。 同期例外処理を有効にします。 代わりに [/EH](eh-exception-handling-model.md) を使用してください。|
|[/Gy](gy-enable-function-level-linking.md)|関数レベルのリンクを有効にします。|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|非推奨。 [/RTC1](rtc-run-time-error-checks.md)と同じです。|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|`__stdcall` 呼び出し規約を使用します (x86 のみ)。|
|[/H](h-restrict-length-of-external-names.md)|非推奨。 外部名 (パブリック名) の長さを制限します。|
|[/HELP](help-compiler-command-line-help.md)|コンパイラ オプションのリストを出力します。|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|関数の実行に入ったときに、レジスタで渡されたパラメーターを、強制的にスタック内のその場所に書き込みます。 このコンパイラオプションは、x64 コンパイラ (ネイティブコンパイルおよびクロスコンパイル) に対してのみ使用できます。|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|ホットパッチ可能なイメージを作成します。|
|[/I](i-additional-include-directories.md)|ディレクトリ内でインクルード ファイルを検索します。|
|[/J](j-default-char-type-is-unsigned.md)|既定の `char` 型を変更します。|
|[/JMC](jmc.md)|ネイティブC++マイコードのみデバッグをサポートします。|
|[/kernel](kernel-create-kernel-mode-binary.md)|コンパイラとリンカーは、Windows カーネルで実行可能なバイナリを作成します。|
|[/LD](md-mt-ld-use-run-time-library.md)|ダイナミック リンク ライブラリを作成します。|
|[/LDd](md-mt-ld-use-run-time-library.md)|デバッグ バージョンのダイナミック リンク ライブラリを作成します。|
|[/link](link-pass-options-to-linker.md)|指定したオプションを LINK に渡します。|
|[/LN](ln-create-msil-module.md)|MSIL モジュールを作成します。|
|[/MD](md-mt-ld-use-run-time-library.md)|MSVCRT.lib を使用して、マルチスレッド DLL を作成します。|
|[/MDd](md-mt-ld-use-run-time-library.md)|MSVCRTD.lib を使用して、デバッグ バージョンのマルチスレッド DLL を作成します。|
|[/MP](mp-build-with-multiple-processes.md)|複数のプロセスを使用して、複数のソース ファイルをコンパイルします。|
|[/MT](md-mt-ld-use-run-time-library.md)|LIBCMT.lib を使用して、マルチスレッド実行可能ファイルを作成します。|
|[/MTd](md-mt-ld-use-run-time-library.md)|LIBCMTD.lib を使用して、デバッグ バージョンのマルチスレッド実行可能ファイルを作成します。|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|著作権情報を表示しません。|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|コードを最小化します。|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|コードを最速化します。|
|[/Ob](ob-inline-function-expansion.md)|関数のインライン展開を制御します。|
|[/Od](od-disable-debug.md)|最適化を無効にします。|
|[/Og](og-global-optimizations.md)|非推奨。 グローバル最適化を使用します。|
|[/Oi](oi-generate-intrinsic-functions.md)|組み込み関数を生成します。|
|[/openmp](openmp-enable-openmp-2-0-support.md)|ソースコードで[`#pragma omp`](../../preprocessor/omp.md)ディレクティブを有効にします。|
|[/Os](os-ot-favor-small-code-favor-fast-code.md)|実行可能ファイルで、サイズの小ささを優先させます。|
|[/Ot](os-ot-favor-small-code-favor-fast-code.md)|実行可能ファイルで、実行速度を優先させます。|
|[/Ox](ox-full-optimization.md)|/GF または/gyを含まない/O2 のサブセット。|
|[/Oy](oy-frame-pointer-omission.md)|フレーム ポインターを省略します (x86 のみ)。|
|[/P](p-preprocess-to-a-file.md)|プリプロセッサ出力をファイルに書き込みます。|
|[/permissive-](permissive-standards-conformance.md)|標準準拠モードを設定します。|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|高速超越関数を生成します。|
|[/QIfist](qifist-suppress-ftol.md)|非推奨。 浮動小数点型から整数型への変換が必要なときに、 `_ftol` を呼び出しません (x86 のみ)。|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|`fwait` ブロックの中にある `try` コマンドを削除します。|
|[/QIntel-jcc-erratum](qintel-jcc-erratum.md)|Intel JCC erratum マイクロコード更新のパフォーマンスへの影響を軽減します。|
|[/Qpar (自動並行化)](qpar-auto-parallelizer.md)|[#pragma loop()](../../preprocessor/loop.md) ディレクティブでマークされているループの自動並列化を有効にします。|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|浮動小数点値の整数移動命令を使用し、特定の浮動小数点読み込み最適化を無効にします。|
|[/Qspectre](qspectre.md)|特定のスペクター バリアント 1 のセキュリティ脆弱性を軽減するコンパイラの命令生成を指定します。|
|[/Qspectre-load](qspectre-load.md)|ロード命令に基づいて Spectre のセキュリティ脆弱性を軽減するための命令をシリアル化するためのコンパイラの生成を指定します。|
|[/Qspectre-load-cf](qspectre-load-cf.md)|メモリを読み込む制御フロー命令に基づいて、Spectre のセキュリティ脆弱性を軽減するための命令をシリアル化するためのコンパイラの生成を指定します。|
|[/Qvec-report (自動ベクター化レポート作成レベル)](qvec-report-auto-vectorizer-reporting-level.md)|自動ベクター化のレポート レベルを有効にします。|
|[/RTC](rtc-run-time-error-checks.md)|ランタイム エラー チェックを有効にします。|
|[/sdl](sdl-enable-additional-security-checks.md)|追加のセキュリティ機能と警告を有効にします。|
|[/showIncludes](showincludes-list-include-files.md)|コンパイル時にインクルード ファイルの一覧を表示します。|
|[/source-charset](source-charset-set-source-character-set.md)|ソース文字セットを設定します。|
|[/std](std-specify-language-standard-version.md)|C++標準バージョン互換性セレクター。|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|C ソース ファイルを指定します。|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|すべてのソースファイルが C であることを指定します。|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|C++ ソース ファイルを指定します。|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|すべてのソースファイルがC++であることを指定します。|
|[/U](u-u-undefine-symbols.md)|1 つの定義済みマクロを削除します。|
|[/u](u-u-undefine-symbols.md)|すべての定義済みマクロを削除します。|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|ソース文字セットと実行文字セットを UTF-8 に設定します。|
|[/V](v-version-number.md)|非推奨。 .obj ファイル バージョン文字列を設定します。|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|互換性のある文字に対してのみ UTF-8 ファイルを検証します。|
|[/vd](vd-disable-construction-displacements.md)|隠し vtordisp クラス メンバーの無効と有効を切り替えます。|
|[/vmb](vmb-vmg-representation-method.md)|メンバーへのポインターに対して、最適なクラスを使用します。|
|[/vmg](vmb-vmg-representation-method.md)|メンバーへのポインターに対して、ジェネリック クラスを使用します。|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|多重継承を宣言します。|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|単一継承を宣言します。|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|仮想継承を宣言します。|
|[/volatile](volatile-volatile-keyword-interpretation.md)|volatile キーワードの解釈方法を選択します。|
|[/w](compiler-option-warning-level.md)|すべての警告を無効にします。|
|[/W0、/W1、/W2、/W3、/W4](compiler-option-warning-level.md)|出力する警告レベルを設定します。|
|[/w1、/w2、/w3、/w4](compiler-option-warning-level.md)|指定した警告の警告レベルを設定します。|
|[/Wall](compiler-option-warning-level.md)|既定で無効にされた警告も含めてすべての警告を有効にします。|
|[/wd](compiler-option-warning-level.md)|指定した警告を無効にします。|
|[/we](compiler-option-warning-level.md)|指定した警告をエラーとして扱います。|
|[/WL](wl-enable-one-line-diagnostics.md)|コマンド ラインから C++ ソース コードをコンパイルするときに、エラー メッセージと警告メッセージの 1 行診断を有効にします。|
|[/wo](compiler-option-warning-level.md)|指定した警告を 1 回だけ表示します。|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|互換性のために残されています。 64 ビット移植性の問題を検出します。|
|[/Wv](compiler-option-warning-level.md)|指定したコンパイラ バージョンの後に、導入された警告は表示されません。|
|[/WX](compiler-option-warning-level.md)|すべての警告をエラーとして扱います。|
|[/X](x-ignore-standard-include-paths.md)|標準のインクルード ディレクトリを無視します。|
|[/Y-](y-ignore-precompiled-header-options.md)|現在のビルドで、他のすべてのプリコンパイル済みヘッダー コンパイラ オプションを無視します。|
|[/Yc](yc-create-precompiled-header-file.md)|プリコンパイル済みヘッダー ファイルを作成します。|
|[/Yd](yd-place-debug-information-in-object-file.md)|非推奨。 すべてのオブジェクト ファイルに、詳細なデバッグ情報を取り込みます。 代わりに [/Zi](z7-zi-zi-debug-information-format.md) を使用してください。|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|デバッグ ライブラリの作成時に PCH の参照を挿入します。|
|[/Yu](yu-use-precompiled-header-file.md)|ビルド時にプリコンパイル済みヘッダー ファイルを使用します。|
|[/Z7](z7-zi-zi-debug-information-format.md)|C 7.0 互換のデバッグ情報を生成します。|
|[/Za](za-ze-disable-language-extensions.md)|言語拡張機能を無効にします。|
|[/Zc](zc-conformance.md)|[/Ze](za-ze-disable-language-extensions.md)の標準動作を指定します。[/Za、/ze (言語拡張機能の無効化)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|非推奨。 言語拡張機能を有効にします。|
|[/Zf](zf.md)|並列ビルドでの PDB 生成時間を改善します。|
|[/Zg](zg-generate-function-prototypes.md)|Visual Studio 2015 で削除されました。 関数プロトタイプを生成します。|
|[/ZH](zh.md)|デバッグ情報のチェックサムに MD5、SHA-1、または SHA-256 を指定します。|
|[/ZI](z7-zi-zi-debug-information-format.md)|エディット コンティニュと互換性のあるプログラム データベースにデバッグ情報を含めます。|
|[/Zi](z7-zi-zi-debug-information-format.md)|詳細なデバッグ情報を生成します。|
|[/Zl](zl-omit-default-library-name.md)|.obj ファイルから既定のライブラリ名を削除します (x86 のみ)。|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|プリコンパイル済みヘッダーのメモリ割り当て制限を指定します。|
|[/Zo](zo-enhance-optimized-debugging.md)|最適化されたコードの強化されたデバッグ情報を生成します。|
|[/Zp](zp-struct-member-alignment.md)|構造体メンバーをパックします。|
|[/Zs](zs-syntax-check-only.md)|構文だけをチェックします。|
|[/ZW](zw-windows-runtime-compilation.md)|Windows ランタイムで実行する出力ファイルを作成します。|

## <a name="see-also"></a>参照

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
