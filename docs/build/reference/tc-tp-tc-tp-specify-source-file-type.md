---
title: /Tc、/Tp、/TC、/TP (ソース ファイル タイプの指定)
ms.date: 01/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927632"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP (ソース ファイル タイプの指定)

**/Tc**オプションは、ファイル名の引数が .c 拡張子を持たない場合でも、c ソースファイルであることを指定します。 **/Tp**オプションは、ファイル名の引数が .cpp C++または .cxx 拡張子を持たない場合でも、ソースファイルであることを指定します。 オプションとファイル名の間のスペースは省略可能です。 各オプションは、1つのファイルを指定します。追加のファイルを指定するには、オプションを繰り返します。

**/Tc**と **/Tp**は、 **/tc**および **/tp**のグローバルなバリエーションです。 このオプションは、コマンドライン上のオプションに関連する場所に関係なく、コマンドラインで指定さC++れたすべてのファイルを C ソースファイル ( **/tc**) またはソースファイル ( **/tp**) として処理するようコンパイラに指定します。 これらのグローバルオプションは、 **/tc**または **/tp**を使用して1つのファイルで上書きできます。

## <a name="syntax"></a>構文

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>引数

*ファイル名*<br/>
C またはC++ソースファイル。

## <a name="remarks"></a>Remarks

既定では、 **CL**は拡張子 .c のファイルが c ソースファイルであり、.cpp または .cxx 拡張子のファイルがC++ソースファイルであることを前提としています。

**Tc**または**tc**オプションが指定されている場合、 [/Zc: Wchar_t (wchar_t はネイティブ型)](zc-wchar-t-wchar-t-is-native-type.md)オプションの指定は無視されます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] [**CC++/**  > **詳細設定**] プロパティページを選択します。

1. "**コンパイル**" プロパティを変更します。 **[OK]** または **[適用]** を選択して変更を適用します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>

## <a name="examples"></a>使用例

この CL コマンドラインでは、MAIN、TEST. prg、および COLLATE. prg がすべて C ソースファイルであることを指定します。 CL will not recognize PRINT.prg.

> CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG

この CL コマンドラインは、.cxx、TEST3、および TEST4 がファイルとしてC++コンパイルされ、TEST5 が c ファイルとしてコンパイルされることを指定します。

> CL TEST1。C TEST2.CXX TEST3。TEST4。O/Tc TEST5。Z/TP

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
