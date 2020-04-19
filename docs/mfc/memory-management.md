---
title: メモリ管理
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 5d81bd0a8bdd24059951cba5c8b69751b3d1db86
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508269"
---
# <a name="memory-management"></a>メモリ管理

この記事のグループでは、メモリ管理に関連する Microsoft Foundation Class ライブラリ (MFC) の汎用サービスを活用する方法について説明します。 メモリ割り当ては、フレーム割り当てとヒープ割り当てという2つの主なカテゴリに分けることができます。

2つの割り当て方法の主な違いの1つは、フレーム割り当てでは、通常は実際のメモリブロック自体を使用しますが、ヒープ割り当てでは常にメモリブロックへのポインターを指定するということです。 2つのスキームの大きな違いは、フレームオブジェクトが自動的に削除されるのに対し、ヒープオブジェクトはプログラマが明示的に削除する必要があることです。

Windows 用プログラムのメモリ管理に関する MFC 以外の情報については、Windows SDK の「[メモリ管理](/windows/win32/memory/memory-management)」を参照してください。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [フレーム割り当て](../mfc/memory-management-frame-allocation.md)

- [ヒープ割り当て](../mfc/memory-management-heap-allocation.md)

- [配列にメモリを割り当てる](../mfc/memory-management-examples.md)

- [ヒープからの配列のメモリの解放](../mfc/memory-management-examples.md)

- [データ構造のメモリの割り当て](../mfc/memory-management-examples.md)

- [オブジェクトのメモリの割り当て](../mfc/memory-management-examples.md)

- [サイズ変更可能メモリブロック](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)<br/>
[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
