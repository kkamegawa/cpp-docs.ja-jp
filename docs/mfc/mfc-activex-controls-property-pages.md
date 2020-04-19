---
title: MFC ActiveX コントロール:プロパティ ページ
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 3fe092e412cf11f7bf8600e8d0d7d43abb0e11c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239964"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX コントロール:プロパティ ページ

プロパティ ページを使用すると、ActiveX コントロールのユーザーを表示および ActiveX コントロールのプロパティを変更します。 これらのプロパティは、表示およびコントロールのプロパティを編集するため、カスタマイズされたグラフィカル インターフェイスを提供する 1 つまたは複数のプロパティ ページを含む、コントロールのプロパティのダイアログ ボックスを呼び出すことによってアクセスされます。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

2 つの方法では、ActiveX コントロールのプロパティ ページが表示されます。

- ときに、コントロールのプロパティの動詞 (**OLEIVERB_PROPERTIES**) が呼び出されると、コントロールはコントロールのプロパティ ページを含むモーダル プロパティ ダイアログ ボックスが表示されます。

- コンテナーは、選択したコントロールのプロパティ ページを表示する独自のモードレス ダイアログ ボックスを表示できます。

タブのプロパティ ページ、および一連のプロパティ ページ ダイアログを閉じるなどの一般的なタスクを実行するボタンの切り替えは、現在のプロパティ ページを表示するための領域で構成されます (次の図に示す) のプロパティ ダイアログ ボックス、加えられた変更をキャンセルまたは ActiveX コントロールにすぐに変更を適用します。

![Circ3 のプロパティ ダイアログ ボックス](../mfc/media/vc373i1.gif "Circ3 のプロパティ ダイアログ ボックス") <br/>
プロパティ ダイアログ ボックス

この記事では、ActiveX コントロールのプロパティ ページの使用に関連するトピックについて説明します。 不足している機能には次が含まれます。

