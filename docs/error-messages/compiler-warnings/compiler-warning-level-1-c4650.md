---
title: コンパイラの警告 (レベル 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393533"
---
# <a name="compiler-warning-level-1-c4650"></a>コンパイラの警告 (レベル 1) C4650

プリコンパイル済みヘッダー以外ではなくデバッグ情報ヘッダーからのグローバル シンボルのみが提供されます。

プリコンパイル済みヘッダー ファイルは、シンボリック デバッグ情報の Microsoft ではコンパイルされませんでした。

リンクされるとき、生成された実行可能ファイルまたはダイナミック リンク ライブラリ ファイルには、プリコンパイル済みヘッダーに含まれるローカル シンボルのデバッグ情報は含まれません。

プリコンパイル済みヘッダー ファイルを再コンパイルでは、この警告を回避できます、 [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)コマンド ライン オプション。