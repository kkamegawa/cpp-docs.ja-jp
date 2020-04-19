---
title: ちらつきなしのアクティベーションの提供
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: fad24d6201260e87ff32436752a9fbf035e822ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297048"
---
# <a name="providing-flicker-free-activation"></a>ちらつきなしのアクティベーションの提供

コントロール、非アクティブとアクティブの状態で同一の描画 (およびウィンドウなしのアクティベーションを使用しない) 場合に、描画操作と、非アクティブの間で移行するときに通常発生するちらつきを除外できます。およびアクティブ状態です。 これを行うには、 **noFlickerActivate**フラグによって返される一連のフラグ[オン](../mfc/reference/colecontrol-class.md#getcontrolflags)します。 例:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

選択した場合、このフラグを追加するコードが自動的に生成、**ちらつきなしのアクティベーション**オプションを[コントロール設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX コントロール ウィザードを使用して、コントロールを作成するときのページします。

ウィンドウなしのアクティベーションを使用している場合は、この最適化に影響はありません。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)
