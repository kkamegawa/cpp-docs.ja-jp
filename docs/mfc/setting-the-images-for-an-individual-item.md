---
title: 各項目のイメージの設定
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511277"
---
# <a name="setting-the-images-for-an-individual-item"></a>各項目のイメージの設定

拡張コンボボックス項目で使用されるさまざまな種類のイメージは、 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)構造体の*iImage*、 *iselectedimage*、および*iオーバーレイ*メンバーの値によって決定されます。 各値は、コントロールの関連付けられたイメージリスト内のイメージのインデックスです。 既定では、これらのメンバーは0に設定されているため、コントロールには項目のイメージが表示されません。 特定の項目に対してイメージを使用する場合は、コンボボックス項目を挿入するとき、または既存のコンボボックス項目を変更して、構造を適宜変更することができます。

## <a name="setting-the-image-for-a-new-item"></a>新しい項目のイメージの設定

新しい項目を挿入する場合は、適切な値を使用して*iImage*、 *iselectedimage*、および*iオーバーレイ*構造体のメンバーを初期化し、 [CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)への呼び出しを使用して項目を挿入します。

次の例では、新しい拡張コンボボックス項目`cbi`() を拡張コンボボックスコントロール (`m_comboEx`) に挿入し、3つのイメージ状態すべてのインデックスを提供します。

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>既存の項目のイメージを設定する

既存のアイテムを変更する場合は、 **COMBOBOXEXITEM**構造体の*mask*メンバーを使用する必要があります。

#### <a name="to-modify-an-existing-item-to-use-images"></a>既存の項目を変更してイメージを使用するには

1. **COMBOBOXEXITEM**構造体を宣言し、変更対象の値に*mask*データメンバーを設定します。

1. この構造体を使用して、 [CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem)を呼び出します。

1. 適切な値を使用して、新しく返された構造体の*mask*、 *IImage*、および*iselectedimage*メンバーを変更します。

1. [CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem)を呼び出して、変更された構造体を渡します。

次の例では、3番目の拡張コンボボックス項目の選択したイメージと選択されていないイメージをスワップすることにより、この手順を示します。

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>関連項目

[CComboBoxEx の使い方](../mfc/using-ccomboboxex.md)<br/>
[コントロール](../mfc/controls-mfc.md)
