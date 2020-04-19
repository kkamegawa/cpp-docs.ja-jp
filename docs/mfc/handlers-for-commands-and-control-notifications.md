---
title: コマンドとコントロール通知のハンドラー
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 43b6a517b680a5f6ff092337fbf3d90dd0115dd7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907981"
---
# <a name="handlers-for-commands-and-control-notifications"></a>コマンドとコントロール通知のハンドラー

コマンドまたはコントロール通知メッセージの既定のハンドラーはありません。 したがって、これらのメッセージカテゴリのハンドラーに名前を付けるには、規則によってのみバインドされます。 コマンドまたはコントロールの通知をハンドラーにマップすると、[クラスウィザード](reference/mfc-class-wizard.md)によって、コマンド ID またはコントロール通知コードに基づいて名前が提示されます。 提案された名前をそのまま使用するか、変更するか、置き換えることができます。

規則は、それらが表すユーザーインターフェイスオブジェクトの両方のカテゴリにハンドラー名を指定することを示しています。 したがって、[編集] メニューの [切り取り] コマンドのハンドラーは、という名前になります。

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Cut コマンドはアプリケーションで一般的に実装されているため、フレームワークは、Cut コマンドのコマンド ID を**ID_EDIT_CUT**として事前します。 定義済みのすべてのコマンド Id の一覧については、ファイル AFXRES.H を参照してください。始め. 詳細については、「[標準コマンド](../mfc/standard-commands.md)」を参照してください。

また、規則では、"My Button" というラベルが付いたボタンからの**BN_CLICKED**通知メッセージのハンドラーを提案します。

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

このコマンドは、アプリケーション固有のユーザーインターフェイスオブジェクトと同等であるため、 **IDC_MY_BUTTON**の ID に割り当てることができます。

どちらのカテゴリのメッセージも引数を取らず、値を返しません。

## <a name="see-also"></a>関連項目

[メッセージ ハンドラー関数の宣言](../mfc/declaring-message-handler-functions.md)
