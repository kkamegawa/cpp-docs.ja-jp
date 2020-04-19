---
title: 致命的なエラー C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 876ae7a368d2d1a1ee94a04fc9ecf50d0f4b8d78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364234"
---
# <a name="fatal-error-c1060"></a>致命的なエラー C1060

ヒープの領域を使い果たしました。

オペレーティング システムまたはランタイム ライブラリがメモリの要求に対応できません。

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>このエラーを解決するには次の方法があります。

1. コンパイラはエラーも発行する場合[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)と[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)を使用して、 [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)コンパイラ オプションで、メモリ割り当て制限を低きます。 残りのメモリ割り当てを削減すると、アプリケーションに使用できるヒープ領域が増加します。

   場合、 [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)オプションは既に設定されている、それを削除してください。 オプションで指定されたメモリ割り当て制限が高すぎるために、ヒープ領域が足りなくなっている可能性があります。 削除する場合、コンパイラは既定の制限を使用して、 [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)オプション。

1. 64 ビット プラットフォームでコンパイルする場合は、64 ビットのコンパイラ ツールセットを使用します。 詳細については、「[方法:コマンドラインで 64 ビット Visual C ツールセットを有効にする](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)します。

1. 32 ビットの Windows で試すを使用して、 [3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini スイッチ。

1. Windows のスワップ ファイルのサイズを大きくします。

1. 実行中のプログラムを終了します。

1. 不必要なインクルード ファイルを除去します。

1. 不要なグローバル変数を削除します。これを行うには、たとえば、サイズの大きな配列を宣言する代わりに、メモリを動的に割り当てます。

1. 不要な宣言を削除します。

9. 現在のファイルを小さなファイルに分割します。