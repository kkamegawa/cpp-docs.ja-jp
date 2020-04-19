---
title: /Fm (マップ ファイルの名前の指定)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: eebb1bc0c553dba1934aea75e2e63edc0f222fff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292407"
---
# <a name="fm-name-mapfile"></a>/Fm (マップ ファイルの名前の指定)

対応する .exe ファイルまたは DLL で表示される順序でセグメントの一覧を含むマップ ファイルを生成するようにリンカーに指示します。

## <a name="syntax"></a>構文

```
/Fmpathname
```

## <a name="remarks"></a>Remarks

マップ ファイルには既定に対応する C または C++ ソース ファイルの基本の名前が付けられます、します。拡張機能をマップします。

指定する **/Fm**を指定した場合と同じ効果があります、 [/MAP (マップ ファイルの生成)](map-generate-mapfile.md)リンカー オプション。

指定した場合[/c (コンパイル リンクなしの)](c-compile-without-linking.md) 、リンクを抑制する **/Fm**も何も起こりません。

マップ ファイル内のグローバル シンボルでは、コンパイラは変数名に、先頭にアンダー スコアを追加するため、通常は 1 つまたは複数の先頭のアンダー スコアがあります。 マップ ファイルに表示される多くのグローバル シンボルは、コンパイラと標準ライブラリによって内部的に使用されます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[パス名の指定](specifying-the-pathname.md)
