---
title: MSVC リンカーオプション
description: Microsoft LINK リンカーでサポートされているオプションの一覧。
ms.date: 02/09/2020
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 12710aff1cf833e277e48ab2f13abc702c7d6c14
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257547"
---
# <a name="linker-options"></a>リンカー オプション

LINK.exe は、COFF (Common Object File Format) オブジェクト ファイルとライブラリをリンクし、実行可能ファイル (.exe) やダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) を生成します。

LINK.exe のオプションの一覧を次の表に示します。 LINK の詳細については、下記を参照してください。

- [Compiler-Controlled LINK Options](compiler-controlled-link-options.md)

- [LINK の入力ファイル](link-input-files.md)

- [LINK 出力](link-output.md)

- [予約語](reserved-words.md)

コマンドラインでは、リンカーオプションの大文字と小文字は区別されません。たとえば、`/base` と `/BASE` は同じことを意味します。 コマンド ラインまたは Visual Studio で各オプションを指定する方法の詳細については、そのオプションのドキュメントを参照してください。

[comment](../../preprocessor/comment-c-cpp.md) プラグマを使用して、一部のリンカー オプションを指定できます。

## <a name="linker-options-listed-alphabetically"></a>リンカーオプションの一覧 (アルファベット順)

|オプション|目的|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|応答ファイルを指定します。|
|[/ALIGN](align-section-alignment.md)|各セクションのアラインメントを指定します。|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|DLL をバインドできないことを指定します。|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|マニフェスト検索の動作を指定します。|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|アプリケーションが appcontainer プロセス環境内で実行される必要があるかどうかを指定します。|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|<xref:System.Diagnostics.DebuggableAttribute> をマネージド イメージに追加します。|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|マネージド リソースへのリンクを作成します。|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|MSIL (Microsoft Intermediate Language) モジュールをアセンブリにインポートする必要があることを指定します。|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|マネージド リソース ファイルをアセンブリに埋め込みます。|
|[/BASE](base-base-address.md)|プログラムのベース アドレスを設定します。|
|[/CGTHREADS](cgthreads-compiler-threads.md)|リンク時のコード生成を指定するときに、最適化およびコード生成に使用する cl.exe スレッド数を設定します。|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|CLR イメージの種類 (IJW、純粋、または安全) を設定します。|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|P/Invoke 機構を通じて呼び出された関数の最終エラー コードを保持します。|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|CLR プログラムのエントリ ポイントに適用するスレッド処理属性を指定します。|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|マネージド コードからネイティブ DLL への呼び出しを行う、リンカーによって生成された PInvoke スタブに、SuppressUnmanagedCodeSecurity 属性を適用するかどうかを指定します。|
|[/DEBUG](debug-generate-debug-info.md)|デバッグ情報を作成します。|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|デバッグ情報に含めるデータを指定します。|
|[/DEF](def-specify-module-definition-file.md)|モジュール定義 (.def) ファイルをリンカーに渡します。|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|外部参照を解決するときに、指定したライブラリを検索します。|
|[/DELAY](delay-delay-load-import-settings.md)|DLL の遅延読み込みを制御します。|
|[/DELAYLOAD](delayload-delay-load-import.md)|指定した DLL に遅延読み込みを発生させます。|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|アセンブリに部分署名します。|
|[/Dependentloadflag](dependentloadflag.md)|依存する DLL 読み込みに既定のフラグを設定します。|
|[/DLL](dll-build-a-dll.md)|DLL をビルドします。|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|カーネル モード ドライバーを作成します。|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|アドレス空間レイアウトのランダム化 (ASLR) 機能を使用して、読み込み時に再配置される実行可能イメージを生成するかどうかを指定します。|
|[/ENTRY](entry-entry-point-symbol.md)|開始アドレスを設定します。|
|[/ERRORREPORT](errorreport-report-internal-linker-errors.md)| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|[/EXPORT](export-exports-a-function.md)|関数をエクスポートします。|
|[/FILEALIGN](filealign.md)|出力ファイル内のセクションを指定した値の倍数に配置します。|
|[/FIXED](fixed-fixed-base-address.md)|指定のベース アドレスだけに読み込まれるプログラムを作成します。|
|[/FORCE](force-force-file-output.md)|未解決のシンボルまたは複数定義のシンボルがある場合でも、リンクを強制的に終了します。|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|ホット パッチ可能なイメージを作成します。|
|[/GENPROFILE、/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|これらのオプションは、ガイド付き最適化のプロファイル (PGO) をサポートするために、リンカーによる *`.pgd`* ファイルの生成を指定します。 /GENPROFILE と /FASTGENPROFILE は、それぞれに異なる既定のパラメーターを使用します。|
|[/GUARD](guard-enable-guard-checks.md)|制御フロー ガードによる保護を有効にします。|
|[/HEAP](heap-set-heap-size.md)|ヒープ サイズをバイト単位で設定します。|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|高エントロピの 64 ビット ASLR (Address Space Layout Randomization) のサポートを指定します。|
|[/IDLOUT](idlout-name-midl-output-files.md)|*`.idl`* ファイルの名前とその他の MIDL 出力ファイルを指定します。|
|[/IGNORE](ignore-ignore-specific-warnings.md)|指定されたリンカー警告の出力を抑制します。|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|*`.idl`* ファイルに属性情報を処理しないようにします。|
|[/IMPLIB](implib-name-import-library.md)|既定のインポート ライブラリ名をオーバーライドします。|
|[/INCLUDE](include-force-symbol-references.md)|シンボルを明示的に参照します。|
|[/INCREMENTAL](incremental-link-incrementally.md)|インクリメンタル リンクの処理方法を制御します。|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|モジュールが読み込み時に署名の確認を要求することを指定します。|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|アセンブリに署名するためのキー コンテナーを指定します。|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|アセンブリに署名するキーまたはキー ペアを指定します。|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|アプリケーションが 2 GB を超えるアドレスをサポートしていることをコンパイラに指定します。|
|[/LIBPATH](libpath-additional-libpath.md)|環境ライブラリ パスの前に検索するパスを指定します。|
|[/Link再現](linkrepro.md)|リンク再現アーティファクトを生成するパスを指定します。|
|[/Linkreprotarget](linkreprotarget.md)|指定されたターゲットを生成するときにのみ、リンク再現を生成します。<sup>16.1</sup>|
|[/LTCG](ltcg-link-time-code-generation.md)|リンク時のコード生成を指定します。|
|[/MACHINE](machine-specify-target-platform.md)|ターゲット プラットフォームを指定します。|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|side-by-side マニフェスト ファイルを作成し、バイナリに埋め込むことができるようにします。|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|マニフェストファイルの \<dependentAssembly > セクションを指定します。|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|マニフェスト ファイルの既定の名前を変更します。|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|リンカーが処理を行い、バイナリに埋め込むための、マニフェスト入力ファイルを指定します。 このオプションを複数回使用して、複数のマニフェストの入力ファイルを指定できます。|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|ユーザー アカウント制御 (UAC) 情報をプログラム マニフェストに組み込むかどうかを指定します。|
|[/MAP](map-generate-mapfile.md)|マップファイルを作成します。|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|指定した情報をマップ ファイルに格納します。|
|[/MERGE](merge-combine-sections.md)|セクションを結合します。|
|[/MIDL](midl-specify-midl-command-line-options.md)|MIDL コマンド ライン オプションを指定します。|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|デバッガービジュアライザーを Natvis ファイルからプログラムデータベース (PDB) に追加します。|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|.NET Framework アセンブリを作成しません。|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|外部参照を解決するときに、すべてのまたは指定した既定のライブラリを無視します。|
|[/NOENTRY](noentry-no-entry-point.md)|リソースだけの DLL を作成します。|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|開始メッセージを表示しません。|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Windows データ実行防止機能との互換性が確認済みとして実行可能ファイルをマークします。|
|[/OPT](opt-optimizations.md)|LINK の最適化を制御します。|
|[/ORDER](order-put-functions-in-order.md)|指定された順序で COMDAT をイメージに取り込みます。|
|[/OUT](out-output-file-name.md)|出力ファイル名を指定します。|
|[/PDB](pdb-use-program-database.md)|PDB ファイルを作成します。|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|別の場所を使用して PDB ファイルを保存します。|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|プライベートシンボルを持たない PDB ファイルを作成します。|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|ガイド付き最適化のプロファイル用の *`.pgd`* ファイルを指定します。|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**廃止**スレッドセーフな PGO によってインストルメント化されたビルドを作成します。|
|[/PROFILE](profile-performance-tools-profiler.md)|パフォーマンス ツール プロファイラーで使用できる出力ファイルを作成します。|
|[/RELEASE](release-set-the-checksum.md)|*`.exe`* ヘッダーにチェックサムを設定します。|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|安全な例外ハンドラーのテーブルがイメージに含まれるように指定します。|
|[/SECTION](section-specify-section-attributes.md)|セクションの属性をオーバーライドします。|
|[/SOURCELINK](sourcelink.md)|PDB に追加する SourceLink ファイルを指定します。|
|[/STACK](stack-stack-allocations.md)|スタック サイズをバイト単位で設定します。|
|[/STUB](stub-ms-dos-stub-file-name.md)|MS-DOS スタブ プログラムを Win32 プログラムにアタッチします。|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|*`.exe`* ファイルの実行方法をオペレーティングシステムに指示します。|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|リンカー出力をスワップファイルにコピーしてから実行するように、オペレーティングシステムに指示します。|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|リンカーによって生成されたタイプ ライブラリのリソース ID を指定します。|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|*`.tlb`* ファイルの名前とその他の MIDL 出力ファイルを指定します。|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|ターミナル サーバーでの実行専用のアプリケーションを作成します。|
|[/USEPROFILE](useprofile.md)|ガイド付き最適化のプロファイルのトレーニングデータを使用して、最適化されたイメージを作成します。|
|[/VERBOSE](verbose-print-progress-messages.md)|リンカーの進行状況メッセージを出力します。|
|[/VERSION](version-version-information.md)|バージョン番号を割り当てます。|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|指定されたスタティックライブラリのすべてのオブジェクトファイルを含みます。|
|[/WINMD](winmd-generate-windows-metadata.md)|Windows ランタイム メタデータ ファイルの生成を有効にします。|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|[/WINMD](winmd-generate-windows-metadata.md) のリンカー オプションによって生成される Windows のランタイム メタデータ (winmd) の出力ファイルの名前を指定します。|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Windows ランタイム メタデータに署名するキーまたはキー ペアを指定します。|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Windows メタデータ ファイルに署名するキー コンテナーを指定します。|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|winmd ファイルに公開キーを設定して、Windows のランタイム メタデータ (.winmd) ファイルに部分的に署名します。|
|[/WX](wx-treat-linker-warnings-as-errors.md)|リンカー警告をエラーとして扱います。|

<sup>16.1</sup>このオプションは、Visual Studio 2019 バージョン16.1 以降で使用できます。

## <a name="see-also"></a>参照

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)\
[MSVC リンカーのリファレンス](linking.md)
