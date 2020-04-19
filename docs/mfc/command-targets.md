---
title: コマンド ターゲット
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: ed3d6a68967dc7f4244f887ae34760fdb99fa7f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388515"
---
# <a name="command-targets"></a>コマンド ターゲット

図[フレームワークにおけるコマンド](../mfc/user-interface-objects-and-command-ids.md)メニュー項目と、オブジェクトがクリックされたときに、結果として得られるコマンドを実行するフレームワークから呼び出されるハンドラー関数などのユーザー インターフェイス オブジェクト間の接続を示しています。

Windows では、メッセージのハンドラーが呼び出され、ウィンドウに直接コマンド メッセージではないメッセージを送信します。 フレームワークが複数の候補のオブジェクトにコマンドをルーティングするただし、-「コマンド ターゲット」と呼ばれる、うちの 1 つ通常コマンドのハンドラーを呼び出します。 ハンドラー関数の動作のコマンドと標準の Windows メッセージの両方に対して同じ方法で説明したように、呼び出されるメカニズムが異なり、[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)します。

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)
