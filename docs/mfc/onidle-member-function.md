---
title: OnIdle メンバー関数
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: c7cdd5cd2327be1b90e7fdb3694353acf8adcafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394565"
---
# <a name="onidle-member-function"></a>OnIdle メンバー関数

Windows メッセージが処理されていないときに、フレームワーク、 [CWinApp](../mfc/reference/cwinapp-class.md)メンバー関数は[OnIdle](../mfc/reference/cwinapp-class.md#onidle) (MFC ライブラリのリファレンスで説明)。

オーバーライド`OnIdle`バック グラウンド タスクを実行します。 既定のバージョンでは、ツール バー ボタンなどのユーザー インターフェイス オブジェクトの状態を更新し、その操作の過程で、フレームワークによって作成される一時オブジェクトのクリーンアップを実行します。 次の図は、メッセージ ループを呼び出す方法を示しています。`OnIdle`キューにメッセージがない場合にします。

![メッセージ ループ プロセス](../mfc/media/vc387c1.gif "メッセージ ループ プロセス") <br/>
メッセージ ループ

アイドル ループで実行できる操作についての詳細については、次を参照してください。[アイドル ループ プロセシング](../mfc/idle-loop-processing.md)します。

## <a name="see-also"></a>関連項目

[CWinApp: アプリケーション クラス](../mfc/cwinapp-the-application-class.md)
