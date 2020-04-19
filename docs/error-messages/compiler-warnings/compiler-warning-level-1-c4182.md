---
title: コンパイラの警告 (レベル 1) C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: 49e3e2f62b4be50d14cb8da3d776b4640be7160c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391635"
---
# <a name="compiler-warning-level-1-c4182"></a>コンパイラの警告 (レベル 1) C4182

\#入れ子のレベルは 'number'。無限再帰の可能性

コンパイラがヒープ上の領域を使い切りました。入れ子になっているインクルード ファイルの数が原因です。 インクルード ファイルは、別のインクルード ファイルに含められると入れ子になります。

このメッセージは情報目的で、エラー [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)に先だって表示されます。