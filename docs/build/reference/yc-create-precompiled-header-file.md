---
title: /Yc (プリコンパイル済みヘッダー ファイルの作成)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 0d902b9ebb35bc7f267cb67861b7be0763f378a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316705"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (プリコンパイル済みヘッダー ファイルの作成)

コンパイラで特定の時点のコンパイルの状態を表すプリコンパイル済みヘッダー (.pch) ファイルを作成するように指示します。

## <a name="syntax"></a>構文

> __/Yc__<br/>
> __/Yc__*filename*

## <a name="arguments"></a>引数

*ファイル名*<br/>
ヘッダー (.h) ファイルを指定します。 この引数を使用すると、コンパイラは、.h ファイルを含むすべてのコードをコンパイルします。

## <a name="remarks"></a>Remarks

ときに **/Yc**なしで指定された引数、またはベースのファイル内のポイントに、ベースのソース ファイルの最後までのすべてのコードをコンパイルしている、 [hdrstop](../../preprocessor/hdrstop.md)ディレクティブに発生します。 使用して別のファイル名を指定しない限り .pch ファイルの結果として得られるが、ベースのソース ファイルと同じ基本名を持つ、 **hdrstop**プラグマまたは **/Fp**オプション。

指定したファイルのベース名から作成された名前のプリコンパイルされたコードをファイルに保存、 **/Yc**オプションと拡張子 .pch をします。 使用することも、 [/Fp (名前です。Pch ファイル)](fp-name-dot-pch-file.md)プリコンパイル済みヘッダー ファイルの名前を指定するオプション。

使用する場合 __/Yc__*filename*でその後使用するため、指定したファイルを含むすべてのコードをコンパイルして、 [/Yu (プリコンパイル済みヘッダー ファイルの使用)](yu-use-precompiled-header-file.md)オプション。

場合、オプション __/Yc__*filename*と __/Yu__*filename*同じコマンド行で発生し、両方の参照、または、同じファイル名を意味します。__/Yc__*filename*が優先されます。 この機能は、メイクファイルの記述を簡略化します。

プリコンパイル済みヘッダーの詳細についてを参照してください。

- [/Y (プリコンパイル済みヘッダー)](y-precompiled-headers.md)

- [プリコンパイル済みヘッダー ファイル](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. .Cpp ファイルを選択します。 .Cpp ファイルである必要があります #include プリコンパイル済みヘッダーの情報を含む .h ファイル。 プロジェクトの **/Yc**ファイル レベルで設定をオーバーライドできます。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 開く、**構成プロパティ**、 **C/C++**、**プリコンパイル済みヘッダー**プロパティ ページ。

1. 変更、**プリコンパイル済みヘッダーの**プロパティ。

1. ファイル名を設定するには、変更、**プリコンパイル済みヘッダー ファイル**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>」を参照してください。

## <a name="example"></a>例

次のコードがあるとします。

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

コマンドを使用してこのコードをコンパイルするときに`CL /YcMYAPP.H PROG.CPP`コンパイラは、AFXWIN.h、RESOURCE.h のすべての前処理を保存し、プリコンパイル済みヘッダー ファイルで MYAPP.h というされます。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[プリコンパイル済みヘッダー ファイル](../creating-precompiled-header-files.md)
