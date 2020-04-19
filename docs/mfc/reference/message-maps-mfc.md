---
title: メッセージ マップ (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 4305d9b1db297eebcb189d2fad98b8c634ed1133
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908038"
---
# <a name="message-maps-mfc"></a>メッセージ マップ (MFC)

参照のこのセクションでは、すべての[メッセージマッピングマクロ](../../mfc/reference/message-map-macros-mfc.md)とすべての[CWnd](../../mfc/reference/cwnd-class.md)メッセージマップエントリを、対応するメンバー関数プロトタイプと共に示します。

|Category|説明|
|--------------|-----------------|
|コマンド\_メッセージハンドラーで|ユーザー `WM_COMMAND`メニュー選択またはメニューアクセスキーによって生成されるメッセージを処理します。|
|[子ウィンドウの通知メッセージ ハンドラー](../../mfc/reference/child-window-notification-message-handlers.md)|子ウィンドウからの通知メッセージを処理します。|
|[WM_ で始まるメッセージハンドラー](../../mfc/reference/handlers-for-wm-messages.md)|など`WM_`のメッセージを`WM_PAINT`処理します。|
|[ユーザー定義メッセージハンドラー](../../mfc/reference/user-defined-handlers.md)|ユーザー定義メッセージを処理します。|

(このリファレンスで使用される用語と規則の詳細については、「[メッセージマップの相互参照の使用方法](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)」を参照してください)。

Windows はメッセージ指向オペレーティング システムであることが理由で、Windows 環境向けのプログラミングの大部分にはメッセージ処理が関係しています。 キーストロークやマウス クリックなどのイベントが発生するたびに、そのイベントを処理する必要があるアプリケーションに対してメッセージが送信されます。

Microsoft Foundation Class ライブラリには、メッセージベースのプログラミングに最適化されたプログラミング モデルが用意されています。 このモデルでは、特定のクラスに対してどの関数がさまざまなメッセージを処理するかを指定した "メッセージ マップ" を使用します。 メッセージ マップには、どの関数がどのメッセージを処理するかを指定する 1 つ以上のマクロが含まれています。 たとえば、`ON_COMMAND` マクロを含むメッセージ マップは、次のように記述されることがあります。

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND` マクロは、メニュー、ボタン、およびアクセラレータ キーによって生成されるコマンド メッセージを処理するために使用します。 [マクロ](../../mfc/reference/message-map-macros-mfc.md)は、次のものをマップするために使用できます。

## <a name="windows-messages"></a>Windows メッセージ

- コントロールの通知

- ユーザー定義メッセージ

## <a name="command-messages"></a>コマンド メッセージ

- 登録済みのユーザー定義メッセージ

- ユーザー インターフェイス更新メッセージ

## <a name="ranges-of-messages"></a>メッセージの範囲

- コマンド

- ハンドラー メッセージの更新

- コントロールの通知

メッセージ マップ マクロは重要なマクロですが、通常は直接記述する必要はありません。 これは、[クラスウィザード](mfc-class-wizard.md)を使用してメッセージ処理関数をメッセージに関連付けた場合に、ソースファイルにメッセージマップエントリが自動的に作成されるためです。 メッセージマップエントリを編集または追加する場合はいつでも、クラスウィザードを使用できます。

> [!NOTE]
>  クラスウィザードでは、メッセージマップ範囲はサポートされていません。 これらのメッセージ マップ エントリは、独自に作成する必要があります。

ただし、メッセージ マップは、Microsoft Foundation Class ライブラリの重要な部分です。 これらが何を実行するかを理解する必要があり、そのためのドキュメントが用意されています。

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
