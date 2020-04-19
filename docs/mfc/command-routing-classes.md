---
title: コマンド ルーティング クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: 264e931ba0468cdc44f27c55e5d259948c5392b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406055"
---
# <a name="command-routing-classes"></a>コマンド ルーティング クラス

ように、ユーザーは、メニューまたはマウスでコントロール バーのボタンを選択して、アプリケーションと対話する、アプリケーションは、適切なコマンド ターゲット オブジェクトに影響を受けるユーザー インターフェイス オブジェクトからメッセージを送信します。 コマンド ターゲット クラスから派生した`CCmdTarget`含める[CWinApp](../mfc/reference/cwinapp-class.md)、 [CWnd](../mfc/reference/cwnd-class.md)、 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)、 [CDocument](../mfc/reference/cdocument-class.md)、 [CView](../mfc/reference/cview-class.md)、およびそれらから派生したクラス。 フレームワークでは、コマンドの自動ルーティング コマンドは、アプリケーションで現在アクティブに最も適切なオブジェクトで処理できるようにサポートしています。

クラスのオブジェクト`CCmdUI`コマンド ターゲットの更新コマンド UI に渡される ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) ハンドラーを使用する特定のコマンドのユーザー インターフェイスの状態を更新できます (たとえば、チェック、または削除するメニュー項目からチェック)。 メンバーの関数を呼び出して、 `CCmdUI` UI オブジェクトの状態を更新するオブジェクト。 このプロセスは、特定のコマンドに関連付けられている UI オブジェクトがメニュー項目をボタン、またはその両方であるかどうかは同じです。

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
受信およびメッセージに応答できるオブジェクトのすべてのクラスの基本クラスとして機能します。

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
メニュー項目やコントロール バーのボタンなどのユーザー インターフェイス オブジェクトを更新するためのプログラム インターフェイスを提供します。 コマンド ターゲット オブジェクトは、有効、無効にします、チェック、またはこのオブジェクトとユーザー インターフェイス オブジェクトをクリアを。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
