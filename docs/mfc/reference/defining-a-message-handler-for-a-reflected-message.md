---
title: リフレクション メッセージ用のメッセージ ハンドラーの定義
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907939"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>リフレクション メッセージ用のメッセージ ハンドラーの定義

新しい MFC コントロールクラスを作成したら、それに対応するメッセージハンドラーを定義できます。 リフレクションされたメッセージハンドラーを使用すると、親によってメッセージが受信される前に、コントロールクラスで独自のメッセージを処理できます。 MFC の[CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)関数を使用すると、コントロールから親ウィンドウにメッセージを送信できます。

この機能を使用すると、たとえば、親ウィンドウに依存するのではなく、自身を再描画するリストボックスを作成することができます (オーナー描画)。 リフレクションされたメッセージの詳細については、「リフレクションされた[メッセージの処理](../../mfc/handling-reflected-messages.md)」を参照してください。

同じ機能を持つ[activex コントロール](../../mfc/activex-controls-on-the-internet.md)を作成するには、activex コントロール用のプロジェクトを作成する必要があります。

> [!NOTE]
>  次に示すように、クラスウィザードを使用して ActiveX コントロールのリフレクションメッセージ (OCM_*message*) を追加することはできません。 これらのメッセージは手動で追加する必要があります。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>クラスウィザードからリフレクションメッセージのメッセージハンドラーを定義するには

1. リスト、rebar コントロール、ツールバー、ツリーコントロールなどのコントロールを MFC プロジェクトに追加します。

1. クラスビューで、コントロールクラスの名前をクリックします。

1. [クラスウィザード](mfc-class-wizard.md)で、 **[クラス名]** ボックスの一覧にコントロールクラスの名前が表示されます。

1. **[メッセージ]** タブをクリックして、コントロールに追加できる Windows メッセージを表示します。

1. ハンドラーを定義するリフレクションメッセージを選択します。 反映されたメッセージには等号 (=) が付いています。

1. クラスウィザードの右側の列にあるセルをクリックすると、ハンドラーの提案された\<名前が [add >*handlername*] として表示されます。 (たとえば、 **= WM_CTLCOLOR**メッセージハンドラーは、add \<>**CTLCOLOR**) を提案します。

1. 同意する場合は、推奨される名前をクリックします。 ハンドラーがプロジェクトに追加されます。

1. メッセージハンドラーを編集または削除するには、手順 4. ~ 7. を繰り返します。 編集または削除するハンドラー名を含むセルをクリックし、適切なタスクをクリックします。

## <a name="see-also"></a>関連項目

[マップ (関数にメッセージを)](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[メンバー関数の追加](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[メンバー変数の追加](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[仮想関数のオーバーライド](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC メッセージ ハンドラー](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[クラス各部へのジャンプ](../../ide/navigate-code-cpp.md)
