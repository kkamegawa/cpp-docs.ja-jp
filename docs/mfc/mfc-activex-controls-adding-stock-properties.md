---
title: MFC ActiveX コントロール:ストック プロパティの追加
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225344"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX コントロール:ストック プロパティの追加

ストック プロパティは、クラスによって既に実装されている点で、カスタム プロパティとは異なります。`COleControl`します。 `COleControl` コントロールの共通プロパティをサポートする定義済みのメンバー関数が含まれています。 いくつかの一般的なプロパティには、コントロールのキャプションと前景色と背景色が含まれます。 その他のストック プロパティについては、次を参照してください。[プロパティの追加ウィザードでサポートするストック プロパティ](#_core_stock_properties_supported_by_classwizard)この記事で後述します。 ストック プロパティが常に付きます DISP_STOCKPROP のディスパッチ マップ エントリ。

この記事では、プロパティの追加ウィザードを使用して ActiveX コントロールを (この例では、キャプション) ではストック プロパティを追加する方法について説明し、結果として得られるコードの変更について説明します。 ここでは、次の内容について説明します。

- [ストック プロパティを追加するプロパティの追加ウィザードを使用します。](#_core_using_classwizard_to_add_a_stock_property)

- [ストック プロパティのプロパティ ウィザードによる変更を追加します。](#_core_classwizard_changes_for_stock_properties)

- [プロパティの追加ウィザードでサポートされているストック プロパティ](#_core_stock_properties_supported_by_classwizard)

- [ストック プロパティと通知](#_core_stock_properties_and_notification)

- [色のプロパティ](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic のカスタム コントロールには、通常、上、左、幅、高さ、配置、タグ、名前、TabIndex、TabStop、および親などのプロパティがあります。 ActiveX コントロール コンテナー、ただし、実装する責任がこれらのコントロール プロパティと、したがって ActiveX コントロールがこれらのプロパティをサポートする必要があります。

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用して、プロパティの追加ウィザード、ストック プロパティを追加するには

ストック プロパティを追加するために、カスタム プロパティを追加するよりも少ないコードが必要です、プロパティはによって自動的に処理のサポート`COleControl`します。 次の手順では、ActiveX コントロール フレームワークへのストック キャプション プロパティの追加について説明し、その他のストック プロパティを追加できます。 キャプションのストック プロパティが選択されている名前に置き換えます。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用して株式の Caption プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

   開き、[プロパティの追加ウィザード](../ide/names-add-property-wizard.md)します。

1. **プロパティ名**ボックスで、**キャプション**します。

1. **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_stock_properties"></a> ストック プロパティのプロパティ ウィザードによる変更を追加します。

`COleControl`サポートするストック プロパティ、プロパティの追加ウィザードには、任意の方法で、クラス宣言は変わりません。 ディスパッチ マップにプロパティを追加します。 プロパティの追加ウィザードの実装であると、コントロールのディスパッチ マップに次の行を追加します (します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

コントロールのインターフェイスの説明に、次の行が追加されます (します。IDL) ファイル。

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

特定の ID の Caption プロパティに割り当てます。 この行 プロパティが連結可能であり、値を変更する前に、データベースからアクセス許可を要求ことに注意してください。

これによりの Caption プロパティの使用可能なコントロールのユーザー。 ストック プロパティの値を使用するメンバー変数またはのメンバー関数にアクセス、`COleControl`基本クラス。 これらのメンバー変数とメンバー関数の詳細については、次のセクションでは、プロパティの追加ウィザードでサポートするストック プロパティを参照してください。

##  <a name="_core_stock_properties_supported_by_classwizard"></a> [ストック プロパティ] でサポートされている、プロパティの追加ウィザード

`COleControl`クラスには、9 つのストック プロパティが用意されています。 プロパティの追加ウィザードを使用して、必要なプロパティを追加することができます。

|プロパティ|ディスパッチ マップ エントリ|値にアクセスする方法|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|値としてアクセスできるように`m_sAppearance`します。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|呼び出すことによってアクセス可能な値`GetBackColor`します。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|値としてアクセスできるように`m_sBorderStyle`します。|
|`Caption`|DISP_STOCKPROP_CAPTION( )|呼び出すことによってアクセス可能な値`InternalGetText`します。|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|値としてアクセスできるように`m_bEnabled`します。|
|`Font`|DISP_STOCKPROP_FONT( )|記事をご覧ください[MFC ActiveX コントロール。フォントを使用して](../mfc/mfc-activex-controls-using-fonts.md)の使用量。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|呼び出すことによってアクセス可能な値`GetForeColor`します。|
|`hWnd`|DISP_STOCKPROP_HWND( )|値としてアクセスできるように`m_hWnd`します。|
|`Text`|DISP_STOCKPROP_TEXT( )|呼び出すことによってアクセス可能な値`InternalGetText`します。 このプロパティは、同じ`Caption`プロパティ名を除く。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|値としてアクセスできるように`m_lReadyState`または `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> ストック プロパティと通知

ほとんどのストック プロパティでは、オーバーライド可能な通知関数があります。 たとえば、たびに、`BackColor`プロパティを変更すると、`OnBackColorChanged`関数 (コントロール クラスのメンバー関数) が呼び出されます。 既定の実装 (で`COleControl`) 呼び出し`InvalidateControl`します。 このような状況への応答で追加のアクションを実行する場合は、この関数をオーバーライドします。

##  <a name="_core_color_properties"></a> 色のプロパティ

素材を使用する`ForeColor`と`BackColor`プロパティ、または、独自のカスタムの色のプロパティ、コントロールを描画するときにします。 色のプロパティを使用する呼び出し、 [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor)メンバー関数。 この関数のパラメーターは、色プロパティと、オプションのパレット ハンドルの値です。 戻り値は、 **COLORREF** GDI に渡すことができる値などの関数、`SetTextColor`と`CreateSolidBrush`します。

素材の色値`ForeColor`と`BackColor`プロパティは、いずれかを呼び出すことによってアクセスが、`GetForeColor`または`GetBackColor`関数は、それぞれします。

次の例では、コントロールを描画するときに、これら 2 つの色のプロパティを使用してを示します。 一時的な初期化**COLORREF**変数と`CBrush`オブジェクトへの呼び出しを`TranslateColor`: 1 つを使用して、`ForeColor`プロパティおよびその他の使用方法、`BackColor`プロパティ。 一時的な`CBrush`コントロールの四角形を描画するオブジェクトを使用してを使用してテキストの色を設定し、`ForeColor`プロパティ。

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: プロパティ](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)
