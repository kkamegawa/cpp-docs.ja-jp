---
title: コマンド以外のメッセージのハンドラー検索方法
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: 4b9fb0a72b330380f0207db9968199a7e4c3d9b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407940"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>コマンド以外のメッセージのハンドラー検索方法

コマンドとは異なりは、標準 Windows メッセージは、チェーン コマンド ターゲットでルーティングされませんが、Windows メッセージを送信する先のウィンドウで、通常は処理されます。 メイン フレーム ウィンドウ、MDI 子ウィンドウ、標準のコントロール、ダイアログ ボックス、ビュー、または他の種類の子ウィンドウのウィンドウがあります。

実行時に、各 Windows ウィンドウがウィンドウのオブジェクトにアタッチ (から直接または間接的に派生した`CWnd`) を持つ独自の関連付けられているメッセージ マップおよびハンドラー関数。 フレームワークは、メッセージ マップを使用: コマンドと、メッセージの受信ハンドラーをマッピングします。

## <a name="see-also"></a>関連項目

[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)
