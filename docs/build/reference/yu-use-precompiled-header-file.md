---
title: /Yu (プリコンパイル済みヘッダー ファイルの使用)
ms.date: 11/04/2016
f1_keywords:
- /yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: c0dcb045450d6e6eca31b8c76a92726e62400656
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316146"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (プリコンパイル済みヘッダー ファイルの使用)

現在のコンパイルで既存のプリコンパイル済みヘッダー (.pch) ファイルを使用するコンパイラに指示します。

## <a name="syntax"></a>構文

```
/Yu[filename]
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
使用して、ソース ファイルに含まれているヘッダー ファイルの名前、 **#include**プリプロセッサ ディレクティブです。

## <a name="remarks"></a>Remarks

インクルード ファイルの名前はどちらに関しても同じである必要があります、 **/Yc**とプリコンパイル済みヘッダーを作成するオプション後続 **/Yu**プリコンパイル済みヘッダーの使用を示すオプション。

**/Yc**、`filename`時点を指定するプリコンパイルが停止しますコンパイラがすべてのコードをプリコンパイル`filename`インクルード ファイルと拡張機能の基本名を使用して、結果として得られるプリコンパイル済みヘッダーの名前と.pch します。

.Pch ファイルを指定する必要がありますを使って作成された **/Yc**します。

コンパイラは、プリコンパイル済みと .h ファイルの前に発生しているすべてのコードを扱います。 それ以降だけにスキップ、 **#include** 、.h ファイルに関連付けられているディレクティブが .pch ファイルに含まれるコードを使用して、後のすべてのコードをコンパイルし、`filename`します。

コマンドラインでスペースは入れません間 **/Yu**と`filename`します。

指定すると、 **/Yu**ファイル名、ソース プログラムのないオプションを指定する必要があります、 [#pragma hdrstop](../../preprocessor/hdrstop.md)プラグマ プリコンパイル済みヘッダーを .pch ファイルのファイル名を指定します。 この場合、コンパイラはによってという名前のプリコンパイル済みヘッダー (.pch ファイル) が使用[/Fp (名前です。Pch ファイル)](fp-name-dot-pch-file.md)します。 コンパイラは、プラグマの位置にスキップ、プラグマで指定されたプリコンパイル済みヘッダー ファイルからコンパイル済みの状態を復元およびプラグマを次のコードだけをコンパイルします。 場合 **#pragma hdrstop**拡張子 .pch を持つソース ファイルのベース名から派生した名前のファイルのコンパイラは、ファイル名を指定しません。 使用することも、 **/Fp**別の .pch ファイルを指定するオプション。

指定した場合、 **/Yu**ファイル名のないオプションを選択し、指定しないと、 **hdrstop**プラグマ、エラー メッセージを生成およびコンパイルが成功しました。

場合、 **/Yc** `filename`と **/Yu** `filename`オプションは、同じコマンド行で発生して、同じファイル名を参照両方 **/Yc** `filename`は優先順位、まで、すべてのコードをプリコンパイルして、名前付きのファイルを含むです。 この機能は、メイクファイルの記述を簡略化します。

.Pch ファイルには、マシンの環境に関する情報のほか、プログラムのメモリ アドレス情報が含まれている、ためにのみが作成されたコンピューターの pch ファイルを使用する必要があります。

プリコンパイル済みヘッダーの詳細についてを参照してください。

- [/Y (プリコンパイル済みヘッダー)](y-precompiled-headers.md)

- [プリコンパイル済みヘッダー ファイル](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. 指定[/Yc (プリコンパイル済みヘッダー ファイルの作成)](yc-create-precompiled-header-file.md)プロジェクトで .cpp ファイルでします。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**プリコンパイル済みヘッダー**プロパティ ページ。

1. 変更、**ファイルを使用して PCH を作成/使用**プロパティまたは**プリコンパイル済みヘッダーの作成/使用**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>」を参照してください。

## <a name="examples"></a>使用例

場合、次のコード。

```
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

コマンドラインを使用したコンパイル`CL /YuMYAPP.H PROG.CPP`コンパイラは、3 つを処理しないファイル (およびすべてのファイルが含まれている可能性があります) の 3 つすべての前処理に関連する時間を節約しされますのプリコンパイルを使用してコードではなくステートメントを含めます。

使用することができます、 [/Fp (名前です。Pch ファイル)](fp-name-dot-pch-file.md)オプションは、 **/Yu**名前がするか、ファイル名引数と異なる場合は、.pch ファイルの名前を指定するオプション **/Yc**またはのソース ファイルの基本名、次の。

```
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

このコマンドは、MYPCH.pch をという名前のプリコンパイル済みヘッダー ファイルを指定します。 コンパイラは、プリコンパイル済みヘッダー ファイルの MYAPP.h のすべての状態を復元するのに、その内容を使用します。 コンパイラが、MYAPP.h 後に発生するコードをコンパイルし、**含める**ステートメント。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
