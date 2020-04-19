---
title: 現在のビューの管理
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: a926a9e31f7c43ab625220a4d759f6d536c2a77f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173341"
---
# <a name="managing-the-current-view"></a>現在のビューの管理

フレーム ウィンドウの既定の実装の一部として、フレーム ウィンドウを現在アクティブなビューの追跡を保持します。 フレーム ウィンドウには、分割ウィンドウで、たとえば、複数のビューが含まれている場合、現在のビューは、使用中で最新のビューが。 アクティブなビューでは、Windows または現在の入力フォーカスのアクティブ ウィンドウ依存しません。

変更すると、アクティブなビュー、フレームワークは、呼び出すことによって、現在のビューの[OnActivateView](../mfc/reference/cview-class.md#onactivateview)メンバー関数。 表示されているかどうかを確認するアクティブ化または非アクティブに調べることで`OnActivateView`の*bActivate*パラメーター。 既定では、`OnActivateView`のアクティブ化に関する現在のビューにフォーカスを設定します。 オーバーライドできます`OnActivateView`ビューが非アクティブ化または再アクティブ化したときに、特別な処理を実行します。 たとえば、非アクティブで、その他のビューから、アクティブなビューを区別するために特別な視覚的な手掛かりを提供します。

フレーム ウィンドウは」の説明に従ってコマンドを現在の (アクティブ) のビューを転送[コマンド ルーティング](../mfc/command-routing.md)、標準のコマンド ルーティングの一部として。

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