- [ActiveX コントロールの既定のプロパティ ページを実装します。](#_core_implementing_the_default_property_page)

- [プロパティ ページにコントロールを追加します。](#_core_adding_controls_to_a_property_page)

- [DoDataExchange 関数をカスタマイズします。](#_core_customizing_the_dodataexchange_function)

ActiveX コントロールのプロパティ ページの使用に関する詳細については、次の記事を参照してください。

- [MFC ActiveX コントロール: 別のカスタム プロパティ ページの追加](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX コントロール: ストック プロパティ ページの使用](../mfc/mfc-activex-controls-using-stock-property-pages.md)

ActiveX コントロール以外の MFC アプリケーションでプロパティ シートの使用方法の詳細については、次を参照してください。[プロパティ シート](../mfc/property-sheets-mfc.md)します。

##  <a name="_core_implementing_the_default_property_page"></a> 既定のプロパティ ページを実装します。

派生したコントロールの ActiveX コントロール ウィザードが既定のプロパティ ページ クラスを提供コントロール プロジェクトの作成に ActiveX コントロール ウィザードを使用する場合[COlePropertyPage クラス](../mfc/reference/colepropertypage-class.md)します。 最初に、このプロパティ ページは空白になりますが、任意のダイアログ ボックス コントロールまたはコントロールのセットを追加することができます。 ActiveX コントロール ウィザードは、既定では、追加のプロパティ ページ クラスで 1 つのプロパティ ページ クラスを作成するため、(からも派生`COlePropertyPage`) クラス ビューを使用して作成する必要があります。 この手順の詳細については、次を参照してください。 [MFC ActiveX コントロール。別のカスタム プロパティ ページの追加](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)します。

プロパティを実装するページ (この例では、既定値) では、3 つの手順。

#### <a name="to-implement-a-property-page"></a>プロパティ ページを実装するには

1. 追加、 `COlePropertyPage`-コントロール プロジェクトにクラスを派生します。 (この場合) のように ActiveX コントロール ウィザードを使用して、プロジェクトが作成されている場合、既定のプロパティ ページ クラスが既に存在します。

1. プロパティ ページのテンプレートにすべてのコントロールを追加するのにには、ダイアログ エディターを使用します。

1. カスタマイズ、`DoDataExchange`の関数、 `COlePropertyPage`-プロパティ ページのコントロールと ActiveX コントロールの間の値を交換するクラスを派生します。

たとえば目的で、次の手順は、単純なコントロール ("Sample"という名前) を使用します。 サンプルでは、ActiveX コントロール ウィザードを使用して作成されたおよびストックの Caption プロパティのみが含まれています。

##  <a name="_core_adding_controls_to_a_property_page"></a> プロパティ ページにコントロールを追加します。

#### <a name="to-add-controls-to-a-property-page"></a>プロパティ ページにコントロールを追加するには

1. コントロール プロジェクトを開き、リソース ビューを開きます。

1. ダブルクリックして、**ダイアログ**directory のアイコン。

1. IDD_PROPPAGE_SAMPLE ダイアログ ボックスを開きます。

   ActiveX コントロール ウィザードでは、ダイアログ ID、ここでは、サンプルの末尾に、プロジェクトの名前を追加します。

1. ドラッグし、選択したコントロールをツールボックスからダイアログ ボックスの領域にドロップします。

1. この例では、コントロールのラベル テキストを"キャプション:"し、上述識別子で、編集ボックス コントロールで十分です。

1. クリックして**保存**ツールバーの変更を保存します。

ユーザー インターフェイスを変更すると、Caption プロパティの編集ボックスにリンクする必要があります。 これは、次のセクションを編集して、`CSamplePropPage::DoDataExchange`関数。

##  <a name="_core_customizing_the_dodataexchange_function"></a> DoDataExchange 関数をカスタマイズします。

プロパティ ページ[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)関数を使用して、コントロール内のプロパティの実際の値にプロパティ ページの値をリンクできます。 リンクを確立するために、対応するコントロール プロパティに適切なプロパティ ページのフィールドをマップする必要があります。

これらのマッピングは、プロパティ ページを使用して実装されます**ddp _** 関数。 **Ddp _** 関数と同様に機能、 **DDX_** 例外が 1 つの標準の MFC ダイアログ ボックスで使用される関数。 メンバー変数への参照だけでなく**ddp _** 関数は、コントロール プロパティの名前を取得します。 一般的なエントリを次に、`DoDataExchange`プロパティ ページの関数。

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

この関数に関連付けますプロパティ ページの*m_caption* 、キャプション、メンバー変数を使用して、`DDP_TEXT`関数。

プロパティ ページのコントロールを挿入した後は、プロパティ ページのコントロール、上述と、実際のコントロール プロパティの間のリンクを確立する必要があります。 を使用して、キャプション、`DDP_Text`上記で説明したとおりに機能します。

[プロパティ ページ](../mfc/reference/property-pages-mfc.md)チェック ボックス、ラジオのボタンなど、他の種類のダイアログ コントロールに使用できる、ボックスの一覧を表示します。 次の表は、プロパティ ページのセット全体を示します**ddp _** 関数とその用途。

### <a name="property-page-functions"></a>プロパティ ページ関数

|関数名|この関数を使用してリンク|
|-------------------|-------------------------------|
|`DDP_CBIndex`|コントロールのプロパティを使用してコンボ ボックスで選択した文字列のインデックス。|
|`DDP_CBString`|コントロールのプロパティを使用してコンボ ボックスで選択されている文字列。 選択した文字列は、プロパティの値と同じ文字で始まることができますが、完全には一致する必要があります。|
|`DDP_CBStringExact`|コントロールのプロパティを使用してコンボ ボックスで選択されている文字列。 選択した文字列とプロパティの文字列値が正確に一致する必要があります。|
|`DDP_Check`|コントロール プロパティを持つチェック ボックスです。|
|`DDP_LBIndex`|コントロールのプロパティにリスト ボックスで選択した文字列のインデックス。|
|`DDP_LBString`|コントロールのプロパティにリスト ボックスで選択されている文字列。 選択した文字列は、プロパティの値と同じ文字で始まることができますが、完全には一致する必要があります。|
|`DDP_LBStringExact`|コントロールのプロパティにリスト ボックスで選択されている文字列。 選択した文字列とプロパティの文字列値が正確に一致する必要があります。|
|`DDP_Radio`|コントロール プロパティを持つラジオ ボタン。|
|`DDP_Text`|コントロール プロパティを持つテキスト。|

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage クラス](../mfc/reference/colepropertypage-class.md)
