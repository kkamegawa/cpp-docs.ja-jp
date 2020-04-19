---
title: スピン ボタンのメンバー関数
ms.date: 11/04/2016
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
ms.openlocfilehash: 5ad6f529762e77e1cf1c00f41eea0add5d196fbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307264"
---
# <a name="spin-button-member-functions"></a>スピン ボタンのメンバー関数

スピン コントロールで使用できるいくつかのメンバー関数は ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md))。 スピン ボタンの次の属性を変更するのにには、これらの関数を使用します。

- **高速化**ユーザーが矢印ボタンを押したときに、位置が変化率を調整することができます。 高速化を使用するには、使用、 [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel)と[GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel)メンバー関数。

- **基本**連動ウィンドウのキャプションの位置の表示に使用される基本 (10 または 16) を変更することができます。 使用して、ベースを使用する、 [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase)と[SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase)メンバー関数。

- **ウィンドウを友人**連動ウィンドウを動的に設定することができます。 使用してクエリを実行したり、どのコントロールが連動ウィンドウを変更したり、 [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy)と[SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy)メンバー関数。

- **位置**クエリを実行し、位置を変更することができます。 位置を直接操作するには、使用、 [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos)と[SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos)メンバー関数。 アップダウン コントロールのキャプション (たとえば、例では、友人がエディット コントロールである)、変更したため`GetPos`現在キャプションを取得し、適宜位置を調整します。

- **範囲**スピン ボタンの最大値と最小の位置を変更することができます。 既定では、最大値は 0 に設定し、最小値が 100 に設定します。 既定の最大値は、既定の最小値未満であるため、矢印ボタンのアクションは逆です。 使用して範囲を設定は通常、 [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)メンバー関数。 クエリ範囲を使用する[GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange)します。

## <a name="see-also"></a>関連項目

[CSpinButtonCtrl の使い方](../mfc/using-cspinbuttonctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
