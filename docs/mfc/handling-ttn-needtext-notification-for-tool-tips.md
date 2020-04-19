---
title: ツール ヒント用 TTN_NEEDTEXT 通知の処理
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: a63154f3da539676f31709899568b6486dc6017e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508531"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>ツール ヒント用 TTN_NEEDTEXT 通知の処理

[ツールヒントを有効](../mfc/enabling-tool-tips.md)にする際には、オーナーウィンドウのメッセージマップに次のエントリを追加することで、 **TTN_NEEDTEXT**メッセージを処理します。

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
このボタンにテキストが必要な場合に呼び出されるメンバー関数。

ツールヒントの ID は常に0であることに注意してください。

次のように、クラス定義でハンドラー関数を宣言します。

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

斜体のパラメーターは次のとおりです。

*ID*<br/>
通知を送信したコントロールの識別子。 使用しません。 コントロール id は、 **NMHDR**構造体から取得されます。

*pNMHDR*<br/>
[Nmttdispinfo](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow)構造体へのポインター。 この構造体の詳細につい[ては、TOOLTIPTEXT 構造体](../mfc/tooltiptext-structure.md)にも記載されています。

*pResult*<br/>
を返す前に設定できる結果コードへのポインター。 **TTN_NEEDTEXT**ハンドラーは、 *pResult*パラメーターを無視できます。

フォームビューの通知ハンドラーの例を次に示します。

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

呼び出し`EnableToolTips` (から`OnInitDialog`取得したこのフラグメント):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>関連項目

[CFrameWnd から派生していないウィンドウのツール ヒント](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
