---
title: /Fp (名前&period;pch ファイル)
description: /Fp コンパイラ オプションを使用して、プリコンパイル済みヘッダー ファイル名を指定します。
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460878"
---
# <a name="fp-name-periodpch-file"></a>/Fp (名前&period;pch ファイル)

既定のパス名を使用する代わりにプリコンパイル済みヘッダーのパス名を提供します。

## <a name="syntax"></a>構文

> **/Fp**<em>パス名</em>

## <a name="remarks"></a>Remarks

使用して、 **/Fp**オプションと[/Yc (プリコンパイル済みヘッダー ファイルの作成)](yc-create-precompiled-header-file.md)または[/Yu (プリコンパイル済みヘッダー ファイルの使用)](yu-use-precompiled-header-file.md)プリコンパイル済みヘッダー (PCH) のパスとファイル名を指定するにはファイルです。 既定では、 **/Yc**オプションは、ソース ファイルの基本名を使用して PCH ファイル名を作成し、 *pch*拡張機能。

拡張機能の一部として指定しない場合、 *pathname*、拡張機能の*pch*と見なされます。 スラッシュを使用してディレクトリ名を指定する場合 ( **/** ) の末尾に*pathname*、既定のファイル名は、vc*バージョン*0. pch 場所*バージョン*Visual Studio ツールセットのメジャー バージョンします。 このディレクトリが存在するか、C1083 エラーが生成されます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. 開く、**構成プロパティ** > **C/C++**  > **プリコンパイル済みヘッダー**プロパティ ページ。

1. 変更、**プリコンパイル済みヘッダー出力ファイル**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="examples"></a>使用例

個別のプログラムのデバッグ ビルドのプリコンパイル済みヘッダー ファイルのバージョンをという名前を作成するには、など、コマンドを指定できます。

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

次のコマンドでは、MYPCH.pch をという名前のプリコンパイル済みヘッダー ファイルの使用を指定します。 コンパイラは PROG.cpp MYAPP.h、月末までのソース コードをプリコンパイルし、MYPCH.pch にプリコンパイル済みのコードが配置します。 MYPCH.pch のコンテンツを使用し、.obj ファイルを作成する PROG.cpp の残りの部分をコンパイルします。 この例の出力は、PROG.exe という名前のファイルです。

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[パス名の指定](specifying-the-pathname.md)
