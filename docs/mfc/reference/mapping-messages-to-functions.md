---
title: 関数へのメッセージの割り当て
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 4a76e28bddda0ad3385ab2110e201d652c0623df
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907877"
---
# <a name="mapping-messages-to-functions"></a>関数へのメッセージの割り当て

[クラスウィザード](mfc-class-wizard.md)を使用すると、メッセージハンドラー (MFC ユーザーインターフェイスクラスのメンバー関数) をアプリケーションのリソースによって生成されるメッセージにバインドできます。 これらは、 [MFC メッセージマップ](../../mfc/messages-and-commands-in-the-framework.md)を使用してバインディングを作成します。

クラスビューを使用して、いずれかのフレームワーククラスから派生した新しいクラスを作成すると、指定したヘッダー (.h) ファイルと実装 (.cpp) ファイルに、完全な機能を持つクラスが自動的に配置されます。

> [!NOTE]
>  メッセージを処理しない新しいクラスを追加するには、テキストエディターで直接クラスを作成します。

### <a name="to-define-or-remove-a-message-handler-using-the-class-wizard"></a>クラスウィザードを使用してメッセージハンドラーを定義または削除するには

1. **クラスビュー**で、クラスを右クリックします。

1. コンテキストメニューで、[[クラスウィザード](mfc-class-wizard.md)] を選択します。

## <a name="see-also"></a>関連項目

[MFC メッセージ ハンドラー](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[メンバー関数の追加](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[メンバー変数の追加](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[仮想関数のオーバーライド](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[クラス各部へのジャンプ](../../ide/navigate-code-cpp.md)
