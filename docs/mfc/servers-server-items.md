---
title: サーバー:サーバー項目
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: abee619aa921b3e036a2bbeb1b4f5ae08d83f5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307849"
---
# <a name="servers-server-items"></a>サーバー:サーバー項目

サーバー アプリケーションをコンテナーでは、ユーザーは埋め込みまたはリンクされている OLE 項目を編集できるように、サーバーが起動したらと、「サーバー項目」を作成します 派生したクラスのオブジェクトではサーバー項目`COleServerItem`サーバーのドキュメントとコンテナー アプリケーション間のインターフェイスを提供します。

`COleServerItem`クラスは、コンテナーからの要求に対する応答として、通常、OLE、によって呼び出されるいくつかのオーバーライド可能なメンバー関数を定義します。 サーバーのアイテムには、サーバーのドキュメントまたはドキュメント全体の一部を表すことができます。 OLE アイテムは、コンテナー ドキュメントに埋め込まれた、サーバーのアイテムは、サーバー全体のドキュメントを表します。 OLE 項目がリンクされている場合、サーバー項目はサーバーのドキュメントまたはリンクが一部または全体がかどうかに応じて、ドキュメント全体の一部を表すことができます。

[HIERSVR](../overview/visual-cpp-samples.md)サーバー アイテムのクラス、たとえば、サンプル`CServerItem`、クラスのオブジェクトへのポインターであるメンバーを持つ`CServerNode`します。 `CServerNode`オブジェクトがツリーの HIERSVR アプリケーションのドキュメント内のノード。 ときに、`CServerNode`オブジェクトは、ルート ノード、`CServerItem`オブジェクトはドキュメント全体を表します。 ときに、`CServerNode`オブジェクトが子ノード、`CServerItem`オブジェクトは、ドキュメントの一部を表します。 MFC OLE サンプルを参照して[HIERSVR](../overview/visual-cpp-samples.md)この相互作用の例についてはします。

##  <a name="_core_implementing_server_items"></a> サーバーのアイテムを実装します。

アプリケーションの"starter"コードを生成するために、アプリケーション ウィザードを使用する場合は、OLE オプション ページからサーバー オプションのいずれかを選択する初期コードでのサーバーのアイテムをするために必要なです。 既存のアプリケーション サーバーのアイテムを追加する場合、次の手順に従います。

#### <a name="to-implement-a-server-item"></a>サーバーのアイテムを実装するには

1. `COleServerItem` の派生クラスを作成します。

1. 派生クラスでオーバーライド、`OnDraw`メンバー関数。

   Framework 呼び出し`OnDraw`メタファイルに OLE 項目を表示するためにします。 コンテナー アプリケーションでは、項目を表示するためにこのメタファイルを使用します。 アプリケーションのビューのクラスがあります、`OnDraw`メンバー関数は、サーバー アプリケーションがアクティブなときに、項目を表示するために使用します。

1. 実装のオーバーライドを`OnGetEmbeddedItem`サーバー ドキュメント クラス。 詳細については、この記事を参照してください。[サーバー。サーバー ドキュメントの実装](../mfc/servers-implementing-server-documents.md)と MFC OLE サンプル[HIERSVR](../overview/visual-cpp-samples.md)します。

1. サーバー項目クラスの実装`OnGetExtent`メンバー関数。 フレームワークは、アイテムのサイズを取得するには、この関数を呼び出します。 既定の実装では、何も行われません。

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> サーバー アイテムのアーキテクチャのヒント

説明したとおり[サーバー アイテムの実装](#_core_implementing_server_items)、サーバー アプリケーションは、サーバーの表示とコンテナー アプリケーションで使用される、メタファイル、アイテムを表示できる必要があります。 Microsoft Foundation Class ライブラリのアプリケーション アーキテクチャでビュー クラスの`OnDraw`メンバー関数は、編集するときに、項目を表示します (を参照してください[詳細](../mfc/reference/cview-class.md#ondraw)で、*クラス ライブラリ リファレンス*). サーバー項目の`OnDraw`メタファイルそれ以外の場合に、項目を表示します (を参照してください[:ondraw](../mfc/reference/coleserveritem-class.md#ondraw))。

サーバー ドキュメント クラスにヘルパー関数を記述してからそれらを呼び出すコードの重複を回避できます、`OnDraw`クラス ビューとサーバー項目クラスの関数。 MFC OLE サンプル[HIERSVR](../overview/visual-cpp-samples.md)では、この方法: 関数は、`CServerView::OnDraw`と`CServerItem::OnDraw`両方呼び出す`CServerDoc::DrawTree`項目のレンダリングにします。

ビューと項目の両方がある`OnDraw`メンバー関数のさまざまな条件で描画するためです。 ビューは、ズーム、選択範囲のサイズと範囲、クリッピング、およびスクロール バーなどのユーザー インターフェイス要素としてなどの条件を考慮する必要があります。 OLE オブジェクト全体を描画常に、その一方で、サーバーのアイテム、しています。

詳細については、次を参照してください[詳細](../mfc/reference/cview-class.md#ondraw)、 [COleServerItem](../mfc/reference/coleserveritem-class.md)、 [:ondraw](../mfc/reference/coleserveritem-class.md#ondraw)、および[COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)。で、*クラス ライブラリ リファレンス*します。

## <a name="see-also"></a>関連項目

[サーバー](../mfc/servers.md)
