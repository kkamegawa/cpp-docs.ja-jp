---
title: リソース コンパイラ エラー RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173445"
---
# <a name="resource-compiler-error-rc2151"></a>リソース コンパイラ エラー RC2151

文字列定数を再利用することはできません。

2 回の同じ値を使用している、 **STRINGTABLE**ステートメント。 10 進数と 16 進数の値が重複している混在させていないことを確認します。

各 ID で、 **STRINGTABLE**で一意である必要があります。 効率を最大化使用の連続する定数は、16 の倍数でを起動します。