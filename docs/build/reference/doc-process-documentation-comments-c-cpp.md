---
title: /doc (ドキュメント コメントの処理) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: 90f63a972245114424b64d4131420dcb4e1e925a
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342919"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (ドキュメント コメントの処理) (C/C++)

ソース コード ファイル内およびドキュメントのコメントを含むソース コード ファイルごとに .xdc ファイルを作成するコンパイラ ドキュメント コメントの処理をします。

## <a name="syntax"></a>構文

> **/doc**[*name*]

## <a name="arguments"></a>引数

*name*<br/>
コンパイラで作成される .xdc ファイルの名前。 1 つの .cpp ファイルがコンパイル時に渡されるときにのみ有効です。

## <a name="remarks"></a>Remarks

.Xdc ファイルは、xdcmake.exe の .xml ファイルに処理されます。 詳細については、次を参照してください。 [XDCMake リファレンス](xdcmake-reference.md)します。

ソース コード ファイルには、ドキュメントのコメントを追加できます。 詳細については、「 [ドキュメント コメント用の推奨タグ](recommended-tags-for-documentation-comments-visual-cpp.md)」を参照してください。

IntelliSense を備えた、生成された .xml ファイルを使用するには、.xml ファイルをサポートし、.xml ファイルを配置するアセンブリと同じアセンブリと同じディレクトリ内のファイル名を確認します。 アセンブリは、Visual Studio プロジェクトで参照されて、.xml ファイルはあります。 詳細については、次を参照してください。[を使用して IntelliSense](/visualstudio/ide/using-intellisense)と[XML コード コメント](/visualstudio/ide/supplying-xml-code-comments)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **出力ファイル**プロパティ ページ。

1. 変更、 **XML ドキュメント ファイルの生成**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
