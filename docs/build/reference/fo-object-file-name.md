---
title: /Fo (オブジェクト ファイルの名前の指定)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: a8f2c1a196f18e6d310fd41d4dbed751440a4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293044"
---
# <a name="fo-object-file-name"></a>/Fo (オブジェクト ファイルの名前の指定)

既定値の代わりに使用する、オブジェクト (.obj) ファイルの名前またはディレクトリを指定します。

## <a name="syntax"></a>構文

```
/Fopathname
```

## <a name="remarks"></a>Remarks

このオプションを使用しない場合、オブジェクト ファイルには、ソース ファイルと .obj 拡張機能の基本名が使用されます。 任意の名前と、拡張機能を使用できますが、推奨される規則は、使用する .obj。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[出力ファイル]** プロパティ ページをクリックします。

1. 変更、**オブジェクト ファイルの名前**プロパティ。  オブジェクト ファイル、開発環境での拡張機能をいる必要があります .obj。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>

## <a name="example"></a>例

次のコマンド ラインが既存のディレクトリに、\OBJECT、ドライブ B に THIS.obj をという名前のオブジェクト ファイルを作成します

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[パス名の指定](specifying-the-pathname.md)
