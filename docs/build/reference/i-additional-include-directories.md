---
title: /I (追加のインクルード ディレクトリ)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 6ec8b15e77fec5214013c484e617904ed29e8197
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270143"
---
# <a name="i-additional-include-directories"></a>/I (追加のインクルード ディレクトリ)

インクルード ファイルを検索するディレクトリの一覧には、ディレクトリを追加します。

## <a name="syntax"></a>構文

> **/I**[ ]*directory*

### <a name="arguments"></a>引数

*directory*<br/>
ディレクトリの一覧に追加するディレクトリは、インクルード ファイルを検索します。

## <a name="remarks"></a>Remarks

1 つ以上のディレクトリを追加するには、このオプションを複数回使用します。 指定したインクルード ファイルが見つかるまでにのみ、ディレクトリが検索されます。

このオプションを使用することができます、([/X (標準インクルード パスの無視)](x-ignore-standard-include-paths.md)) オプション。

コンパイラは、次の順序でディレクトリを検索します。

1. 使用して指定されている場合、 [#include ディレクティブ](../../preprocessor/hash-include-directive-c-cpp.md)二重引用符のフォームで最初に検索のローカル ディレクトリ。 含むファイルと同じディレクトリで検索を開始、 **#include**ステートメント。 検索できない場合は、ファイルを検索、開かれた逆の順序で現在開かれているディレクトリのインクルード ファイル。 ディレクトリの検索は親インクルード ファイルのディレクトリから始まり、上方向へ移動して親の親インクルード ファイルのディレクトリへと続きます。

1. 使用して指定されている場合、 **#include**ディレクティブの角度でフォームを角かっこまたはを使用して指定されたディレクトリを検索するローカル ディレクトリの検索が失敗した場合、 **/I** CL で出現する順序でのオプションコマンドライン。

1. 指定されたディレクトリ、 **INCLUDE**環境変数。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **全般**プロパティ ページ。

1. 変更、**追加のインクルード ディレクトリ**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>

## <a name="example"></a>例

次のコマンドは、次の順序で MAIN.c によって要求されたインクルード ファイルを探します。まず、二重引用符を使用して、指定した場合は、ローカル ファイルが検索されます。 次に、検索は、\INCLUDE ディレクトリから、\MY\INCLUDE ディレクトリを継続し、最後に、ディレクトリに、INCLUDE 環境変数に割り当てられています。

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
