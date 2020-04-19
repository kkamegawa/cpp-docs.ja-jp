---
title: CSpinButtonCtrl の使い方
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: a2a12672f0e70248e135bdd177b76589b6197c75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513467"
---
# <a name="using-cspinbuttonctrl"></a>CSpinButtonCtrl の使い方

*スピンボタン*コントロール (*アップダウン*コントロールとも呼ばれます) は、ユーザーがクリックして値を調整できる矢印のペアを提供します。 この値は、現在の*位置*と呼ばれます。 位置は、スピンボタンの範囲内にとどまります。 ユーザーが上矢印をクリックすると、位置が最大値に移動します。また、ユーザーが下矢印をクリックすると、位置が最小値に移動します。

スピンボタンコントロールは、MFC で[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)クラスによって表されます。

> [!NOTE]
>  既定では、スピンボタンの範囲の最大値はゼロ (0)、最小値は100に設定されています。 最大値が最小値より小さいため、上矢印をクリックすると位置が減少し、下矢印をクリックすると位置が増加します。 これらの値を調整するには、 [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)を使用します。

通常、現在の位置は、コンパニオンコントロールに表示されます。 コンパニオンコントロールは、関連*ウィンドウ*と呼ばれます。 スピンボタンコントロールの図解は、「Windows SDK の[アップダウンコントロールについ](/windows/win32/Controls/up-down-controls)て」を参照してください。

スピンコントロールと編集コントロールの関連ウィンドウを作成するには、Visual Studio で、まず、エディットコントロールをダイアログボックスまたはウィンドウにドラッグし、次にスピンコントロールをドラッグします。 スピンコントロールを選択し、 **[Auto buddy]** と **[set Buddy Integer]** プロパティを**True**に設定します。 また、 **Alignment**プロパティも設定します。最も一般的なのは、**右揃え**です。 これらの設定を使用すると、エディットコントロールは、タブオーダーの編集コントロールの直前にあるため、[関連] ウィンドウとして設定されます。 エディットコントロールに整数が表示され、エディットコントロールの右側にスピンコントロールが埋め込まれます。 必要に応じて、 [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)メソッドを使用して、スピンコントロールの有効な範囲を設定できます。 スピンコントロールと関連ウィンドウ間の通信には、データが直接交換されるため、イベントハンドラーは必要ありません。 他の目的でスピンコントロールを使用する場合 (たとえば、ウィンドウやダイアログボックスのシーケンスをページ分割する場合など) は、UDN_DELTAPOS メッセージのハンドラーを追加し、そこでカスタムアクションを実行します。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [スピン ボタンのスタイル](../mfc/spin-button-styles.md)

- [スピン ボタンのメンバー関数](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>関連項目

[コントロール](../mfc/controls-mfc.md)
