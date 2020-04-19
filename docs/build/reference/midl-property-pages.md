---
title: MIDL コンパイラプロパティページ
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: e9c9cb75d326642c86405992a4bf9d7da9e578df
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927688"
---
# <a name="midl-property-pages"></a>[MIDL] プロパティ ページ

MIDL プロパティページは、の項目プロパティとして使用できます。COM を使用するC++プロジェクト内の IDL ファイル。 それらを使用して[MIDL コンパイラ](/windows/win32/midl/using-the-midl-compiler-2)を構成します。 C++ プロジェクト用の MIDL オプションにプログラムでアクセスする方法の詳細については、<xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> オブジェクトに関するページを参照してください。 「[一般的な MIDL コマンドライン構文](/windows/win32/midl/general-midl-command-line-syntax)」も参照してください。

## <a name="general-property-page"></a>[全般] プロパティページ

### <a name="preprocessor-definitions"></a>プリプロセッサの定義

MIDL マクロ ([/d](/windows/win32/midl/-d))\[マクロ\]を含め、1つまたは複数の定義を指定します。

### <a name="additional-include-directories"></a>追加のインクルード ディレクトリ

インクルードパス ([/i](/windows/win32/midl/-i)\[パス\]) に追加する1つ以上のディレクトリを指定します。

### <a name="additional-metadata-directories"></a>追加のメタデータディレクトリ

Windows の WinMD ファイル ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[path\]) が格納されているディレクトリを指定します。

### <a name="enable-windows-runtime"></a>Windows ランタイムを有効にする

Windows メタデータファイル ([winrt](/windows/win32/midl/-winrt)) を作成するための Windows ランタイムセマンティクスを有効にします。

### <a name="ignore-standard-include-path"></a>標準インクルードパスを無視する

現在のディレクトリとインクルードディレクトリを無視します ([/no_def_idir](/windows/win32/midl/-no-def-idir))。

### <a name="mktyplib-compatible"></a>MkTypLib 互換

Mktyplib バージョン 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)) との互換性を強制します。

### <a name="warning-level"></a>警告レベル

MIDL コードエラーの厳格度 ([/w](/windows/win32/midl/-w)) を選択します。

**いずれ**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>[警告をエラーとして扱う]

MIDL ですべての警告をエラーとして扱う ([/wx](/windows/win32/midl/-wx)) ことができます。

### <a name="suppress-startup-banner"></a>著作権情報の非表示

著作権情報メッセージ ([/nologo](/windows/win32/midl/-nologo)) の表示を抑制します。

### <a name="c-compiler-char-type"></a>C コンパイラの Char 型

生成されたコードをコンパイルするために使用される C コンパイラの既定の文字型を指定します。 ([/文字](/windows/win32/midl/-char)符号付き | unsigned | ascii7)。

**いずれ**

- **signed** - 符号あり
- **unsigned** - 符号なし
- **Ascii** -ascii

### <a name="target-environment"></a>対象の環境

ターゲットにする環境を指定します ([/env](/windows/win32/midl/-env) arm32 | win32 | ia64 | x64)。

**いずれ**

- **設定なし**-Win32
- **Microsoft Windows 32-bit** -Win32
- **Itanium の Microsoft Windows 64-bit** -IA64
- **Microsoft WINDOWS arm** -arm
- **Microsoft WINDOWS ARM64** -ARM64
- **Microsoft Windows 64-bit on x64** -x64

### <a name="generate-stubless-proxies"></a>スタブレスプロキシの生成

オブジェクトインターフェイス ([/Oicf](/windows/win32/midl/-oi)、 [/Oif](/windows/win32/midl/-oi) ) の拡張機能とスタブレスプロキシを使用して、完全に解釈されたスタブを生成します。

### <a name="suppress-compiler-warnings"></a>コンパイラ警告の非表示

コンパイラの警告メッセージ ([/no_warn](/windows/win32/midl/-no-warn)) を非表示にします。

### <a name="application-configuration-mode"></a>アプリケーション構成モード

IDL ファイル ([/appconfig](/windows/win32/midl/-app-config)) で選択した acf 属性を許可します。

### <a name="locale-id"></a>ロケール ID

入力ファイルの LCID、ファイル名、およびディレクトリパス ([/Lcid](/windows/win32/midl/-lcid) DECIMAL) を指定します。

### <a name="multi-processor-compilation"></a>マルチプロセッサコンパイル

複数のインスタンスを同時に実行します。

## <a name="output-property-page"></a>[出力] プロパティページ

### <a name="output-directory"></a>出力ディレクトリ

出力ディレクトリ ([/out](/windows/win32/midl/-out) [ディレクトリ]) を指定します。

### <a name="metadata-file"></a>メタデータファイル

生成されたメタデータファイルの名前 ([/winmd](/windows/win32/midl/-winmd)ファイル名) を指定します。

