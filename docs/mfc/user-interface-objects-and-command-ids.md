---
title: ユーザー インターフェイス オブジェクトとコマンド ID
ms.date: 11/19/2018
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
ms.openlocfilehash: 54372facc51062add122c1db2e01e3081127512e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180616"
---
# <a name="user-interface-objects-and-command-ids"></a>ユーザー インターフェイス オブジェクトとコマンド ID

メニュー項目、ツール バー ボタン、およびアクセラレータ キーが「ユーザー インターフェイス オブジェクト」コマンドを生成できます。 このような各ユーザー インターフェイス オブジェクトが ID コマンド オブジェクトとコマンドを同じ ID を割り当てることで、ユーザー インターフェイス オブジェクトに関連付けます。 説明したよう[メッセージ](../mfc/messages.md)コマンドは、特別なメッセージとして実装されます。 「コマンド フレームワーク内の」次の図は、フレームワークがコマンドを管理する方法を示します。 ときに、コマンドを生成、ユーザー インターフェイス オブジェクトなど`ID_EDIT_CLEAR_ALL`は、アプリケーション内のオブジェクトのいずれかのコマンドを処理する-ドキュメント オブジェクトの次の図の`OnEditClearAll`ドキュメントのメッセージ マップを使用して関数が呼び出されます。

![フレームワークにおけるコマンド](../mfc/media/vc385p1.gif "フレームワーク内のコマンド") <br/>
フレームワークにおけるコマンド

「コマンド更新フレームワーク内の」次の図は、MFC がメニュー項目とツール バー ボタンなどのユーザー インターフェイス オブジェクトを更新する方法を示します。 メニューになると停止、またはツール バー ボタンの場合、アイドル ループの中に、前に、MFC は、update コマンドをルーティングします。 ドキュメント オブジェクトがその更新コマンド ハンドラーを呼び出す次の図に`OnUpdateEditClearAll`を有効にまたはユーザー インターフェイス オブジェクトを無効にします。

![コマンド更新フレームワークで](../mfc/media/vc385p2.png "コマンド フレームワークでの更新") <br/>
フレームワーク内のコマンド更新

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)
