---
title: ActiveX コントロールコンテナー:ActiveX コントロールからのイベントの処理
ms.date: 09/12/2018
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907770"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX コントロールコンテナー:ActiveX コントロールからのイベントの処理

この記事では、 **[プロパティ]** ウィンドウ (**クラスビュー**) を使用して ActiveX コントロールコンテナーに activex コントロールのイベントハンドラーをインストールする方法について説明します。 イベントハンドラーは、特定のイベントの通知 (コントロールからの) を受信し、応答で何らかのアクションを実行するために使用されます。 この通知は、イベントの "起動" と呼ばれます。

>[!IMPORTANT]
> ActiveX は、新しい開発には使用しない従来のテクノロジです。 ActiveX を置き換える最新テクノロジの詳細については、「 [Activex コントロール](activex-controls.md)」を参照してください。

> [!NOTE]
>  この記事では、コンテナーという名前のダイアログベースの ActiveX コントロールコンテナープロジェクトと、手順とコードの例として、Circ という名前の埋め込みコントロールを使用します。

**プロパティ** ウィンドウの イベント ボタン (**クラスビュー**) を使用すると、ActiveX コントロールコンテナーアプリケーションで発生するイベントのマップを作成できます。 このマップは "イベントシンクマップ" と呼ばれ、コントロールコンテナークラスにイベントハンドラー C++を追加すると、ビジュアルによって作成および管理されます。 イベントマップエントリと共に実装された各イベントハンドラーは、特定のイベントをコンテナーイベントハンドラーのメンバー関数にマップします。 このイベントハンドラー関数は、ActiveX コントロールオブジェクトによって指定されたイベントが発生したときに呼び出されます。

イベントシンクマップの詳細については、*クラスライブラリリファレンス*の「[イベントシンクマップ](../mfc/reference/event-sink-maps.md)」を参照してください。

##  <a name="_core_event_handler_modifications_to_the_project"></a>プロジェクトに対するイベントハンドラーの変更

**[プロパティ]** ウィンドウを使用してイベントハンドラーを追加すると、イベントシンクマップが宣言され、プロジェクトで定義されます。 次のステートメントがコントロールに追加されます。最初にイベントハンドラーが追加されたときの CPP ファイル。 このコードは、ダイアログボックスクラス (この場合は`CContainerDlg`) のイベントシンクマップを宣言します。

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

**[プロパティ]** ウィンドウを使用してイベントを追加すると、イベント`ON_EVENT`マップエントリ () がイベントシンクマップに追加され、イベントハンドラー関数がコンテナーの実装 (に追加されます。CPP) ファイル。

次の例では、Circ コントロールの`OnClickInCircCtrl` `ClickIn`イベントに対してという名前のイベントハンドラーを宣言しています。

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

さらに、次のテンプレートがクラスの`CContainerDlg`実装 (に追加されます。CPP) ファイルハンドラーのメンバー関数の場合:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

イベントシンクマクロの詳細については、*クラスライブラリリファレンス*の「[イベントシンクマップ](../mfc/reference/event-sink-maps.md)」を参照してください。

#### <a name="to-create-an-event-handler-function"></a>イベントハンドラー関数を作成するには

1. クラスビューから、ActiveX コントロールを含むダイアログクラスを選択します。 この例では、 `CContainerDlg`を使用します。

1. **[プロパティ]** ウィンドウで、 **[イベント]** ボタンをクリックします。

1. **[プロパティ]** ウィンドウで、埋め込み ActiveX コントロールのコントロール ID を選択します。 この例では、 `IDC_CIRCCTRL1`を使用します。

   **[プロパティ]** ウィンドウには、埋め込み ActiveX コントロールによって起動できるイベントの一覧が表示されます。 太字で示されているメンバー関数には、既にハンドラー関数が割り当てられています。

1. ダイアログクラスで処理するイベントを選択します。 この例では、 **[クリック]** を選択します。

1. 右側のドロップダウンリストボックスで、[  **\<Add > ClickCircctrl1**] を選択します。

1. クラスビューから新しいハンドラー関数をダブルクリックして、実装 () のイベントハンドラーコードに移動します。CPP) ファイル`CContainerDlg`。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
