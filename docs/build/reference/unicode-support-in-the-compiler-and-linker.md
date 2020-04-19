---
title: コンパイラおよびリンカーでの Unicode のサポート
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317329"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>コンパイラおよびリンカーでの Unicode のサポート

ほとんどの Visual C ビルド ツールでは、Unicode の入力と出力をサポートします。

## <a name="filenames"></a>ファイル名

コマンドラインまたはコンパイラ ディレクティブで指定されたファイル名 (など`#include`) の Unicode 文字を含めることができます。

## <a name="source-code-files"></a>ソース コード ファイル

Unicode 文字には、識別子、マクロ、文字列と文字のリテラルやコメントではサポートされています。  ユニバーサル文字名もサポートされます。

Unicode は、次のエンコーディングのソース コード ファイルに入力できます。

- BOM (Byte Order Mark) 付き、または BOM なしの UTF-16 リトル エンディアン。

- BOM 付き、または BOM なしの UTF-16 ビッグ エンディアン。

- BOM 付きの UTF-8

## <a name="output"></a>出力

コンパイル時に、コンパイラは、utf-16 でコンソールに診断を出力します。  コンソールに表示できる文字は、コンソール ウィンドウのプロパティによって決まります  ファイルにリダイレクトされるコンパイラ出力は、現在の ANSI コンソール コードページになります。

## <a name="linker-response-files-and-def-files"></a>リンカー応答ファイルおよび .DEF ファイル

応答ファイルおよび DEF ファイルは、utf-16 BOM または ANSI を指定できます。

## <a name="asm-and-cod-dumps"></a>.asm ダンプおよび .cod ダンプ

.asm ダンプおよび .cod ダンプは、MASM との互換性のために、既定で ANSI になっています。 使用[は/FAu](fa-fa-listing-file.md)を utf-8 を出力します。 指定した場合 **/FAs**、混在したソースが直接は出力したとソース コードが utf-8 と指定しなかった場合の例については、文字が正しくなります **/FAsu**します。

## <a name="see-also"></a>関連項目

[コマンド ラインから MSVC ツールセットを使用する](../building-on-the-command-line.md)