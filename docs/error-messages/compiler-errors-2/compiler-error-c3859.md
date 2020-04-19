---
title: コンパイラ エラー C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391882"
---
# <a name="compiler-error-c3859"></a>コンパイラ エラー C3859

> を超えました PCH の仮想メモリの範囲コマンド ライン オプションを使用してください再コンパイル '-Zm*値*' 以上

コンパイラがこれに格納するしようとしたデータの量に応じて、プリコンパイル済みヘッダーに割り当てられた仮想メモリが小さすぎます。 Visual Studio 2015 以降、 **/Zm**推奨事項を使用する場合にのみ重要な`#pragma hdrstop`ディレクティブ。 それ以外の場合は、Windows 仮想メモリ不足の問題を示す疑似エラーを勧めします。

プリコンパイル済みヘッダーを使用している場合、`#pragma hdrstop`ディレクティブを使用して、 **/Zm**コンパイラ フラグをプリコンパイル済みヘッダー ファイルのより大きな値を指定します。 それ以外の場合、ビルドでの並列コンパイル プロセスの数を減らすことを検討します。 詳細については、次を参照してください。 [/Zm (指定プリコンパイル済みヘッダーのメモリ割り当て制限)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)します。
