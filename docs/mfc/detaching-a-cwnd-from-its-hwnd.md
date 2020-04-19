---
title: CWnd と HWND の分離
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: 259af94958f88643e9c3ce725b25c4e92cc38226
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394573"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>CWnd と HWND の分離

オブジェクトを回避する必要がある場合`HWND`リレーションシップ、MFC 別提供`CWnd`メンバー関数は、[デタッチ](../mfc/reference/cwnd-class.md#detach)Windows のウィンドウから C++ ウィンドウ オブジェクトを切断します。 これは、デストラクターが、オブジェクトが破棄されると、Windows のウィンドウを破棄することを防ぎます。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ウィンドウの作成](../mfc/creating-windows.md)

- [ウィンドウの破棄順序](../mfc/window-destruction-sequence.md)

- [割り当てとウィンドウ メモリの解放](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>関連項目

[Window オブジェクト](../mfc/window-objects.md)
