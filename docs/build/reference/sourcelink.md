---
title: /SOURCELINK (PDB に含める Sourcelink ファイル)
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: a5a01ca56a49791a608c5c836312c7728e9328c3
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978284"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (PDB にソース リンクを含めるファイル)

リンカーによって生成される PDB ファイルに含めるソース リンクの構成ファイルを指定します。

## <a name="syntax"></a>構文

> **/SOURCELINK:**_ファイル名_

## <a name="arguments"></a>引数

*ファイル名*<br/>
JSON 形式の構成ファイルの Url へのローカル ファイル パスの単純なマッピングを含むソース ファイルを取得できる、デバッガーによって表示を指定します。 このファイルの形式の詳細については、次を参照してください。[ソース リンクの JSON スキーマ](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema)します。

## <a name="remarks"></a>Remarks

ソース リンクは、ソースのバイナリのデバッグを提供するために依存しない言語とソース管理システムです。 ソース リンクは、ネイティブの C++ バイナリが Visual Studio 2017 バージョン 15.8 以降でサポートされます。 ソース リンクの概要については、次を参照してください。[ソース リンク](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md)します。 プロジェクトでソース リンクを使用する方法と、プロジェクトの一部として、SourceLink ファイルを生成する方法については、次を参照してください。[を使用してソース リンク](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects)します。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Visual Studio で/SOURCELINK リンカー オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、「[プロジェクト プロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加 **/SOURCELINK:**_filename_選び、 **[ok]** または**適用**、変更を保存します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- このオプションでは、同等のプログラムはありません。

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
