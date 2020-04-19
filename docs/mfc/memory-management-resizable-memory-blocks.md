---
title: メモリ管理:サイズ変更可能なメモリ ブロック
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 124a2599e1523d5393fcf6255c88de0fd8cd72cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219143"
---
# <a name="memory-management-resizable-memory-blocks"></a>メモリ管理:サイズ変更可能なメモリ ブロック

**新しい**と**削除**演算子は、この記事で説明されている[メモリ管理。例](../mfc/memory-management-examples.md)はの割り当てと解放の固定サイズのメモリ ブロックとオブジェクトによって適しています。 場合によっては、アプリケーションには、サイズ変更可能なメモリ ブロックが必要があります。 標準の C ランタイム ライブラリ関数を使用する必要があります[malloc](../c-runtime-library/reference/malloc.md)、 [realloc](../c-runtime-library/reference/realloc.md)、および[無料](../c-runtime-library/reference/free.md)ヒープ上のサイズ変更可能なメモリ ブロックを管理します。

> [!IMPORTANT]
>  混合、**新しい**と**削除**MFC のデバッグ バージョンで、破損したメモリ内と同じメモリ ブロックのサイズ変更可能なメモリ割り当て関数と演算子になります。 使用しないようにする**realloc**で割り当てられたメモリ ブロックに**新しい**します。 同様に、割り当てる必要がありますいないメモリ ブロックを**新しい**演算子の削除と**無料**を使用して、または、**削除**で割り当てられたメモリブロックの演算子**malloc**します。

## <a name="see-also"></a>関連項目

[メモリ管理: ヒープの割り当て](../mfc/memory-management-heap-allocation.md)
