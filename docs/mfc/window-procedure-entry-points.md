---
title: ウィンドウ プロシージャのエントリ ポイント
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 6d91e2c432588afc5a84f7189fa87a7fc2531b1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372013"
---
# <a name="window-procedure-entry-points"></a>ウィンドウ プロシージャのエントリ ポイント

MFC のウィンドウ プロシージャ、特別なウィンドウ プロシージャの実装を含むモジュールの静的リンクを保護します。 MFC のモジュールがリンクされている場合、リンケージは自動的に発生します。 このウィンドウの手順では、AFX_MANAGE_STATE マクロを使用して、有効なモジュールの状態が正しく設定し、呼び出す`AfxWndProc`、順番にデリゲートを`WindowProc`メンバー関数は、適切な`CWnd`-派生オブジェクト。

## <a name="see-also"></a>関連項目

[MFC モジュールの状態データの管理](../mfc/managing-the-state-data-of-mfc-modules.md)
