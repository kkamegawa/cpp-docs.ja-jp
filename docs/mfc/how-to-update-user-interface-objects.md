---
title: '方法: ユーザー インターフェイス オブジェクトを更新します。'
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
ms.openlocfilehash: 0dee9bb48c11cf061af60ebaf9a80c0123d339be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160277"
---
# <a name="how-to-update-user-interface-objects"></a>方法: ユーザー インターフェイス オブジェクトを更新します。

通常、メニュー項目とツール バー ボタンには、1 つ以上の状態があります。 たとえば、メニュー項目は灰色が現在のコンテキストで使用できない場合 (淡色)。 メニュー項目はオンまたはオフにもできます。 を使用できない場合、ツール バー ボタンを無効にできますもまたはチェックすることができます。

これらのアイテムによって処理されるコマンドをメニュー項目が生成する場合は、条件が変更を論理的には、プログラムと、たとえば、ドキュメントの状態を更新するユーザー、理にかなってドキュメントでメニュー項目を更新します。 おそらく、ドキュメントには、更新プログラムが基になる情報が含まれています。

コマンドに複数のユーザー インターフェイス オブジェクト (おそらくはメニュー項目とツールバーのボタン) がある場合は、同じハンドラー関数に両方ルーティングされます。 これには、1 か所で同等のユーザー インターフェイス オブジェクトのすべてのユーザー インターフェイス更新コードがカプセル化します。

フレームワークは、ユーザー インターフェイス オブジェクトを自動的に更新するための便利なインターフェイスを提供します。 その他の何らかの方法で更新を行うことができますが、提供されるインターフェイスは、効率的かつ簡単に使用します。

次のトピックでは、更新ハンドラーの使用について説明します。

- [更新ハンドラーが呼び出されるタイミング](../mfc/when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI マクロ](../mfc/on-update-command-ui-macro.md)

- [CCmdUI クラス](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>関連項目

[メニュー](../mfc/menus-mfc.md)
