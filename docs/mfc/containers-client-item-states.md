---
title: コンテナー:クライアント アイテムの状態
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 1453ba3f96e49cefc9014a93ebcfbcfe5c6bc905
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152853"
---
# <a name="containers-client-item-states"></a>コンテナー:クライアント アイテムの状態

この記事では、クライアントの項目がその有効期間内を通過するさまざまな状態について説明します。

クライアント アイテムは、作成、アクティブ化、変更、および保存されるいくつかの状態を通過します。 項目の状態の変更、フレームワークによって毎回[として](../mfc/reference/coleclientitem-class.md#onchange)で、 **OLE_CHANGED_STATE**通知します。 2 番目のパラメーターの値は、`COleClientItem::ItemState`列挙体。 次のいずれかを指定できます。

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

空の状態でクライアント アイテムはまだ完全項目です。 メモリが、割り当てられていますが、OLE アイテムのデータで初期化されていません。 これは、クライアントの項目を呼び出すことによって作成されたときの状態**新しい**が、一般的な 2 段階の作成の 2 番目の手順を実施されていません。

呼び出すことによって実行される、2 番目の手順で`COleClientItem::CreateFromFile`別または`CreateFrom` *xxxx*関数の場合、項目が作成される完全にします。 (ファイルまたはクリップボードなど、他のソース) から OLE データが関連付けられている、 `COleClientItem`-派生オブジェクト。 これで、アイテムが読み込み済み状態です。

項目がされているサーバーのウィンドウで開かれているではなく、コンテナーのドキュメント内で開かれているときに開いている (または完全なオープン) の状態になります。 この状態で、クロスハッチ通常を描画、項目がアクティブであることを示す別の場所のコンテナーのウィンドウ内の項目の形式をします。

項目はインプレース アクティブ化時に合格した通常のみアクティブな状態を簡単にします。 メニューのツールバー、およびコンテナーの場合は、その他のユーザー インターフェイス コンポーネントのサーバーにマージ、UI のアクティブな状態を入力します。 これらのユーザー インターフェイス コンポーネントの存在は、アクティブな状態から UI のアクティブな状態を区別します。 それ以外の場合、アクティブな状態では、UI のアクティブな状態に似ています。 サーバーは、元に戻すをサポートする場合は、サーバーが読み込まれたまたはオープン状態に到達するまで OLE 項目の元に戻す状態情報を保持するために必要です。

## <a name="see-also"></a>関連項目

[コンテナー](../mfc/containers.md)<br/>
[アクティベーション](../mfc/activation-cpp.md)<br/>
[コンテナー:クライアント アイテム通知](../mfc/containers-client-item-notifications.md)<br/>
[トラッカー](../mfc/trackers.md)<br/>
[CRectTracker クラス](../mfc/reference/crecttracker-class.md)
