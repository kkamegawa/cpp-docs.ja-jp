---
title: /showIncludes (インクルード ファイル一覧)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
ms.openlocfilehash: d454054c132976a899fcc4a56a63be427e79beec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318161"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (インクルード ファイル一覧)

コンパイラでインクルード ファイルのリストを出力します。 入れ子になった含めるファイルも表示されている (に含まれるファイルを含むファイルから)。

## <a name="syntax"></a>構文

```
/showIncludes
```

## <a name="remarks"></a>Remarks

インクルード ファイルがコンパイル時に発生したときに、メッセージは、出力をなどです。

```
Note: including file: d:\MyDir\include\stdio.h
```

入れ子になった含めるなどのファイルは、インデントは、入れ子のレベルごとに 1 つの領域で示されます。

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

この場合、`2.h`内から含まれていました`1.h`、そのため、インデントします。

**/ShowIncludes**オプションを生成する`stderr`ではなく、`stdout`します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**詳細**プロパティ ページ。

1. 変更、 **インクルード ファイルの**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
