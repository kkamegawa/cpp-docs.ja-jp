---
title: /P (プリプロセス出力のファイルへの書き込み)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 5e6302d90647bce7e37c47a619e814cab300aaee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319981"
---
# <a name="p-preprocess-to-a-file"></a>/P (プリプロセス出力のファイルへの書き込み)

C および C++ ソース ファイルを前処理し、ファイルを前処理済みの出力を書き込みます。

## <a name="syntax"></a>構文

```
/P
```

## <a name="remarks"></a>Remarks

ファイル名は、ソース ファイルの基本名に .i 拡張機能を持ちます。 プロセスですべてのプリプロセッサ ディレクティブが実行されます、マクロの展開が実行されて、およびコメントを削除します。 前処理済みの出力内のコメントを保持するために使用して、 [(保持プリプロセス時のコメント)/C](c-preserve-comments-during-preprocessing.md)オプションと共に **/P**します。

**/P**追加`#line`ディレクティブを先頭と末尾各インクルード ファイルの条件付きコンパイルのプリプロセッサ ディレクティブによって削除された行に出力します。 これらのディレクティブは、前処理済みファイルの行を再設定します。 その結果、処理の後のステージ中に生成されたエラーは、前処理済みファイル内の行ではなく、元のソース ファイルの行番号を参照してください。 生成を抑制する`#line`ディレクティブを使用して、 [/EP (#line ディレクティブなしの stdout に前処理する)](ep-preprocess-to-stdout-without-hash-line-directives.md)だけでなく **/P**します。

**/P**オプションはコンパイルを中止します。 使用する場合でも、.obj ファイルは生成されません[/Fo (オブジェクト ファイル名)](fo-object-file-name.md)します。 Compilation の前処理済みファイルを再送信する必要があります。 **/P**から出力ファイルも生成されません、 **/FA**、 **/Fa**、および **/Fm**オプション。 詳細については、次を参照してください。 [/FA、/Fa (リスティング ファイル)](fa-fa-listing-file.md)と[/Fm (マップ ファイルの名前)](fm-name-mapfile.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**プリプロセッサ**プロパティ ページ。

1. 変更、**前処理されたファイルの生成**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>

## <a name="example"></a>例

次のコマンドラインの前処理`ADD.C`、コメントを保持、追加`#line`ディレクティブをファイルに結果を書き出すと`ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/Fi (出力ファイル名の前処理)](fi-preprocess-output-file-name.md)
