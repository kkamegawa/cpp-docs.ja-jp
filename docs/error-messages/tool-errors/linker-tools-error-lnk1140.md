---
title: リンカ ツール エラー LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255067"
---
# <a name="linker-tools-error-lnk1140"></a>リンカ ツール エラー LNK1140

プログラム データベース モジュールが多すぎます/pdb:none を指定してリンク: なし

プロジェクトには、4096 を超えるモジュールが含まれています。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. 使用して再リンク[/PDB: NONE](../../build/reference/pdb-use-program-database.md)します。

1. デバッグ情報なしには、一部のモジュールをコンパイルします。

1. モジュールの数を減らします。