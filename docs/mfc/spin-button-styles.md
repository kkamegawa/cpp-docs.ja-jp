---
title: スピン ボタンのスタイル
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907856"
---
# <a name="spin-button-styles"></a>スピン ボタンのスタイル

スピンボタン ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) の設定の多くは、スタイルによって制御されます。 [クラスウィザード](reference/mfc-class-wizard.md)を使用して、次のスタイルを設定できます。

- **向き**垂直方向または水平方向。 矢印ボタンの向きを制御します。 UDS_HORZ スタイルに関連付けられています。

- **配置**未接続、左、または右のいずれかです。 スピンボタンの位置を制御します。 左と右にある [関連] ウィンドウの横にスピンボタンを配置します。 スピンボタンに合わせて、関連ウィンドウの幅が小さくなります。 UDS_ALIGNLEFT スタイルと UDS_ALIGNRIGHT スタイルに関連付けられています。

- **自動メンバー**は、前のウィンドウを自動的に [関連] ウィンドウとしてスピンボタンに選択します。 ダイアログテンプレートでは、これは、タブオーダーのスピンボタンの前にあるコントロールです。 UDS_AUTOBUDDY スタイルに関連付けられています。

- 関連する**整数の設定**現在の位置が変更されたときに、スピンコントロールが関連ウィンドウのキャプションをインクリメントおよびデクリメントします。 UDS_SETBUDDYINT スタイルに関連付けられています。

- **何千もありません**は、関連ウィンドウのキャプションの値に桁区切り記号を挿入しません。 UDS_NOTHOUSANDS スタイルに関連付けられています。

    > [!NOTE]
    >  ダイアログデータエクスチェンジ (DDX) を使用して、関連コントロールから整数値を取得する場合は、このスタイルを設定します。 `DDX_Text`には、桁区切り記号を埋め込むことはできません。

- **折り返し**値がコントロールの範囲を超えてインクリメントまたはデクリメントされると、位置が "wrap" になります。 UDS_WRAP スタイルに関連付けられています。

- **方向キー**上方向キーと下方向キーが押されたときに、スピンボタンが位置を増減するようにします。 UDS_ARROWKEYS スタイルに関連付けられています。

## <a name="see-also"></a>関連項目

[CSpinButtonCtrl の使い方](../mfc/using-cspinbuttonctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
