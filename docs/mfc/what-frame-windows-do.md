---
title: フレーム ウィンドウの機能
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: 594700ef1cbe0030bbe452adaa40b29b4a72f4d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405678"
---
# <a name="what-frame-windows-do"></a>フレーム ウィンドウの機能

フレーム ウィンドウは単に、ビューのフレーム化、だけでなく、そのビューと、アプリケーションのフレームの調整に関連する多数のタスクを担当します。 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)と[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)継承[CFrameWnd](../mfc/reference/cframewnd-class.md)があるため、`CFrameWnd`機能だけではなく、新しい機能を追加します。 子ウィンドウの例には、ビュー、ボタン、リスト ボックス、およびコントロール バー、ツールバー、ステータス バー、およびダイアログ バーを含むなどのコントロールが含まれます。

フレーム ウィンドウは、その子ウィンドウのレイアウトの管理を担当します。 MFC フレームワークでは、フレーム ウィンドウは、クライアント領域内で、コントロール バー、ビュー、およびその他の子ウィンドウを配置します。

また、フレーム ウィンドウ、コマンドをビューに転送し、windows のコントロールから通知メッセージに応答できます。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [(これらに適合させる方法、フレーム ウィンドウ) コントロール バー](../mfc/control-bars.md)

- [メニューのコントロール バー、およびアクセラレータ (それらに適合させる方法、フレーム ウィンドウ) の管理](../mfc/managing-menus-control-bars-and-accelerators.md)

- [(そのビューを他のコマンド ターゲット フレーム ウィンドウ) からのコマンド ルーティング](../mfc/command-routing.md)

- [ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)

- [コントロール バー](../mfc/control-bars.md)

- [コントロール](../mfc/controls-mfc.md)

## <a name="see-also"></a>関連項目

[フレーム ウィンドウ](../mfc/frame-windows.md)
