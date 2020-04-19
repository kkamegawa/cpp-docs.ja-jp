---
title: コンテナー:クライアント アイテム通知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 583c438820c002a4c192d15358ca98424d02889a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153426"
---
# <a name="containers-client-item-notifications"></a>コンテナー:クライアント アイテム通知

この記事では、MFC フレームワークが呼び出すサーバー アプリケーション、クライアント アプリケーションのドキュメント内の項目を変更するときにオーバーライド可能な関数について説明します。

[COleClientItem](../mfc/reference/coleclientitem-class.md)サーバー アプリケーションとも呼ばれるコンポーネントのアプリケーションからの要求に対する応答として呼び出されるいくつかのオーバーライド可能な関数を定義します。 これらのオーバーライド可能な関数は、通常、通知として機能します。 スクロール、アクティベーションなどのさまざまなイベントまたはユーザーが編集またはそれ以外の場合、項目を操作するときに加える変更および位置の変更のコンテナー アプリケーションを通知します。

フレームワークへの呼び出しを使用して変更のコンテナー アプリケーションに通知`COleClientItem::OnChange`、オーバーライド可能な関数のうち、その実装が必要です。 保護されたこの関数は、2 つの引数を受け取ります。 1 つ目は、サーバーは、項目を変更した理由を指定します。

|Notification|説明|
|------------------|-------------|
|**OLE_CHANGED**|OLE 項目の外観が変更されました。|
|**で**|OLE 項目が保存されました。|
|**OLE_CLOSED**|OLE 項目が閉じられました。|
|**OLE_RENAMED**|OLE 項目を格納しているサーバーのドキュメントの名前が変更されました。|
|**OLE_CHANGED_STATE**|OLE 項目は、別の 1 つの状態から変更されました。|
|**OLE_CHANGED_ASPECT**|OLE 項目の描画の側面は、フレームワークによって変更されました。|

これらの値は、 **OLE_NOTIFICATION** AFXOLE で定義されている列挙型。H.

この関数の 2 番目の引数は、アイテムがどのように変更されたか、またはにどの状態を指定します。

|最初の引数|2 番目の引数|
|----------------------------|---------------------|
|**OLE_SAVED**または**OLE_CLOSED**|使用されません。|
|**OLE_CHANGED**|OLE 項目が変更されたことの縦横比を指定します。|
|**OLE_CHANGED_STATE**|入力されている状態について説明します (*this*、 *loadedState*、 *openState*、 *activeState*、または*activeUIState*)。|

クライアント アイテムの状態の詳細については、次を参照してください。[コンテナー。クライアント アイテムの状態](../mfc/containers-client-item-states.md)します。

Framework 呼び出し`COleClientItem::OnGetItemPosition`で埋め込み先編集の項目がアクティブ化されている場合。 実装は、インプレース編集をサポートするアプリケーションに必要です。 MFC アプリケーション ウィザードに、項目の座標を割り当てます、基本的な実装を提供する、`CRect`への引数として渡されるオブジェクト`OnGetItemPosition`します。

インプレース編集中に OLE 項目の位置またはサイズが変更された場合は、項目の位置とクリッピング四角形のコンテナーの情報を更新する必要があり、サーバーは、変更に関する情報を受け取る必要があります。 Framework 呼び出し`COleClientItem::OnChangeItemPosition`この目的のためです。 MFC アプリケーション ウィザードでは、基本クラスの関数を呼び出す上書きを提供します。 アプリケーション ウィザードで生成する関数を編集する必要があります、 `COleClientItem`-関数は、クライアント アイテム オブジェクトによって保持される情報を更新するようにクラスを派生します。

## <a name="see-also"></a>関連項目

[コンテナー](../mfc/containers.md)<br/>
[コンテナー:クライアント アイテムの状態](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)