### <a name="header-file"></a>ヘッダーファイル

生成されるヘッダーファイルの名前を指定します ([/h](/windows/win32/midl/-h)ファイル名)。

### <a name="dlldata-file"></a>DllData ファイル

DLLDATA ファイル ([/dlldata](/windows/win32/midl/-dlldata)ファイル名) の名前を指定します。

### <a name="iid-file"></a>IID ファイル

インターフェイス識別子ファイル ([iid](/windows/win32/midl/-iid)ファイル名) の名前を指定します。

### <a name="proxy-file"></a>プロキシファイル

プロキシファイルの名前 ([/プロキシ](/windows/win32/midl/-proxy)ファイル名) を指定します。

### <a name="generate-type-library"></a>タイプライブラリの生成

タイプライブラリを生成しないように指定します ([/notlb] (いいえ))。

### <a name="type-library"></a>タイプライブラリ

タイプライブラリファイルの名前を指定します ([/tlb](/windows/win32/midl/-tlb)ファイル名)。

### <a name="generate-client-stub-files"></a>クライアントスタブファイルの生成

クライアントスタブファイルのみを生成します ([/client](/windows/win32/midl/-client) [スタブ | なし])。

**いずれ**

- **スタブ**スタブ
- **なし**-なし

### <a name="generate-server-stub-files"></a>サーバースタブファイルの生成

サーバースタブファイルのみを生成します ([/server](/windows/win32/midl/-server) [スタブ | なし])。

**いずれ**

- **スタブ**スタブ
- **なし**-なし

### <a name="client-stub-file"></a>クライアントスタブファイル

クライアントスタブファイルを指定します ([/cスタブ](/windows/win32/midl/-cstub)[ファイル])。

### <a name="server-stub-file"></a>サーバースタブファイル

サーバースタブファイル ([/sstub](/windows/win32/midl/-sstub) [ファイル]) を指定します。

### <a name="type-library-format"></a>タイプライブラリ形式

タイプライブラリファイル形式を指定します ([/oldtlb |/newtlb])。

**いずれ**

- **Newformat** -新しい形式
- **Oldformat** -old 形式

## <a name="advanced-property-page"></a>[詳細設定] プロパティページ

### <a name="c-preprocess-options"></a>C 前処理オプション

C コンパイラプリプロセッサ ([/cppopt](/windows/win32/midl/-cpp-opt)スイッチ) に渡すスイッチを指定します。

### <a name="undefine-preprocessor-definitions"></a>指定したプリプロセッサ定義の無効化

MIDL マクロ ([/u](/windows/win32/midl/-U) [マクロ]) を含め、1つ以上の未定義を指定します。

### <a name="enable-error-checking"></a>エラーチェックを有効にする

エラーチェックオプションを選択します ([/エラーすべて | なし])。

**いずれ**

- **EnableCustom** -すべて
- **すべて**-すべて
- **なし**-なし

### <a name="check-allocations"></a>割り当ての確認

メモリ不足エラーをチェックします ([/エラー](/windows/win32/midl/-error)割り当て)。

### <a name="check-bounds"></a>範囲のチェック

[サイズと転送の長さの指定] ([/エラー](/windows/win32/midl/-error) bounds_check) を確認します。

### <a name="check-enum-range"></a>列挙型の範囲のチェック

列挙値が許容範囲内であることを確認してください ([/エラー](/windows/win32/midl/-error)列挙型)。

### <a name="check-reference-pointers"></a>参照ポインターの確認

参照ポインターが null 以外 ([/エラー](/windows/win32/midl/-error)参照) であることを確認してください。

### <a name="check-stub-data"></a>スタブデータのチェック

サーバー側のスタブデータの有効性について追加のチェックを生成します ([/error](/windows/win32/midl/-error) stub_data)。

### <a name="prepend-with-abi-namespace"></a>' ABI ' 名前空間を先頭に付ける

' ABI ' 名前空間をすべての型に先頭に付加します。  ([nsプレフィックス](/windows/win32/midl/-ns-prefix))。

### <a name="validate-parameters"></a>パラメーターの検証

パラメーターを検証するための追加情報を生成します ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust))。

### <a name="struct-member-alignment"></a>構造体メンバーのアラインメント

ターゲットシステム (/ZpN) 内の構造体のパッキングレベルを指定します。

**いずれ**

- **設定されて**いません-設定されていません
- **1 バイト**-Zp1
- **2 バイト**Zp2
- **4 バイト**-Zp4
- **8 バイト**-Zp8

### <a name="redirect-output"></a>出力のリダイレクト

画面からファイル ([/o](/windows/win32/midl/-o)ファイル) に出力をリダイレクトします。

### <a name="minimum-target-system"></a>最小ターゲットシステム

最小のターゲットシステム ([/Target](/windows/win32/midl/-target) STRING) を設定します。



