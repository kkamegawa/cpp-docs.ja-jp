---
title: MFC ActiveX コントロール:フォントの使用
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: ce1e913bb3bd1c3b74db43dc02d9d360b9cfd00c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239516"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX コントロール:フォントの使用

ActiveX コントロールには、テキストが表示されている場合は、コントロールのフォント プロパティを変更することで、テキストの外観を変更するユーザーを許可できます。 フォントのプロパティは、フォント オブジェクトとして実装され、2 種類のいずれかを指定できます: 株価またはカスタム。 ストック フォント プロパティは、プロパティの追加ウィザードを使用して追加できるあらかじめ実装されているフォントのプロパティです。 カスタム フォントのプロパティがあらかじめ実装されていないと、コントロールの開発者が、プロパティの動作と使用状況を判断します。

ここでは、次のトピックについて説明します。

- [ストック フォント プロパティを使用します。](#_core_using_the_stock_font_property)

- [コントロールのカスタム フォントのプロパティを使用](#_core_implementing_a_custom_font_property)

##  <a name="_core_using_the_stock_font_property"></a> ストック フォント プロパティを使用します。

ストック フォント プロパティがクラスによってあらかじめ実装されて[COleControl](../mfc/reference/colecontrol-class.md)します。 さらに、標準のフォント プロパティ ページでは、使用可能なユーザーのフォント オブジェクトの名前、サイズ、スタイルなど、さまざまな属性を変更することができますも。

使用してフォント オブジェクトへのアクセス、 [GetFont](../mfc/reference/colecontrol-class.md#getfont)、 [SetFont](../mfc/reference/colecontrol-class.md#setfont)、および[InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont)関数の`COleControl`します。 コントロールのユーザーが経由でのフォント オブジェクトへのアクセス、`GetFont`と`SetFont`他の取得/設定プロパティと同様に機能します。 フォント オブジェクトへのアクセスがコントロール内から必要な場合は、使用、`InternalGetFont`関数。

説明したよう[MFC ActiveX コントロール。プロパティ](../mfc/mfc-activex-controls-properties.md)、ストック プロパティの追加を簡単に、[プロパティの追加ウィザード](../ide/names-add-property-wizard.md)します。 フォント プロパティを選択して、プロパティの追加ウィザードが自動的にコントロールのディスパッチ マップには、ストックのフォント エントリを挿入します。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用して、ストック フォント プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

   プロパティの追加ウィザードが開きます。

1. **プロパティ名**ボックスで、**フォント**します。

1. **[完了]** をクリックします。

プロパティの追加ウィザードでは、コントロール クラス実装ファイル内にあるコントロールのディスパッチ マップに次の行が追加されます。

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

さらに、プロパティの追加ウィザードでは、コントロールに、次の行を追加します。IDL ファイル:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

ストックの Caption プロパティは、ストックのフォント プロパティ情報を使用して描画するテキスト プロパティの例を示します。 ストック フォント プロパティに使用されるものと同様の手順を使用するコントロールへのストック プロパティのキャプションを追加します。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用して株式の Caption プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

   プロパティの追加ウィザードが開きます。

1. **プロパティ名**ボックスで、**キャプション**します。

1. **[完了]** をクリックします。

プロパティの追加ウィザードでは、コントロール クラス実装ファイル内にあるコントロールのディスパッチ マップに次の行が追加されます。

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

##  <a name="_core_modifying_the_ondraw_function"></a> OnDraw 関数の変更

既定の実装`OnDraw`コントロールに表示されるすべてのテキストを Windows システム フォントを使用します。 つまり、変更する必要がある、`OnDraw`デバイス コンテキスト、フォント オブジェクトを選択してコード。 これを行うには、呼び出す[それ](../mfc/reference/colecontrol-class.md#selectstockfont)を次の例に示すように、コントロールのデバイス コンテキストを渡します。

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

後に、`OnDraw`関数を変更するフォント オブジェクトを使用して、コントロールのストック フォント プロパティからの特性を持つコントロール内の任意のテキストが表示されます。

##  <a name="_core_using_custom_font_properties_in_your_control"></a> コントロールのカスタム フォントのプロパティを使用

ストックのフォント プロパティだけでなく、ActiveX コントロールがカスタム フォントのプロパティを持つことができます。 カスタム フォント プロパティを追加する必要があります。

- プロパティの追加ウィザードを使用して、カスタムのフォント プロパティを実装します。

- [フォントの通知を処理](#_core_processing_font_notifications)します。

- [新しいフォント通知インターフェイスを実装する](#_core_implementing_a_new_font_notification_interface)します。

###  <a name="_core_implementing_a_custom_font_property"></a> カスタム フォント プロパティを実装します。

カスタムのフォント プロパティを実装するには、プロパティの追加ウィザードを使用するプロパティを追加し、コードにいくつかの変更を加えます。 次のセクションでは、ユーザー設定を追加する方法を説明する`HeadingFont`サンプル コントロールのプロパティ。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用してカスタムのフォント プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

   プロパティの追加ウィザードが開きます。

1. **プロパティ名**ボックスに、プロパティの名前を入力します。 この例では、使用**HeadingFont**します。

1. **[実装型]** として、 **[Get/Set メソッド]** をクリックします。

1. **プロパティ型**ボックスで、 **IDispatch** <strong>\*</strong>のプロパティの型。

1. **[完了]** をクリックします。

プロパティの追加ウィザードを追加するコードを作成し、`HeadingFont`カスタム プロパティを`CSampleCtrl`クラスと、サンプル。IDL ファイルです。 `HeadingFont`取得/設定プロパティの型は、プロパティの追加ウィザードは、 `CSampleCtrl` 、DISP_PROPERTY_EX_ID を含めるクラスのディスパッチ マップ[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)マクロ エントリ。

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX マクロを関連付けます、 `HeadingFont` 、対応するプロパティ名`CSampleCtrl`Get し、Set メソッドをクラス`GetHeadingFont`と`SetHeadingFont`します。 プロパティ値の型が指定されてもします。この場合、VT_FONT です。

プロパティの追加ウィザードは、コントロールのヘッダー ファイルで宣言を追加することも (します。H) の`GetHeadingFont`と`SetHeadingFont`関数し、コントロール実装ファイル内の関数テンプレートを追加します (します。CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最後に、プロパティの追加ウィザードは、コントロールを変更します。IDL ファイルのエントリを追加することで、`HeadingFont`プロパティ。

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>コントロールのコードの変更

追加したので、`HeadingFont`プロパティ、コントロールを完全に新しいプロパティをサポートするコントロールのヘッダーと実装ファイルにいくつかの変更を加える必要があります。

コントロールのヘッダー ファイル内 (します。H)、プロテクト メンバー変数の次の宣言を追加します。

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

コントロールの実装ファイル内 (します。CPP) では、次の操作を行います。

- 初期化*取り上げた*コントロールのコンス トラクター内。

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- フォントの既定の属性を含む静的 FONTDESC 構造体を宣言します。

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- コントロールで`DoPropExchange`メンバー関数を呼び出しを追加、`PX_Font`関数。 これは、初期化とカスタムのフォント プロパティを永続化を提供します。

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- コントロールの実装を終了`GetHeadingFont`メンバー関数。

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- コントロールの実装を終了`SetHeadingFont`メンバー関数。

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- コントロールの変更`OnDraw`メンバー関数は、以前に選択したフォントを保持する変数を定義します。

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- コントロールの変更`OnDraw`メンバー関数は、フォントが使用される場所に次の行を追加することで、デバイス コンテキストにカスタム フォントを選択します。

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- コントロールの変更`OnDraw`メンバー関数は、フォントを使用した後、次の行を追加することで、デバイス コンテキストに戻す前のフォントを選択します。

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

カスタムのフォント プロパティを実装すると、標準のフォント プロパティ ページを実装するコントロールの現在のフォントを変更するユーザーが制御できるようにします。 標準のフォント プロパティ ページのプロパティ ページの ID を追加するには、BEGIN_PROPPAGEIDS マクロの後に、次の行を挿入します。

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

BEGIN_PROPPAGEIDS マクロのカウント パラメーターは、いずれかによっても増やす必要があります。 次の行に例を示します。

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

これらの変更が完了したら、追加の機能を組み込むプロジェクト全体を再構築します。

###  <a name="_core_processing_font_notifications"></a> フォントの通知の処理

ほとんどの場合は、コントロールがフォント オブジェクトの特性が変更された時に知っておく必要があります。 フォントの各オブジェクトがのメンバー関数を呼び出すことによって変更するときに通知を提供することのできる、`IFontNotification`によって実装されるインターフェイス`COleControl`します。

その通知は、コントロールは、ストック フォント プロパティを使用している場合、`OnFontChanged`のメンバー関数`COleControl`します。 カスタム フォントのプロパティを追加すると、同じ実装を使用して、そのことができます。 前のセクションの例で渡すことによってこれが &*トラクター*初期化するときに、*取り上げた*メンバー変数。

![複数のフォント オブジェクト インターフェイスを実装する](../mfc/media/vc373q1.gif "複数のフォント オブジェクト インターフェイスを実装します。") <br/>
複数のフォント オブジェクト インターフェイスの実装

上記の図の実線は、両方のフォント オブジェクトでの同じ実装を使用していることを表示`IFontNotification`します。 これにより、どのフォントが変更を区別する場合は問題が発生する可能性があります。

コントロールのフォント オブジェクトの通知を区別する方法の 1 つがの別々 の実装を作成するには、`IFontNotification`コントロール内の各フォント オブジェクトのインターフェイス。 この手法では、文字列、または最近変更されたフォントを使用するには、文字列を更新することで、描画のコードを最適化できます。 次のセクションでは、2 番目のフォント プロパティの別の通知のインターフェイスを実装するための手順を示します。 2 番目のフォント プロパティがあると見なされます、`HeadingFont`前のセクションで追加されたプロパティ。

###  <a name="_core_implementing_a_new_font_notification_interface"></a> 新しいフォント通知インターフェイスを実装します。

2 つまたは複数のフォントの通知を区別するには、コントロールで使用される各フォントの新しい通知インターフェイスを実装する必要があります。 次のセクションでは、コントロールのヘッダーと実装ファイルを変更して新しいフォント通知インターフェイスを実装する方法について説明します。

### <a name="additions-to-the-header-file"></a>ヘッダー ファイルへの追加

コントロールのヘッダー ファイル内 (します。H)、クラス宣言に次の行を追加します。

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

これの実装を作成、`IPropertyNotifySink`と呼ばれるインターフェイス`HeadingFontNotify`します。 この新しいインターフェイスには、呼び出されたメソッドが含まれています。`OnChanged`します。

### <a name="additions-to-the-implementation-file"></a>実装ファイルへの追加

(コントロールのコンス トラクター) の見出しのフォントを初期化するコードで次のように変更します。 (& a)*トラクター*する (& a)*m_xHeadingFontNotify*します。 次のコードを追加します。

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`と`Release`メソッド、`IPropertyNotifySink`インターフェイスの追跡、ActiveX コントロール オブジェクトの参照カウントします。 コントロールは、インターフェイス ポインターへのアクセスを取得する場合、コントロールは`AddRef`参照カウントをインクリメントします。 コントロールがマウス ポインターで完了したら、呼び出す`Release`でほぼ同じ方法`GlobalFree`グローバル メモリ ブロックを解放するために呼び出す可能性があります。 このインターフェイスの参照カウントがゼロに時に、インターフェイスの実装を解放できます。 この例で、`QueryInterface`関数へのポインターを返します、`IPropertyNotifySink`特定のオブジェクトのインターフェイス。 この関数は、ActiveX コントロールをサポートするインターフェイスを決定するオブジェクトを照会できます。

これらの変更が行われた後、プロジェクトにプロジェクトをリビルドし、インターフェイスをテストするテスト コンテナーを使用します。 Test Container にアクセスする方法について詳しくは、「 [テスト コンテナーでのプロパティとイベントのテスト](../mfc/testing-properties-and-events-with-test-container.md) 」をご覧ください。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: ActiveX コントロールにおけるピクチャの使用](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX コントロール: ストック プロパティ ページの使用](../mfc/mfc-activex-controls-using-stock-property-pages.md)
