---
title: MFC ActiveX コントロール:イベント
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 0d8a881d07a3e48673c6dc3298816d165273be0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392675"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX コントロール:イベント

ActiveX コントロールは、コントロールに何かが発生するコンテナーに通知するのにイベントを使用します。 イベントの一般的な例には、コントロール、キーボード、および変更をコントロールの状態を使用して入力データのクリックが含まれます。 これらのアクションが発生すると、コントロールは、コンテナーのアラートを生成するイベントを発生させます。

イベントは、メッセージとも呼ばれます。

MFC は、2 つの種類のイベントをサポートしています: 株価とカスタムです。 ストック イベントはイベント クラスを[COleControl](../mfc/reference/colecontrol-class.md)は自動的に処理します。 ストック イベントの完全な一覧は、記事を参照してください。 [MFC ActiveX コントロール。ストック イベントの追加](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)します。 カスタム イベントは、コントロールをコントロールに固有の動作が発生した場合、コンテナーに通知する機能を許可します。 いくつかの例には、コントロールの内部状態または特定のウィンドウ メッセージの受信に変更があります。

コントロールのイベントが適切に通知をコントロール クラスは、コントロールの各イベントを関連するイベントの発生時に呼び出す必要がありますをメンバー関数にマップする必要があります。 このマッピングのメカニズム (イベント マップと呼ばれます) は、イベントに関する情報を一元化し、Visual Studio に簡単にアクセスして、コントロールのイベントを操作できるようにします。 このイベントのマップがヘッダーに存在する、次のマクロで宣言されている (します。H)、コントロール クラス宣言のファイル:

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

イベント マップを宣言すると、コントロールの実装で定義する必要があります (します。CPP) ファイルです。 次のコード行は、コントロールで特定のイベントを発生させるイベント マップを定義します。

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

MFC ActiveX コントロール ウィザードを使用してプロジェクトを作成する場合は、次の行が自動的に追加します。 MFC ActiveX コントロール ウィザードを使用しない場合は、次の行を手動で追加する必要があります。

クラスでサポートされているストック イベントを追加するクラスのビューを使って`COleControl`やカスタム イベントを定義します。 新しいイベントごとに、クラス ビューは、コントロールのイベントのマップをコントロールの適切なエントリを自動的に追加します。IDL ファイルです。

その他の 2 つの記事では、イベントの詳細について説明します。

- [MFC ActiveX コントロール: ストック イベントの追加](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX コントロール: カスタム イベントの追加](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)
