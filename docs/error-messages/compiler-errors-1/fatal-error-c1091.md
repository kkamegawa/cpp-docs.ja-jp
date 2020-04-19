---
title: 致命的なエラー C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 9758d4b779f4727012041da60632bcea8ce18d42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208537"
---
# <a name="fatal-error-c1091"></a>致命的なエラー C1091

コンパイラの制限: 文字列が長さ 'length' バイトを超えています

文字列定数が文字列の長さに対する現在の制限を超えました。

静的な文字列を 2 つ (以上) の変数に分割し、 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) を使用して実行時または宣言の一部としてその分割したものを結合することをお勧めします。