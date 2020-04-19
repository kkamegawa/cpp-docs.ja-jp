---
title: /U、/u (定義済みマクロ シンボルの未定義化)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: bfc03ebd5c900bf8bf81b4a50eed02111baf85ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317004"
---
# <a name="u-u-undefine-symbols"></a>/U、/u (定義済みマクロ シンボルの未定義化)

**/U**コンパイラ オプションが指定したプリプロセッサ シンボルを未定義にします。 **/U**コンパイラ オプションは、コンパイラを定義する Microsoft 固有のシンボルを未定義にします。

## <a name="syntax"></a>構文

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>引数

*シンボル*<br/>
プリプロセッサ シンボルを未定義にします。

## <a name="remarks"></a>Remarks

どちらも、 **/U**または **/u**オプションを使用して作成されたシンボルを未定義ことができます、 **#define**ディレクティブ。

**/U**オプションを使用して定義したシンボルを未定義ことができます、 **/D**オプション。

既定では、コンパイラは、次の Microsoft 固有のシンボルを定義します。

|シンボル|関数|
|------------|--------------|
|_CHAR_UNSIGNED|既定の char 型が署名されていません。 定義されているときに、 [/J](j-default-char-type-is-unsigned.md)オプションを指定します。|
|_CPPRTTI|コンパイルされたコードに対して定義された、 [/GR](gr-enable-run-time-type-information.md)オプション。|
|_CPPUNWIND|コンパイルされたコードに対して定義された、 [/EHsc](eh-exception-handling-model.md)オプション。|
|_DLL|定義されているときに、 [/MD](md-mt-ld-use-run-time-library.md)オプションを指定します。|
|_M_IX86|既定では 600 x86 用に定義されているターゲット。|
|_MSC_VER|詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。|
|_WIN32|WIN32 アプリケーションで定義されています。 これは、常に定義されます。|
|_MT|定義されているときに、 [/MD、/MT または](md-mt-ld-use-run-time-library.md)オプションを指定します。|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**詳細**プロパティ ページ。

1. 変更、**指定したプリプロセッサ定義**または**定義済みプリプロセッサ定義**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 詳細については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>」または「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/J (既定の char 型の unsigned への変更)](j-default-char-type-is-unsigned.md)<br/>
[/GR (ランタイム型情報の有効化)](gr-enable-run-time-type-information.md)<br/>
[/EH (例外処理モデル)](eh-exception-handling-model.md)<br/>
[/MD、/MT、/LD (ランタイム ライブラリの使用)](md-mt-ld-use-run-time-library.md)
