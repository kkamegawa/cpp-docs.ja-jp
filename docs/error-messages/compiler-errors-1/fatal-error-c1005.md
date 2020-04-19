---
title: 致命的なエラー C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: a84791367656729b1cbd50ca180368f6c01531a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383192"
---
# <a name="fatal-error-c1005"></a>致命的なエラー C1005

コンパイラの中間ファイルの文字列がバッファーの大きさを超えました。

コンパイラの中間ファイル内の文字列で、バッファーがオーバーフローしました。

このエラーは、 [/Fd](../../build/reference/fd-program-database-file-name.md) または [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) コンパイラ オプションに渡すパラメーターが 256 バイトを超えている場合に発生することがあります。