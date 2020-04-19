---
title: ウィンドウ オブジェクトの破棄
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297243"
---
# <a name="destroying-window-objects"></a>ウィンドウ オブジェクトの破棄

注意が必要で独自の子ウィンドウのウィンドウで、ユーザーが終了すると、C++ ウィンドウ オブジェクトを破棄します。 これらのオブジェクトを破棄しないと、アプリケーションはメモリを復元できません。 さいわい、フレームワークは、フレーム ウィンドウ、ビュー、およびダイアログ ボックスの作成とウィンドウの破棄を管理します。 追加のウィンドウを作成する場合は、それらを破棄する必要があります。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ウィンドウの破棄順序](../mfc/window-destruction-sequence.md)

- [割り当てとウィンドウ メモリの解放](../mfc/allocating-and-deallocating-window-memory.md)

- [Cwnd と HWND の分離](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [一般的なウィンドウ作成順序](../mfc/general-window-creation-sequence.md)

- [フレーム ウィンドウの破棄](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>関連項目

[Window オブジェクト](../mfc/window-objects.md)
