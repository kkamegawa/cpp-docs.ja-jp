---
title: クリッピングを行わないデバイス コンテキストの使用
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411813"
---
# <a name="using-an-unclipped-device-context"></a>クリッピングを行わないデバイス コンテキストの使用

コントロールは、そのクライアントの四角形の外側は描画されませんがわかっている場合への呼び出しを無効にして小さくても検出可能な速度向上を実現できます`IntersectClipRect`はによって作成される`COleControl`します。 これを行うには、削除、 *clipPaintDC*フラグによって返されるフラグのセットから[オン](../mfc/reference/colecontrol-class.md#getcontrolflags)します。 例:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

選択した場合、このフラグを削除するコードが自動的に生成、**クリッピングを行わないデバイス コンテキスト**オプションを[コントロール設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX コントロール ウィザードを使用して、コントロールを作成するときに、ページします。

ウィンドウなしのアクティベーションを使用している場合は、この最適化に影響はありません。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)
