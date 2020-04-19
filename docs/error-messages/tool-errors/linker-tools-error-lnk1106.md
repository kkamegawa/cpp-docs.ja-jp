---
title: リンカ ツール エラー LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 7551e2f3f1efc90913981feb674f48aadb9ace51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255320"
---
# <a name="linker-tools-error-lnk1106"></a>リンカ ツール エラー LNK1106

無効なファイルまたはディスクがいっぱいです: の場所にシークできません。

ツールの読み取りまたは書き込みがいない`location`メモリ マップト ファイル。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. ディスクがいっぱいです。

   領域を解放し、リンクを再度クリックします。

1. ネットワーク経由でリンクしようとしています。

   いくつかのネットワークでは、リンカーで使用されるメモリ マップト ファイルは完全にサポートしていません。 ローカル ディスクでのリンクを再試行してください。

1. ディスクで不良ブロックします。

   オペレーティング システムとディスクのハードウェアでは、このようなエラーが検出が必要、ディスク チェックのプログラムを実行することがあります。

1. ヒープ領域にします。

   参照してください[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)詳細についてはします。