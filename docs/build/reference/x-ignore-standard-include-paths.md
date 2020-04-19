---
title: /X (標準インクルード パスの無視)
ms.date: 07/18/2019
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341043"
---
# <a name="x-ignore-standard-include-paths"></a>/X (標準インクルード パスの無視)

パスで指定されたディレクトリ内のインクルードファイルをコンパイラが検索できないようにし、環境変数を含めます。

## <a name="syntax"></a>構文

```
/X
```

## <a name="remarks"></a>Remarks

このオプションは、 [/i (追加のインクルードディレクトリ)](i-additional-include-directories.md) ( **/i**`directory`) オプションと共に使用できます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[プリプロセッサ]** プロパティページをクリックします。

1. "**標準インクルードパスを無視**する" プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>

## <a name="example"></a>例

次のコマンドでは`/X` 、は、パスで指定された場所を無視し、環境変数`/I`を含めるようにコンパイラに指示します。また、インクルードファイルを検索するディレクトリを指定します。

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
