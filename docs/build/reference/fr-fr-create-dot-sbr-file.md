---
title: /FR、/Fr (.sbr ファイルの作成)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 73642baba77a62cac531ae7b2842ec9953b338ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292797"
---
# <a name="fr-fr-create-sbr-file"></a>/FR、/Fr (.sbr ファイルの作成)

.sbr ファイルを作成します。

## <a name="syntax"></a>構文

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Remarks

> [!WARNING]
> BSCMAKE は、現在も Visual Studio と共にインストールされていますが、IDE では使用されなくなりました。 Visual Studio 2008 以降、ブラウザーとシンボルの情報は、ソリューション フォルダー内の SQL Server の .sdf ファイルに自動的に格納されます。

ビルド処理中、Microsoft Browse Information File Maintenance Utility (BSCMAKE) はこれらのファイルを使って BSC ファイルを作成します。このファイルは、ブラウザー情報を表示するために使います。

**/FR** は、完全なシンボリック情報を含む .sbr ファイルを作成します。

**/Fr** は、ローカル変数に関する情報を含まない .sbr ファイルを作成します。

`filename`を指定しない場合、.sbr ファイルはソース ファイルと同じベース名を取得します。

**/Fr** は非推奨とされます。代わりに **/FR** を使用してください。 詳しくは、 [Compiler Options Listed by Category](compiler-options-listed-by-category.md)の「非推奨とされた削除済みのコンパイラ オプション」をご覧ください。

> [!NOTE]
>  .sbr 拡張子を変更しないでください。 BSCMAKE では、中間ファイルにその拡張子を含める必要があります。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. ナビゲーション ウィンドウで、 **[C/C++]**、 **[ブラウザー情報]** プロパティ ページを選択してください。

1. **[ブラウザー情報ファイル]** か **[ブラウザー情報の有効化]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[パス名の指定](specifying-the-pathname.md)
