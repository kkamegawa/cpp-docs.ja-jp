---
title: リソース コンパイラの致命的なエラー RW1022
ms.date: 11/04/2016
f1_keywords:
- RW1022
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
ms.openlocfilehash: 8065745c85d0552687e77f4d901adce6d1b130c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347223"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>リソース コンパイラの致命的なエラー RW1022

**ファイルの書き込み I/O エラー**

リソース コンパイラは、ファイルに書き込めませんでした。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. ディスク領域が不足しています。 空き領域を作成する実行可能ファイルのサイズの 2 倍以上でなければなりません。

1. ボリュームが読み取り専用です。

1. 正しくないセクターです。

1. 共有違反です。