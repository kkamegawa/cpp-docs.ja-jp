---
title: ウィンドウ メモリの割り当てと解放
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394703"
---
# <a name="allocating-and-deallocating-window-memory"></a>ウィンドウ メモリの割り当てと解放

C++ を使用しないでください**削除**フレーム ウィンドウまたはビューを破棄する演算子。 代わりに、`CWnd`メンバー関数は`DestroyWindow`します。 フレーム ウィンドウ、そのため、割り当てる必要がある演算子でヒープに**新しい**します。 フレーム ウィンドウのスタック フレームにまたはグローバルに割り当てるときは注意します。 他のウィンドウは、可能な限りのスタック フレームに割り当てる必要があります。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ウィンドウの作成](../mfc/creating-windows.md)

- [ウィンドウの破棄順序](../mfc/window-destruction-sequence.md)

- [Cwnd と HWND の分離](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>関連項目

[ウィンドウ オブジェクトの破棄](../mfc/destroying-window-objects.md)
