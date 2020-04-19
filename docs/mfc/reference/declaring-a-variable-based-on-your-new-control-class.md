---
title: 新しいコントロール クラスに基づいた変数の宣言
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: d550b80beb124f3d8ec36ba81dad1a9ca7e9fa15
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741617"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>新しいコントロール クラスに基づいた変数の宣言

MFC コントロール クラスを作成すると、それに基づいて変数を宣言することができます。 新しい変数のコンテキストを提供するには、は、ダイアログ エディターを開き、再利用可能なコントロールを使用する ダイアログ ボックスを編集する必要があります。 また、ダイアログ ボックスは、関連付けられているクラスを既にが必要です。 ダイアログ エディターを使用する方法の詳細については、次を参照してください。[ダイアログ エディター](../../windows/dialog-editor.md)します。

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>再利用可能なクラスに基づいた変数を宣言するには

1. ダイアログ ボックスを編集している間には、ダイアログ ボックスの上にコントロールのツールバーから、新しいコントロールの基底クラスと同じ型のコントロールをドラッグします。

1. ドロップのコントロールの上にマウス ポインターを置きます。

1. CTRL キーを押しながらコントロールをダブルクリックします。

   [メンバー変数の追加](../../ide/add-member-variable-wizard.md) ダイアログ ボックスが表示されます。

1. **アクセス**ボックスで、コントロールの適切なアクセス権を選択します。

1. をクリックして、**コントロール変数**チェック ボックスをオンします。

1. **変数名**ボックスに、名前を入力します。

1. [**カテゴリ**、] をクリックして**コントロール**します。

1. **コントロール ID**一覧で、追加したコントロールを選択します。 **変数の型**一覧は、適切な変数の型を表示する必要があります、**コントロール型**ボックスは、適切なコントロール型を表示する必要があります。

9. **コメント**ボックスで、コードに表示する任意のコメントを追加します。

10. **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

[マップ (関数にメッセージを)](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[メンバー関数の追加](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[メンバー変数の追加](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[仮想関数のオーバーライド](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC メッセージ ハンドラー](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[クラス各部へのジャンプ](../../ide/navigate-code-cpp.md)
