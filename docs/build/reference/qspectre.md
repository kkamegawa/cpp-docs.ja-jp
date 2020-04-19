---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e8d03075a980a9b9c345ce351413e39a3c3444cb
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808834"
---
# <a name="qspectre"></a>/Qspectre

特定のスペクター バリアント 1 のセキュリティ脆弱性を軽減するコンパイラの命令生成を指定します。

## <a name="syntax"></a>構文

> **/Qspectre**

## <a name="remarks"></a>Remarks

**/Qspectre** オプションは、Visual Studio 2017 バージョン 15.5.5 以降、および Visual Studio 2015 Update 3 から [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre) で使用できます。 指定すると、コンパイラによって特定の[スペクター セキュリティ脆弱性](https://spectreattack.com/spectre.pdf)を軽減する命令が挿入されます。 これらの脆弱性は、予測*実行のサイドチャネル攻撃*と呼ばれます。 多くのオペレーティングシステムと最新のプロセッサ (Intel、AMD、ARM のプロセッサを含む) に影響します。

**/Qspectre** オプションは既定ではオフです。

最初のリリースでは、 **/Qspectre** オプションは最適化されたコードに対してのみ機能しました。 Visual Studio 2017 バージョン 15.7 以降では、 **/Qspectre** オプションはすべての最適化レベルでサポートされています。

スペクターの軽減策を含むバージョンの Microsoft Visual C++ ライブラリもリリースされています。 Visual Studio 2017 以降用のスペクター軽減済みライブラリは、Visual Studio インストーラーでダウンロードできます。 これらは、 **[コンパイラ、ビルドツール、およびランタイム]** の **[個々のコンポーネント]** タブにあり、名前に "lib for Spectre" があります。 軽減策が有効な DLL および静的ランタイム ライブラリのいずれも、次の Visual C++ ランタイムのサブセットに使用できます。VC++ のスタートアップ コード、vcruntime140、msvcp140、concrt140、および vcamp140。 Dll は、アプリケーションローカル配置でのみサポートされています。 再頒布可能な Visual C++ 2017 以降のランタイムライブラリの内容は変更されていません。

また、MFC および ATL 用の Spectre 軽減ライブラリをインストールすることもできます。 **Sdk、ライブラリ、およびフレームワーク**の **[個々のコンポーネント]** タブにあります。

> [!NOTE]
> ユニバーサル Windows (UWP) アプリまたはコンポーネント用の Spectre ライブラリのバージョンはありません。 このようなライブラリのアプリローカル展開はできません。

### <a name="applicability"></a>適用条件

コードが信頼境界を越えるデータを操作する場合は、 **/Qspectre**オプションを使用してコードをリビルドして再デプロイし、できるだけ早くこの問題を軽減することをお勧めします。 このようなコードの例としては、実行に影響を与える信頼できない入力を読み込むコードがあります。 たとえば、リモートプロシージャ呼び出しを行ったり、信頼されていない入力またはファイルを解析したり、他のローカルのプロセス間通信 (IPC) インターフェイスを使用したりするコードです。 標準的なサンドボックスの手法では不十分な場合があります。 コードが信頼境界を越えることがないことを判断する前に、サンドボックスを慎重に調査してください。

### <a name="availability"></a>対象

**/Qspectre**オプションは、Visual Studio 2017 バージョン15.5.5、および2018年1月23日以降C++に作成された Microsoft コンパイラ (MSVC) のすべての更新プログラムで使用できます。 Visual Studio インストーラーを使用してコンパイラを更新し、スペクター軽減済みライブラリを個別のコンポーネントとしてインストールします。 **/Qspectre** オプションは、修正プログラムを介して Visual Studio 2015 Update 3 でも利用できます。 詳細については、[KB 4338871](https://support.microsoft.com/help/4338871) を参照してください。

すべてのバージョンの Visual Studio 2017 バージョン15.5、および Visual Studio 2017 バージョン15.6 のすべてのプレビュー。 ドキュメントに記載のないオプション **/d2guardspecload**を含めます。 これは、 **/Qspectre**の初期動作と同じです。 これらのバージョンのコンパイラでは、 **/d2guardspecload** を使用してコードに同じ軽減策を適用できます。 オプションをサポートするコンパイラで **/Qspectre**を使用するようにビルドを更新することをお勧めします。 **/Qspectre**オプションでは、新しいバージョンのコンパイラで新しい軽減策をサポートすることもできます。

### <a name="effect"></a>効果

**/Qspectre** オプションを指定すると、スペクター バリアント 1 の Bounds Check Bypass ([CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753)) を軽減するコードが出力されます。 これは、投機的コード実行バリアとして動作する命令を挿入することで機能します。 プロセッサの投機の軽減に使用される具体的な命令は、プロセッサとそのマイクロアーキテクチャによって異なり、今後のバージョンのコンパイラでは変更される可能性があります。

**/Qspectre**オプションを有効にすると、コンパイラは、予測実行が境界チェックをバイパスする可能性のあるインスタンスを識別しようとします。 ここで、バリア命令を挿入します。 コンパイラがバリアント1のインスタンスを識別するために実行できる分析の制限に注意することが重要です。 そのため、バリアント1の可能なすべてのインスタンスが **/Qspectre**の下でインストルメント化されるという保証はありません。

### <a name="performance-impact"></a>パフォーマンスへの影響

**/Qspectre**のパフォーマンスへの影響は、いくつかのサイズの大きいコードベースではごくわずかです。 ただし、 **/Qspectre**のコードのパフォーマンスが影響を受けないことは保証されません。 このオプションがパフォーマンスに与える影響を判断するには、コードのベンチマークを実行することをお勧めします。 パフォーマンスクリティカルなブロックまたはループで軽減策が必要ないことがわかっている場合は、 [__declspec (spectre (nomitigation))](../../cpp/spectre.md)ディレクティブを使用して、軽減策を選択的に無効にすることができます。 このディレクティブは、 **/d2guardspecload**オプションのみをサポートするコンパイラでは使用できません。

### <a name="required-libraries"></a>必要なライブラリ

**/Qspectre**コンパイラオプションは、Spectre の緩和策を提供するために構築されたランタイムライブラリのバージョンを暗黙的にリンクするコードを生成します。 これらのライブラリは省略可能なコンポーネントであり、Visual Studio インストーラーを使用してインストールする必要があります。

- MSVC version *version_numbers* Libs for Spectre \[(x86 and x64) | (ARM) | (ARM64)]
- Visual C++ ATL for \[(x86/x64) | ARM | ARM64] with Spectre Mitigations
- Visual C++ MFC for \[x86/x64 | ARM | ARM64] with Spectre Mitigations

**/Qspectre**を使用してコードをビルドし、これらのライブラリがインストールされて**いない場合、ビルドシステムは警告 MSB8038 を報告します。Spectre mitigation is enabled but Spectre mitigated libraries are not found"(警告 MSB8038: スペクターの軽減策は有効ですが、スペクター軽減済みライブラリが見つかりません)** が報告されます。 MFC または ATL コードのビルドに失敗し、リンカーが致命的なエラー LNK1104 などのエラーを報告した場合 **: ファイル ' oldnames. lib ' を開くことができません**。これらの不足しているライブラリが原因である可能性があります。

### <a name="additional-information"></a>追加情報

詳細については、Microsoft の公式の[セキュリティアドバイザリ ADV180002、予測実行のサイドチャネルの脆弱性を軽減するためのガイダンス](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)を参照してください。 Intel の「[Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)」(投機的実行サイド チャネルの軽減策) と ARM の「[Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf)」(キャッシュ投機的サイドチャネル) のガイダンスも利用できます。 Spectre と Meltdown の緩和策の Windows 固有の概要については、「 [Windows システムでの Spectre と Meltdown の緩和のパフォーマンスへの影響につい](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/)て」を参照してください。 MSVC の軽減策によって解決される Spectre 脆弱性の概要については、 C++チームブログの「 [MSVC の Spectre 軽減策](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./)」を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

::: moniker range="vs-2019"

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] [ **CC++ /** > **コード生成**] プロパティページを選択します。

1. **Spectre 軽減**プロパティの新しい値を選択します。 **[OK]** を選択して変更を適用します。

::: moniker-end

::: moniker range="<=vs-2017"

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **構成プロパティ** > **C/C++** > **コマンドライン** プロパティページを選択します。

1. **[追加のオプション]** ボックスに **/Qspectre** コンパイラ オプションを入力します。 **[OK]** を選択して変更を適用します。

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](q-options-low-level-operations.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
