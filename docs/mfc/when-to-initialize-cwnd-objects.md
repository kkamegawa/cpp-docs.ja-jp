---
title: CWnd オブジェクトの初期化のタイミング
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: aa396ade2e8ab4e1245e161423de7bd5bfafaaf8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405717"
---
# <a name="when-to-initialize-cwnd-objects"></a>CWnd オブジェクトの初期化のタイミング

独自の子ウィンドウを作成またはのコンス トラクターで、Windows API 関数を呼び出すことはできません、 `CWnd`-派生オブジェクト。 これは、ため、`HWND`の`CWnd`オブジェクトが作成されていません。 子ウィンドウの追加などの Windows 固有性の高い初期化を行う必要がある、 [OnCreate](../mfc/reference/cwnd-class.md#oncreate)メッセージ ハンドラー。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメント フレーム ウィンドウの作成](../mfc/creating-document-frame-windows.md)

- [ドキュメント/ビューの作成](../mfc/document-view-creation.md)

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
