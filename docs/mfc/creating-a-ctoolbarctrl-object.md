---
title: CToolBarCtrl オブジェクトの作成
ms.date: 11/04/2016
f1_keywords:
- CToolBarCtrl
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: d0f41731e3a4db7b15d4f2a7ebaac94135d5350d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406133"
---
# <a name="creating-a-ctoolbarctrl-object"></a>CToolBarCtrl オブジェクトの作成

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクトに複数の内部データ構造を含める-ボタン イメージのビットマップの一覧、ボタンのラベルの文字列のリスト、および一連の`TBBUTTON`構造-イメージを関連付けたり、位置、スタイル、状態、文字列とボタンのコマンド ID。 これらのデータ構造の要素のそれぞれは、0 から始まるインデックスによって呼ばれます。 使用する前に、`CToolBarCtrl`オブジェクトに、これらのデータ構造を設定する必要があります。 データ構造の一覧は、次を参照してください。[ツール バー コントロール](controls-mfc.md)Windows SDK に含まれています。 文字列の一覧は、ボタンのラベルに対してのみ使用できます。ツールバーから文字列を取得することはできません。

使用する、`CToolBarCtrl`オブジェクトに、次の手順を通常になります。

### <a name="to-use-a-ctoolbarctrl-object"></a>CToolBarCtrl オブジェクトを使用するには

1. 構築、 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)オブジェクト。

1. 呼び出す[作成](../mfc/reference/ctoolbarctrl-class.md#create)Windows ツール バー コモン コントロールを作成してに接続する、`CToolBarCtrl`オブジェクト。 ボタンのビットマップ イメージを使う場合、ボタンのビットマップ、ツールバーに追加を呼び出して[表示](../mfc/reference/ctoolbarctrl-class.md#addbitmap)します。 ボタンのラベルの文字列をする場合に文字列を追加、ツールバーを呼び出して[AddString](../mfc/reference/ctoolbarctrl-class.md#addstring)や[AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)します。 呼び出した後`AddString`や`AddStrings`、呼び出す必要があります[AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize)文字列または文字列が表示されるを取得するためにします。

1. 呼び出して、ツールバーにボタンの構造体を追加[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)します。

1. ツール ヒントを表示する場合は、処理**TTN_NEEDTEXT** 」の説明に従って、ツールバーのオーナー ウィンドウにメッセージ[ツール ヒントの通知の処理](../mfc/handling-tool-tip-notifications.md)します。

1. ユーザーがツールバーをカスタマイズできる場合は、処理、オーナー ウィンドウでの通知メッセージのカスタマイズ」の説明に従って[カスタマイズ通知の処理](../mfc/handling-customization-notifications.md)します。

## <a name="see-also"></a>関連項目

[CToolBarCtrl の使い方](../mfc/using-ctoolbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
