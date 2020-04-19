---
title: /FC (診断時のソース コード ファイルの完全パス)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 190174e1e2ac4d160140ddc54f9cc1c3a1b31709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271295"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (診断時のソース コード ファイルの完全パス)

コンパイラ診断でコンパイラに渡されるソース コード ファイルの完全なパスを表示します。

## <a name="syntax"></a>構文

> /FC

## <a name="remarks"></a>Remarks

次のコード サンプルを検討してください。

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

せず **/FC**、診断用のテキストはこの診断用のテキストのようになります。

- compiler_option_FC.cpp(5) : error C2143: syntax error : missing ';' before '}'

**/FC**、診断用のテキストはこの診断用のテキストのようになります。

- c:\test\compiler_option_fc.cpp(5) : error C2143: syntax error : missing ';' before '}'

**/FC**を使用する場合は、ファイル名の完全なパスを表示する場合にも必要です、 &#95;&#95;ファイル&#95;&#95;マクロ。 参照してください[定義済みマクロ](../../preprocessor/predefined-macros.md)の詳細については&#95;&#95;ファイル&#95;&#95;します。

**/FC**がオプションが含まれる **/ZI**します。 詳細については **/ZI**を参照してください[/Z7、/Zi、/ZI (デバッグ情報の形式)](z7-zi-zi-debug-information-format.md)します。

**/FC**小文字で完全なパスを出力します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **詳細**プロパティ ページ。

1. 変更、**完全パスの使用**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
