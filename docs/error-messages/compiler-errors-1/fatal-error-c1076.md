---
title: 致命的なエラー C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406952"
---
# <a name="fatal-error-c1076"></a>致命的なエラー C1076

> コンパイラの制限 : 内部ヒープの上限に達しました。上限を変更するには /Zm オプションを使用してください。

このエラーは、シンボルが多すぎるか、テンプレートのインスタンス生成が多すぎることが原因で発生する場合があります。 Visual Studio 2015 以降、このメッセージは可能性が並列ビルドのプロセスが多すぎるによる Windows 仮想メモリの負荷からあります。 この場合、使用する推奨事項、 **/Zm**オプションは、使用している場合を除き、無視するか、`#pragma hdrstop`ディレクティブ。

このエラーを解決するには、次の方法があります。

1. プリコンパイル済みヘッダーを使用している場合、`#pragma hdrstop`ディレクティブを使用して、 [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)で指定された値に、コンパイラ メモリ制限を設定するオプション、 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)エラー メッセージ。 Visual Studio でこの値を設定する方法などの詳細については、「解説」セクションを参照してください。 [/Zm (指定プリコンパイル済みヘッダーのメモリ割り当て制限)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)します。

1. 使用して指定された並列処理の数を減らすことを検討してください、 **/maxcpucount** msbuild オプション。実行可能ファイルと組み合わせて、 **/MP** CL するオプション。実行可能ファイルです。 詳細については、次を参照してください。[プリコンパイル済みヘッダー (PCH) の問題と推奨事項](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)します。

1. 64 ビット オペレーティング システムで 32 ビット ホスト コンパイラを使用している場合は、代わりに 64 ビット ホスト コンパイラを使用します。 詳細については、「[方法 :コマンドラインで 64 ビット Visual C ツールセットを有効にする](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)します。

1. 不必要なインクルード ファイルを除去します。

1. 不要なグローバル変数を削除します。これを行うには、たとえば、サイズの大きな配列を宣言する代わりに、メモリを動的に割り当てます。

1. 不要な宣言を削除します。

場合の値が指定されたビルドの開始後すぐに C1076 **/Zm**は、プログラムの高すぎる可能性があります。 削減、 **/Zm**値。