---
title: MFC ActiveX コントロール:ActiveX コントロールへのストック イベントの追加
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: 9f6f3c63f0436296791df428c704bce96eca3ec0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392727"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールへのストック イベントの追加

ストック イベントは、クラスによって自動的に呼び出される点で、カスタム イベントとは異なります。 [COleControl](../mfc/reference/colecontrol-class.md)します。 `COleControl` 定義済みのメンバー関数の一般的なアクションの結果イベントを発生させることがあります。 一般的なアクションによって実装される`COleControl`に含める 1 つのシングル クリックやダブルクリック コントロール、キーボード イベント、および変更のマウス ボタンの状態。 イベントは、ストック イベントの前に必ず EVENT_STOCK プレフィックスのエントリをマップします。

##  <a name="_core_stock_events_supported_by_classwizard"></a> サポートされているイベントのイベント追加ウィザード

`COleControl`クラスには、次の表に、10 個のストック イベントが用意されています。 コントロールを使用して、必要なイベントを指定することができます、[イベント追加ウィザード](../ide/add-event-wizard.md)します。

### <a name="stock-events"></a>ストック イベント

|event|発生させる関数|コメント|
|-----------|---------------------|--------------|
|ここを|**void FireClick( )**|コントロールが、マウスをキャプチャするときに発生**BUTTONUP** (左、中央、または右) のメッセージを受信し、コントロールの上のボタンが離されました。 株価 MouseDown、MouseUp イベントは、このイベントの前に発生します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_CLICK( )**|
|DblClick|**void FireDblClick( )**|クリックすると似ていますが、ときに発生する、 **BUTTONDBLCLK**メッセージを受信します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_DBLCLICK( )**|
|Error|**void FireError( SCODE**  *scode* **, LPCSTR**  `lpszDescription` **, UINT**  `nHelpID`  **= 0 )**|メソッドの呼び出しまたはプロパティ アクセスのスコープの外部で ActiveX コントロール内でエラーが発生したときに発生します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**void FireKeyDown( short**  `nChar` **, short**  `nShiftState`  **)**|ときに発生する、`WM_SYSKEYDOWN`または`WM_KEYDOWN`メッセージを受信します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_KEYDOWN( )**|
|Keypress イベント|**void FireKeyPress( short** <strong>\*</strong>  `pnChar`  **)**|ときに発生する、`WM_CHAR`メッセージを受信します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**FireKeyUp を無効にする (短い**`nChar` **、短い**`nShiftState`**)**|ときに発生する、`WM_SYSKEYUP`または`WM_KEYUP`メッセージを受信します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_KEYUP( )**|
|MouseDown|**void FireMouseDown( short**  `nButton` **, short**  `nShiftState` **, float**  *x* **, float**  *y*  **)**|存在する場合に発生した**BUTTONDOWN** (左、中央、または右) を受信します。 このイベントが発生する直前に、マウスがキャプチャされます。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_MOUSEDOWN( )**|
|MouseMove|**void FireMouseMove( short**  `nButton` **, short**  `nShiftState` **, float**  *x* **, float**  *y*  **)**|WM_MOUSEMOVE メッセージを受信したときに発生します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_MOUSEMOVE( )**|
|MouseUp|**FireMouseUp を無効にする (短い**`nButton` **、短い**`nShiftState` **、float** *x* **、float** *y*  **)**|存在する場合に発生した**BUTTONUP** (左、中央、または右) を受信します。 このイベントが発生する前に、マウス キャプチャが解放されます。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|受信データの量のための次の準備完了状態にコントロールの遷移するときに発生します。<br /><br /> イベント マップ エントリ:**EVENT_STOCK_READYSTATECHANGE( )**|

##  <a name="_core_adding_a_stock_event_using_classwizard"></a> ストック イベントを使用して追加のイベント追加ウィザード

実際のイベントの発生は、基本クラスによって自動的に処理されるので、カスタム イベントを追加するよりも処理量が少ないストック イベントの追加が必要です`COleControl`します。 次の手順では、ストック イベントを追加するコントロールを使用して開発された[MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)します。 キーが押され、コントロールがアクティブなときに、KeyPress と呼ばれる、イベントが発生します。 この手順は、その他のストック イベントを追加することも使用できます。 KeyPress のストック イベントの選択した名前に置き換えます。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>イベントの追加ウィザードを使用して KeyPress ストック イベントを追加するには

1. コントロールのプロジェクトを読み込みます。

1. クラス ビューでは、ショートカット メニューを開き、ActiveX コントロール クラスを右クリックします。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**イベントの追加**します。

   イベントの追加ウィザードが開きます。

1. **イベント名**ドロップダウン リストで、`KeyPress`します。

1. **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_stock_events"></a> ストック イベントのイベント ウィザードによる変更を追加します。

ストック イベントは、コントロールの基本クラスによって処理される、ので、イベントの追加ウィザードには任意の方法でクラスの宣言は変わりません。 コントロールのイベントのマップにイベントを追加し、内のエントリは、そのします。IDL ファイルです。 次の行は、コントロール クラスの実装である、コントロールのイベントのマップに追加されます (します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

このコードを追加すると、WM_CHAR メッセージを受信し、コントロールがアクティブでは、KeyPress イベントが発生します。 KeyPress イベントは、起動処理関数を呼び出すことによって他のタイミングで起動できる (たとえば、 `FireKeyPress`) から、コントロール コード内で。

イベントの追加ウィザードでは、コントロールの次のコード行を追加します。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

この行は、標準のディスパッチ ID を持つ KeyPress イベントを関連付けますでき、KeyPress イベントを予測するコンテナーです。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)
