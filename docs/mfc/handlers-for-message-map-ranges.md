---
title: 範囲内のメッセージのハンドラー
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: d2bc961486d9bc686e1ca0d5feb0fe01d65f9512
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358644"
---
# <a name="handlers-for-message-map-ranges"></a>範囲内のメッセージのハンドラー

この記事では、メッセージの範囲を 1 つのメッセージを 1 つだけの関数にマッピング) ではなく 1 つのメッセージ ハンドラー関数にマップする方法について説明します。

まったく同じ方法では、複数のメッセージまたはコントロールの通知を処理する必要がある場合もあります。 このような場合は、すべてのメッセージを 1 つのハンドラー関数にマップする場合があります。 メッセージ マップの範囲は、メッセージの連続する範囲はこれを使用します。

- コマンド Id の範囲を割り当てることができます。

  - コマンドのハンドラー関数。

  - コマンド更新ハンドラー関数。

- コントロール Id の範囲のコントロールの通知メッセージは、メッセージ ハンドラー関数にマップできます。

この記事で説明したトピックは次のとおりです。

- [メッセージ マップ エントリを書き込む](#_core_writing_the_message.2d.map_entry)

- [ハンドラー関数の宣言](#_core_declaring_the_handler_function)

- [コマンド Id の範囲の例](#_core_example_for_a_range_of_command_ids)

- [コントロール Id の範囲の例](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> メッセージ マップ エントリを書き込む

の。CPP ファイルに、次の例に示すように、メッセージ マップ エントリを追加します。

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

メッセージ マップ エントリは、次の項目で構成されます。

- メッセージ マップの範囲のマクロ:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- マクロ パラメーター:

  最初の 2 つのマクロは、次の 3 つのパラメーターをとります。

  - 範囲の開始コマンド ID

  - 範囲の最後のコマンド ID

  - メッセージ ハンドラー関数の名前

  コマンド Id の範囲は連続している必要があります。

  3 番目のマクロ`ON_CONTROL_RANGE`、追加の最初のパラメーターを受け取る: コントロールの通知メッセージなど、 **EN_CHANGE**します。

##  <a name="_core_declaring_the_handler_function"></a> ハンドラー関数の宣言

内のハンドラー関数の宣言を追加します。H ファイルです。 次に示すように、次のコードは、これが検索する方法を示します。

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

通常 1 つのコマンド ハンドラー関数はパラメーターを受け取らない。 メッセージ マップの範囲のハンドラー関数が追加のパラメーターを必要と更新のハンドラー関数を除く*nID*、型の**UINT**します。 このパラメーターは、最初のパラメーターです。 追加のパラメーターには、ユーザーが実際に選択したコマンドを指定するために必要なコマンドの ID が対応しています。

更新ハンドラー関数のパラメーターの要件の詳細については、次を参照してください。[例の Id の範囲コマンド](#_core_example_for_a_range_of_command_ids)します。

##  <a name="_core_example_for_a_range_of_command_ids"></a> 範囲のコマンド Id の例

1 つの例は、MFC サンプル ズーム コマンドのようなコマンドの処理範囲を使用して場合[HIERSVR](../overview/visual-cpp-samples.md)します。 このコマンドは、ビュー、25% と、通常のサイズの 300% の間のスケールを拡大します。 HIERSVR のビュー クラスでは、次のようなメッセージ マップ エントリに拡大/縮小コマンドを処理するために、範囲を使用します。

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

メッセージ マップ エントリを記述するときに指定します。

- 2 つのコマンドの開始と終了の連続する範囲の Id。

   ここには**ID_VIEW_ZOOM25**と**ID_VIEW_ZOOM300**します。

- コマンドのハンドラー関数の名前。

   ここでは`OnZoom`します。

この関数の宣言になります。

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新ハンドラー関数と同様に、およびより広範に使用できる可能性があります。 記述する非常に一般的`ON_UPDATE_COMMAND_UI`多数のコマンドのハンドラーを記述またはコピーを同じコードを何に気付くとします。 ソリューションは、さまざまなコマンド ハンドラー関数を使用して Id を 1 つの更新をマップする、`ON_UPDATE_COMMAND_UI_RANGE`マクロ。 コマンド Id は、連続する範囲を形成する必要があります。 例については、次を参照してください。、`OnUpdateZoom`ハンドラーとその`ON_UPDATE_COMMAND_UI_RANGE`hiersvr のビュー クラスのメッセージ マップ エントリ。

ハンドラー関数を更新プログラムは、1 つのコマンドは通常 1 つのパラメーターを受け取ります*対応付けられた*、型の`CCmdUI*`します。 ハンドラーの関数とは異なりメッセージ マップの範囲の更新のハンドラー関数必要としない追加のパラメーター *nID*、型の**UINT**します。 ユーザーが実際に選択したコマンドを指定するには、必要なコマンド ID がで見つかった、`CCmdUI`オブジェクト。

##  <a name="_core_example_for_a_range_of_control_ids"></a> 範囲のコントロール Id の例

別の興味深いケースでは、コントロール Id の範囲のコントロールの通知メッセージを単一のハンドラーにマップします。 たとえば、ユーザーが 10 個のボタンをクリックします。 10 のすべてのボタンを 1 つのハンドラーにマップするに、メッセージ マップ エントリは次のようになります。

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

記述するとき、`ON_CONTROL_RANGE`メッセージ マップにマクロを指定します。

- 特定のコントロール通知メッセージです。

   ここでは**BN_CLICKED**します。

- コントロールの範囲に関連付けられているコントロール ID の値。

   ここではこれら**IDC_BUTTON1**と**IDC_BUTTON10**します。

- メッセージ ハンドラー関数の名前。

   ここでは`OnButtonClicked`します。

ハンドラー関数を記述する場合は、余分なを指定**UINT**では、次に示すように、パラメーター。

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked` 1 つのハンドラー **BN_CLICKED**パラメーターを受け取らないメッセージ。 同じ一連のボタンのハンドラーは、いずれか**UINT**します。 生成する特定のコントロールを識別するため、余分なパラメーターを使用できます、 **BN_CLICKED**メッセージ。

例に示したコードは一般的な: に渡される値に変換する、`int`内メッセージ範囲し場合は、このことをアサートします。 ボタンのクリックしてに応じて異なるアクションをかかる場合があります。

## <a name="see-also"></a>関連項目

[メッセージ ハンドラー関数の宣言](../mfc/declaring-message-handler-functions.md)
