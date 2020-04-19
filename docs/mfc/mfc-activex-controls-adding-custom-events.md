---
title: MFC ActiveX コントロール:カスタムイベントの追加
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907318"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX コントロール:カスタムイベントの追加

カスタムイベントは、クラス`COleControl`によって自動的に起動されないという点で、stock イベントとは異なります。 カスタムイベントは、コントロールの開発者によって決定された特定のアクションをイベントとして認識します。 カスタムイベントのイベントマップエントリは、EVENT_CUSTOM マクロによって表されます。 次のセクションでは、ActiveX コントロールウィザードを使用して作成された ActiveX コントロールプロジェクトのカスタムイベントを実装します。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>イベントの追加ウィザードを使用したカスタムイベントの追加

次の手順では、特定のカスタムイベント ClickIn を追加します。 この手順を使用すると、他のカスタムイベントを追加できます。 ClickIn イベント名とパラメーターには、カスタムイベント名とそのパラメーターを置き換えます。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>イベントの追加ウィザードを使用して ClickIn カスタムイベントを追加するには

1. コントロールのプロジェクトを読み込みます。

1. **クラスビュー**で、ActiveX コントロールクラスを右クリックしてショートカットメニューを開きます。

1. ショートカットメニューの **[追加]** をクリックし、 **[イベントの追加]** をクリックします。

   イベントの追加ウィザードが開きます。

1. **[イベント名]** ボックスで、まず既存のイベントを選択し、 **[カスタム]** オプションボタンをクリックして、「 *ClickIn*」と入力します。

1. **[内部名]** ボックスに、イベントの発生関数の名前を入力します。 この例では、イベントの追加ウィザード (`FireClickIn`) によって提供される既定値を使用します。

1. パラメーター**名**と**パラメーターの型**コントロールを使用して、 *xcoord* (type *OLE_XPOS_PIXELS*) という名前のパラメーターを追加します。

1. *Ycoord* (type *OLE_YPOS_PIXELS*) という2番目のパラメーターを追加します。

1. イベントを作成するには、 **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_custom_events"></a>カスタムイベントのイベント追加ウィザードの変更

カスタムイベントを追加すると、イベントの追加ウィザードによってコントロールクラスが変更されます。H、。CPP、および。IDL ファイル。 次のコードサンプルは、ClickIn イベントに固有のものです。

ヘッダー () には、次の行が追加されます。H) ファイルを作成します。

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

このコードは、イベントの追加`FireClickIn`ウィザードを使用して定義した ClickIn イベントとパラメーターを使用して、 [COleControl:: FireEvent](../mfc/reference/colecontrol-class.md#fireevent)を呼び出すという名前のインライン関数を宣言します。

また、実装 () にあるコントロールのイベントマップに次の行が追加されます。CPP) コントロールクラスのファイル:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

このコードは、イベント ClickIn をインライン関数`FireClickIn`にマップし、イベントの追加ウィザードを使用して定義したパラメーターを渡します。

最後に、次の行がコントロールのに追加されます。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

この行によって、イベントの追加ウィザードのイベント一覧のイベントの位置から取得された特定の ID 番号が ClickIn イベントに割り当てられます。 イベント一覧のエントリを使用すると、コンテナーでイベントを予測できます。 たとえば、イベントが発生したときに実行されるハンドラーコードを提供できます。

##  <a name="_core_calling_fireclickin"></a>FireClickIn の呼び出し

イベントの追加ウィザードを使用して ClickIn カスタムイベントを追加したので、このイベントがいつ発生するかを決定する必要があります。 これを行うには`FireClickIn` 、適切なアクションが発生したときにを呼び出します。 この説明では、コントロールは、 `InCircle`ユーザーが円形`WM_LBUTTONDOWN`または楕円の領域内をクリックしたときに、ClickIn イベントを発生させるために、メッセージハンドラー内で関数を使用します。 ハンドラーを`WM_LBUTTONDOWN`追加する手順を次に示します。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>イベントの追加ウィザードを使用してメッセージハンドラーを追加するには

1. コントロールのプロジェクトを読み込みます。

1. **クラスビュー**で、ActiveX コントロールクラスを選択します。

1. **[プロパティ]** ウィンドウに、ActiveX コントロールで処理できるメッセージの一覧が表示されます。 太字で示されているメッセージには、既にハンドラー関数が割り当てられています。

1. 処理するメッセージを選択します。 この例では、 `WM_LBUTTONDOWN`を選択します。

1. 右側のドロップダウンリストボックスで、[  **\<Add > OnLButtonDown**] を選択します。

1. **クラスビュー**の新しいハンドラー関数をダブルクリックして、実装 () のメッセージハンドラーコードに移動します。CPP) ActiveX コントロールのファイル。

次のコードサンプルでは`InCircle` 、コントロールウィンドウ内でマウスの左ボタンがクリックされるたびに関数を呼び出します。 このサンプルは、 [Circ サンプル](../overview/visual-cpp-samples.md)抽象`WM_LBUTTONDOWN`のハンドラー `OnLButtonDown`関数で参照できます。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  イベントの追加ウィザードでマウスボタン操作のメッセージハンドラーが作成されると、基本クラスの同じメッセージハンドラーの呼び出しが自動的に追加されます。 この呼び出しは削除しないでください。 コントロールが任意のストックマウスメッセージを使用する場合は、マウスキャプチャが適切に処理されるように、基本クラスのメッセージハンドラーを呼び出す必要があります。

次の例では、コントロール内の円形または楕円の領域内でクリックが発生した場合にのみ、イベントが発生します。 この動作を実現するには、コントロール`InCircle`の実装 () に関数を配置します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

また、 `InCircle`関数の次の宣言をコントロールのヘッダー () に追加する必要があります。H) ファイル:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>ストック名を持つカスタムイベント

Stock イベントと同じ名前のカスタムイベントを作成できますが、両方を同じコントロールに実装することはできません。 たとえば、ストックイベントのクリックが通常発生したときに起動しない Click というカスタムイベントを作成することができます。 その後、Click 関数を呼び出すことによって、いつでも Click イベントを発生させることができます。

次の手順では、カスタムの Click イベントを追加します。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Stock イベント名を使用するカスタムイベントを追加するには

1. コントロールのプロジェクトを読み込みます。

1. **クラスビュー**で、ActiveX コントロールクラスを右クリックしてショートカットメニューを開きます。

1. ショートカットメニューの **[追加]** をクリックし、 **[イベントの追加]** をクリックします。

   イベントの追加ウィザードが開きます。

1. **[イベント名]** ボックスの一覧で、ストックイベント名を選択します。 この例では、 **[クリック]** を選択します。

1. **[イベントの種類]** で **[カスタム]** を選択します。

1. イベントを作成するには、 **[完了]** をクリックします。

1. コード`FireClick`内の適切な場所でを呼び出します。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)
