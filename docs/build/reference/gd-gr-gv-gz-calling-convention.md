---
title: /Gd、/Gr、/Gv、/Gz (呼び出し規約)
ms.date: 09/05/2018
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: eabb4e11715e03745e27911ccd654568d70b8352
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400498"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd、/Gr、/Gv、/Gz (呼び出し規約)

これらのオプションでは、関数の引数をスタックにプッシュする順序、呼び出し元と呼び出し先のどちらの関数が呼び出しの最後にスタックから引数を削除するか、および個々の関数を識別するためにコンパイラが使用する名前装飾規約を決定します。

## <a name="syntax"></a>構文

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**

## <a name="remarks"></a>Remarks

**/Gd** では、[__stdcall](../../cpp/stdcall.md)、[__fastcall](../../cpp/fastcall.md)、または [__vectorcall](../../cpp/vectorcall.md) が指定されている関数と C++ メンバー関数を除く、すべての関数の [__cdecl](../../cpp/cdecl.md) 呼び出し規約を指定します。これは既定の設定です。

**/Gr** では、C++ メンバー関数、`main` という名前の関数、および `__cdecl`、`__stdcall`、または `__vectorcall` が指定されている関数を除く、すべての関数の `__fastcall` 呼び出し規約を指定します。 すべての `__fastcall` 関数には、プロトタイプ宣言が必要です。 この呼び出し規約は、x86 を対象とするコンパイラでのみ使用され、他のアーキテクチャを対象とするコンパイラでは無視されます。

**/Gz** では、C++ メンバー関数、`main` という名前の関数、および `__cdecl`、`__fastcall`、または `__vectorcall` が指定されている関数を除く、すべての関数の `__stdcall` 呼び出し規約を指定します。 すべての `__stdcall` 関数には、プロトタイプ宣言が必要です。 この呼び出し規約は、x86 を対象とするコンパイラでのみ使用され、他のアーキテクチャを対象とするコンパイラでは無視されます。

**/Gv**を指定します、`__vectorcall`を除くすべての関数の呼び出し規約をC++メンバー関数、関数の名前付き`main`、関数、`vararg`可変個引数リスト、または競合するいるとマークされている関数`__cdecl`、 `__stdcall`、または`__fastcall`属性。 この呼び出し規約は、/arch:SSE2 以上をサポートする x86 アーキテクチャおよび x64 アーキテクチャのみで使用され、ARM アーキテクチャを対象とするコンパイラでは無視されます。

可変数の引数を受け取る関数には `__cdecl` が指定されている必要があります。

**/Gd**、 **/Gr**、 **/Gv**、および **/Gz** は、[/clr:safe](clr-common-language-runtime-compilation.md) または **/clr:pure** と互換性がありません。 **/clr:pure** および **/clr:safe** コンパイラ オプションは Visual Studio 2015 では非推奨とされており、Visual Studio 2017 以降ではサポートされていません。

> [!NOTE]
> 既定では、x86 プロセッサの場合、C++ メンバー関数では [__thiscall](../../cpp/thiscall.md) が使用されます。

すべてのプロセッサで、`__cdecl`、`__fastcall`、`__vectorcall`、または `__stdcall` のいずれかとして明示的に指定されているメンバー関数では、指定の呼び出し規約が使用されます (そのアーキテクチャで無視されない場合)。 可変個の引数を取るメンバー関数では、常に `__cdecl` 呼び出し規約が使われます。

これのコンパイラ オプションを指定しても、C++ のメソッドや関数の名前装飾規約には影響しません。 `extern "C"` として宣言しない限り、C++ のメソッドや関数では、別の名前装飾規約が使用されます。 詳細については、「[装飾名](decorated-names.md)」を参照してください。

呼び出し規則の詳細については、「[呼び出し規則](../../cpp/calling-conventions.md)」を参照してください。

## <a name="cdecl-specifics"></a>__cdecl の場合

x86 プロセッサでは、すべての関数の引数は、スタックで右から左へ渡されます。 ARM アーキテクチャおよび x64 アーキテクチャでは、一部の引数はレジスタで渡され、残りの引数はスタックで右から左へ渡されます。 呼び出しルーチンによって、スタックから引数がポップされます。

C の `__cdecl` 名前付け規則では、関数名の前にアンダースコア (`_`) が付けられ、大文字小文字は変換されません。 `extern "C"` として宣言しない限り、C++ の関数では、別の名前装飾規約が使用されます。 詳細については、「[装飾名](decorated-names.md)」を参照してください。

## <a name="fastcall-specifics"></a>__fastcall の場合

`__fastcall` 関数の一部の引数はレジスタ (x86 プロセッサの場合 ECX および EDX) で渡され、その他の引数は右から左の順にスタックにプッシュされます。 これらの引数は、呼び出し元に制御が戻る前に、呼び出し先のルーチンによってスタックからポップされます。 通常、 **/Gr** 実行時間を短縮します。

> [!NOTE]
> インライン アセンブリ言語で記述された関数に対して `__fastcall` 呼び出し規則を使用する場合は注意してください。 レジスタを使用すると、コンパイラ側で使用するレジスタと競合する場合があります。

C の `__fastcall` 名前付け規則では、関数名の前にアット マーク ( **\@** ) を付け、その後ろに関数の引数の大きさをバイト数で示します。 大文字と小文字は変換されません。 コンパイラでは、次の名前付け規則用テンプレートが使用されます。

`@function_name@number`

`__fastcall` 名前付け規則を使う場合は、標準のインクルード ファイルを使用してください。 使用しないと、外部参照が解決されません。

## <a name="stdcall-specifics"></a>__stdcall の場合

`__stdcall` 関数の引数は、右から左の順序でスタックにプッシュされます。これらの引数は、呼び出し元に制御が戻る前に、呼び出し先の関数によってポップされます。

C の `__stdcall` 名前付け規則では、関数名の前にアンダースコア ( **\_** ) を付け、関数名の最後にアット マーク ( **\@** ) を付けます。このアット マークの後ろに、関数の引数の大きさをバイト数で示します。 大文字小文字は変換されません。 コンパイラでは、次の名前付け規則用テンプレートが使用されます。

`_functionname@number`

## <a name="vectorcall-specifics"></a>__vectorcall の場合

`__vectorcall` 関数の整数引数は、最大 2 個 (x86) または最大 4 個 (x64) の整数レジスタ、および浮動小数点とベクター値の場合は最大の 6 個の XMM レジスタを使用して値渡しされ、その他はスタックで右から左へ渡されます。 呼び出された関数は、制御を戻す前にスタックをクリーンオフします。 ベクターと浮動小数点戻り値は、XMM0 で返されます。

C の `__vectorcall` 名前付け規則では、関数名の後ろに 2 つのアット マーク ( **\@\@** ) を付け、その後ろに関数の引数の大きさをバイト数で示します。 大文字小文字は変換されません。 コンパイラでは、次の名前付け規則用テンプレートが使用されます。

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[C/C++]**  >  **[詳細]** プロパティ ページを選択します。

1. **[呼び出し規約]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>

## <a name="see-also"></a>関連項目

- [MSVC コンパイラ オプション](compiler-options.md)
- [MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
