---
title: /Z7、/Zi、/ZI (デバッグ情報の形式)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: e809c7af7465cde98db11eac8628b76d04f7e8b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316289"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI (デバッグ情報の形式)

オブジェクト ファイルまたはプログラム データベース (PDB) ファイルにこの情報を保持するかどうかのプログラム用に作成されるデバッグ情報の種類を指定します。

## <a name="syntax"></a>構文

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>Remarks

コードがコンパイルされ、デバッグ モードで構築された、ときに、コンパイラは関数と変数、型情報、および行番号の場所、デバッガーで使用するためのシンボル名を生成します。 このシンボリック デバッグ情報をコンパイラによって生成されたオブジェクト ファイル (.obj ファイル) または実行可能ファイルの別の PDB ファイル (.pdb ファイル) に含まれることはできます。  デバッグ情報の形式オプションは、次のセクションで説明します。

### <a name="none"></a>なし

既定では、デバッグ情報の形式オプションが指定されていない場合、コンパイラが生成されないデバッグについては、ためコンパイルが高速です。

### <a name="z7"></a>/Z7

**/Z7**オプションも、デバッガーで使用するための完全なシンボリック デバッグ情報が含まれているオブジェクト ファイルが生成されます。 これらのオブジェクト ファイルとビルドの実行可能ファイルは、デバッグ情報のないファイルよりも大幅に拡大できます。 シンボリック デバッグ情報には、変数や関数の名前と型、および行番号が含まれます。 PDB ファイルは生成されません。

サード パーティ製ライブラリのデバッグ バージョンのディストリビューターの場合、PDB ファイルを持たないことによる利点があります。 ただし、プリコンパイル済みヘッダーのオブジェクト ファイルは、ライブラリのリンク フェーズ中、およびデバッグに必要です。 使用する必要がある .pch オブジェクト ファイルの情報 (とコードなし) を入力のみが場合、 [/Yl (挿入 PCH 参照のライブラリのデバッグ)](yl-inject-pch-reference-for-debug-library.md)オプションは、ライブラリをビルドするときに、既定で有効にします。

非推奨とされる[/Gm (簡易リビルドの有効)](gm-enable-minimal-rebuild.md)場合オプションは使用できません **/Z7**を指定します。

### <a name="zi"></a>/ZI

**/Zi**オプションはすべて、シンボリック デバッグ情報を格納用に、デバッガーで別の PDB ファイルを生成します。 オブジェクト ファイルにデバッグ情報が含まれていないか、実行可能なものになりますかなり小さくなります。

使用 **/Zi**の最適化には影響しません。 ただし、 **/Zi**わけでは **/debug**; を参照してください[/DEBUG (デバッグ情報の生成)](debug-generate-debug-info.md)詳細についてはします。

両方を指定すると **/Zi**と **/clr**、<xref:System.Diagnostics.DebuggableAttribute>属性がアセンブリのメタデータには配置されません。 場合は、ソース コードで指定する必要があります。 この属性は、アプリケーションの実行時パフォーマンスに影響します。 方法の詳細については**Debuggable**属性がパフォーマンスに影響し、パフォーマンスに与える影響を変更する方法を参照してください。[デバッグをイメージの簡略化する](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)します。

PDB ファイルの名前、コンパイラ*プロジェクト*.pdb。 プロジェクトの外側でファイルをコンパイルする場合、コンパイラは、VC をという名前の PDB ファイルを作成*x*、.pdb、 *x*は使用中で、コンパイラのバージョンのメジャーおよびマイナー バージョン番号の連結になります。 コンパイラは、このオプションは、デバッガーを指すシンボリックと行番号の情報の場所を使用して作成された各オブジェクト ファイル内の名前、PDB と識別のタイムスタンプの署名を埋め込みます。 PDB ファイル内の署名と名前は、デバッガーに読み込まれるシンボルの実行可能ファイルと一致する必要があります。 WinDBG デバッガーを使用して一致しないシンボルを読み込むことができます、`.symopt+0x40`コマンド。 Visual Studio には、一致しないシンボルを読み込むようなオプションはありません。

使用してコンパイルされたオブジェクトからライブラリを作成するかどうかは **/Zi**プログラムにライブラリがリンクされている場合に、関連付けられた .pdb ファイルが使用可能なにある必要があります。 したがって、ライブラリを配布する場合は、PDB ファイルも配布する必要があります。 PDB ファイルを使用せずにデバッグ情報を含むライブラリを作成することを選択する必要があります、 **/Z7**オプション。 プリコンパイル済みヘッダー オプションを使用すると、PDB ファイルでプリコンパイル済みヘッダーとソース コードの残りの部分の両方のデバッグ情報は配置されます。

### <a name="zi"></a>/ZI

**/ZI**オプションはのような **/Zi**をサポートする形式での PDB ファイルが生成されますが、[エディット コンティニュ](/visualstudio/debugger/edit-and-continue-visual-cpp)機能します。 エディット コンティニュのデバッグ機能を使用するには、このオプションを使用する必要があります。 エディット コンティニュの機能は開発者の生産性、便利ですが、サイズ、パフォーマンス、およびコンパイラの準拠をコードで問題が発生することができます。 使用しているため、ほとんどの最適化は、エディット コンティニュと互換性がない、 **/ZI**無効になります`#pragma optimize`ステートメントをコードにします。 **/ZI**オプションは、またの使用と互換性のある、 [ &#95;&#95;行&#95;&#95;定義済みマクロが](../../preprocessor/predefined-macros.md); のコードをコンパイル **/ZI** を使用することはできません **&#95;&#95;行&#95;&#95;** 非型テンプレート引数としてが **&#95;&#95;行&#95;&#95;** マクロの展開で使用できます。

**/ZI**オプションを有効にどちらも、 [/Gy (関数レベルのリンクの有効にする)](gy-enable-function-level-linking.md)と[/FC (完全なソース コード ファイルのパスで診断)](fc-full-path-of-source-code-file-in-diagnostics.md)コンパイル時に使用するオプション。

**/ZI**と互換性がない[/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md)します。

> [!NOTE]
> **/ZI**オプションは、x86 および x64 プロセッサを対象とするコンパイラで使用できるのみ、このコンパイラ オプションは ARM プロセッサを対象とするコンパイラで使用できません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 開く、**構成プロパティ** > **C/C++** > **全般**プロパティ ページ。

1. 変更、**デバッグ情報の形式**プロパティ。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)

