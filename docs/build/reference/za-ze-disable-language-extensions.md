---
title: /Za、/Ze (言語拡張機能の無効化)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315886"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze (言語拡張機能の無効化)

**/Za**コンパイラ オプションを無効にし、ANSI C89/ISO C90 と互換性のない C への Microsoft 拡張のエラーを出力します。 非推奨とされる **/Ze**コンパイラ オプションは、Microsoft の拡張機能を使用します。 Microsoft 拡張機能は既定で有効になっています。

## <a name="syntax"></a>構文

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>Remarks

> [!NOTE]
> 使用 **/Za**コードがコンパイルされると、C++ は推奨されません。 **/Ze**オプションは、その動作は既定で非推奨とされます。 非推奨のコンパイラ オプションの一覧は、次を参照してください。[非推奨と削除されたコンパイラ オプション](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)します。

Microsoft C/C コンパイラでは、2 つの方法で C コードのコンパイルをサポートします。

- ソース ファイルの場合、コンパイラが既定で C コンパイル モードを使用、 *.c*拡張機能、または、 [/Tc](tc-tp-tc-tp-specify-source-file-type.md)または[/TC](tc-tp-tc-tp-specify-source-file-type.md)オプションを指定します。 C コンパイラは、既定では、C 言語に対する Microsoft 拡張機能を使用する C89/C90 コンパイラです。 特定の拡張機能の詳細については、次を参照してください。 [C および C++ の Microsoft 拡張機能](microsoft-extensions-to-c-and-cpp.md)します。 ときに両方の C のコンパイルと **/Za**オプションが指定されて、C コンパイラは、C89/C90 標準に厳密に準拠しています。 コンパイラは、Microsoft 拡張キーワードを単純な識別子として扱われます、他の Microsoft 拡張機能を無効にし、自動的に定義されます、 [ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md)定義済みC プログラム用のマクロ。

- コンパイラは C++ のコンパイル モードでの C コードをコンパイルできます。 この動作は、既定のソース ファイルがない、 *.c*拡張機能とタイミング、 [/Tp](tc-tp-tc-tp-specify-source-file-type.md)または[/TP](tc-tp-tc-tp-specify-source-file-type.md)オプションを指定します。 C++ のコンパイル モードでは、コンパイラは、C++ 標準に組み込まれていますが、ISO C99、C11 の標準の一部をサポートします。 ほぼすべての C コードは、有効な C++ コードをもできます。 C キーワードとコードの構成要素の数が少ないはいない有効な C++ コード、または C++ では異なる方法で解釈されます。 コンパイラは、このような場合は標準の C++ に従って動作します。 C++ のコンパイル モードで、 **/Za**オプションを選択して予期しない動作がありますはお勧めしません。

他のコンパイラ オプション、コンパイラにより標準への準拠、方法に影響を与えることができます。 特定の標準 C および C++ の動作設定を指定する方法は、次を参照してください。、 [/Zc](zc-conformance.md)コンパイラ オプション。 C++ 標準準拠の追加の設定を参照してください、 [/permissive -](permissive-standards-conformance.md)と[/std](std-specify-language-standard-version.md)コンパイラ オプション。

Visual C の準拠の問題の詳細については、次を参照してください。[非標準動作](../../cpp/nonstandard-behavior.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. ナビゲーション ウィンドウで、**構成プロパティ** > **C/C++** > **言語**します。

1. 変更、**言語拡張機能を無効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](compiler-options.md)<br/>
[/Zc (準拠)](zc-conformance.md)<br/>
[/permissive- (標準への準拠)](permissive-standards-conformance.md)<br/>
[/std (言語の標準バージョンの指定)](std-specify-language-standard-version.md)<br/>
