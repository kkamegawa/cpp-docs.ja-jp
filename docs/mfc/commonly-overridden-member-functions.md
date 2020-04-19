---
title: 通常オーバーライドされるメンバー関数
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 51a647bb50415af71d6d148d3139f906f503ee2a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685825"
---
# <a name="commonly-overridden-member-functions"></a>通常オーバーライドされるメンバー関数

次の表に、 `CDialog`の派生クラスでオーバーライドされる可能性の高いメンバー関数を示します。

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>クラス CDialog の通常オーバーライドされるメンバー関数

|メンバー関数|応答メッセージ|上書きの目的|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|ダイアログボックスのコントロールを初期化します。|
|`OnOK`|ボタン**IDOK**の場合は**BN_CLICKED**|ユーザーが [OK] ボタンをクリックしたときに応答します。|
|`OnCancel`|ボタン**IDCANCEL**の**BN_CLICKED**|ユーザーが [キャンセル] ボタンをクリックしたときに応答します。|

`OnInitDialog`、 `OnOK`、および`OnCancel`は仮想関数です。 これらをオーバーライドするには、 [MFC クラスウィザード](reference/mfc-class-wizard.md)を使用して、派生ダイアログクラスでオーバーライドする関数を宣言します。

`OnInitDialog`は、ダイアログボックスが表示される直前に呼び出されます。 オーバーライドから既定`OnInitDialog`のハンドラーを呼び出す必要があります。通常は、ハンドラーの最初のアクションです。 既定では`OnInitDialog` 、は、ダイアログボックスの最初のコントロールにフォーカスを設定する必要があることを示すために**TRUE**を返します。

`OnOK`は通常、モードレスではオーバーライドされますが、モーダルダイアログボックスには上書きされません。 モーダルダイアログボックスに対してこのハンドラーをオーバーライドする場合は、オーバーライドから基本クラスバージョンを呼び出して、 `EndDialog`が呼び出されるように`EndDialog`するか、自分で呼び出す必要があります。

`OnCancel`は通常、モードレスダイアログボックスでオーバーライドされます。

これらのメンバー関数の詳細については、 *Mfc リファレンス*のクラス[CDialog](../mfc/reference/cdialog-class.md)に関する記事と、 [mfc でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)に関する説明を参照してください。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[通常追加されるメンバー関数](../mfc/commonly-added-member-functions.md)
