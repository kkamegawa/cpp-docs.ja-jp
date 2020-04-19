---
title: /EP (#line ディレクティブを挿入しない stdout へのプリプロセス)
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: 49745b644234c0e5ce92661f14304531aaca5c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293252"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (#line ディレクティブを挿入しない stdout へのプリプロセス)

C および C++ ソース ファイルを前処理し、前処理済みファイルを標準出力デバイスにコピーします。

## <a name="syntax"></a>構文

```
/EP
```

## <a name="remarks"></a>Remarks

プロセスですべてのプリプロセッサ ディレクティブが実行されます、マクロの展開が実行されて、およびコメントを削除します。 前処理済みの出力内のコメントを保持するために使用して、 [/C (保持プリプロセス時のコメント)](c-preserve-comments-during-preprocessing.md)オプションと **/EP**します。

**/EP**オプションはコンパイルを中止します。 Compilation の前処理済みファイルを再送信する必要があります。 **/EP**から出力ファイルも生成されません、 **/FA**、 **/Fa**、および **/Fm**オプション。 詳細については、次を参照してください。 [/FA、/Fa (リスティング ファイル)](fa-fa-listing-file.md)と[/Fm (マップ ファイルの名前)](fm-name-mapfile.md)します。

処理の後のステージ中に生成されたエラーは、元のソース ファイルではなく、前処理済みファイルの行番号を参照してください。 行番号を元のソース ファイルを参照する場合は、使用[/E (stdout に前処理する)](e-preprocess-to-stdout.md)代わりにします。 **/E**オプションは、追加`#line`をこの目的の出力ディレクティブ。

前処理済みの出力を送信する`#line`ディレクティブでは、ファイル、使用、 [/P (ファイルへのプリプロセス)](p-preprocess-to-a-file.md)オプションを使用します。

と共にを stdout に前処理済みの出力を送信する`#line`ディレクティブを使用して、 **/P**と **/EP**化します。

プリコンパイル済みヘッダーを使用することはできません、 **/EP**オプション。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**プリプロセッサ**プロパティ ページ。

1. 変更、**前処理されたファイルの生成**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>

## <a name="example"></a>例

次のコマンド ライン ファイルを前処理`ADD.C`をコメントを保持しを標準出力デバイスに、結果を表示します。

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
