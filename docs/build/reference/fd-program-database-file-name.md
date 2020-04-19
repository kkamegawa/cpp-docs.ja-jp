---
title: /Fd (プログラム データベース ファイル名)
ms.date: 11/04/2016
f1_keywords:
- /FD
- VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName
- VC.Project.VCCLCompilerTool.ProgramDataBaseFileName
helpviewer_keywords:
- /FD compiler option [C++]
- program database file name [C++]
- -FD compiler option [C++]
- PDB files, creating
- program database compiler option [C++]
- .pdb files, creating
- FD compiler option [C++]
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
ms.openlocfilehash: c686de7dc9c9c20c404240db558d2ff66078ceb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292732"
---
# <a name="fd-program-database-file-name"></a>/Fd (プログラム データベース ファイル名)

によって作成されたプログラム データベース (PDB) ファイルのファイル名を示す[/Z7、/Zi、/ZI (デバッグ情報の形式)](z7-zi-zi-debug-information-format.md)します。

## <a name="syntax"></a>構文

```
/Fdpathname
```

## <a name="remarks"></a>Remarks

せず **/Fd**、PDB ファイル名の既定値は VC*x*0. pdb、場所*x*使用中の Visual C のメジャー バージョンします。

ファイル名 (パスは、円記号で終わる) が含まれていないパス名を指定する場合、コンパイラは、VC をという名前の .pdb ファイルを作成*x*指定したディレクトリ内の 0. pdb です。

拡張機能が含まれていないファイル名を指定する場合、コンパイラは、拡張機能として .pdb を使用します。

このオプションには、最小リビルドとインクリメンタル コンパイルに使用される状態 (.idb) ファイル名もします。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[出力ファイル]** プロパティ ページをクリックします。

1. 変更、**プログラム データベース ファイル名**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>

## <a name="example"></a>例

このコマンドラインは、PROG.pdb と .idb ファイル PROG.idb という名前をという名前の .pdb ファイルを作成します。

```
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP
```

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[パス名の指定](specifying-the-pathname.md)
