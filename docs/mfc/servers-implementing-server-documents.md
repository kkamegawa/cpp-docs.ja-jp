---
title: サーバー:サーバー ドキュメントの実装
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: 17ced1cdb0b40b13fbda68150030efde5735ba7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307914"
---
# <a name="servers-implementing-server-documents"></a>サーバー:サーバー ドキュメントの実装

この記事では、アプリケーション ウィザードで、OLE サーバー オプションを指定しなかった場合、サーバーのドキュメントを適切に実装するために行う手順について説明します。

#### <a name="to-define-a-server-document-class"></a>サーバー ドキュメント クラスを定義するには

1. ドキュメントからクラスを派生`COleServerDoc`の代わりに`CDocument`します。

1. 派生したサーバーのアイテム クラスを作成`COleServerItem`です。

1. 実装、`OnGetEmbeddedItem`サーバーのドキュメント クラスのメンバー関数。

   `OnGetEmbeddedItem` コンテナー アプリケーションのユーザーを作成または埋め込みアイテムを編集すると呼び出されます。 ドキュメント全体を表す項目が返されます。 オブジェクトがあります、 `COleServerItem`-クラスを派生します。

1. 上書き、`Serialize`メンバー関数は、ドキュメントの内容をシリアル化します。 ドキュメントでネイティブのデータを表すために使用されていない場合は、サーバーのアイテムの一覧をシリアル化する必要はありません。 詳細については、次を参照してください。*サーバー アイテムの実装*記事[サーバー。サーバー項目](../mfc/servers-server-items.md)します。

サーバーのドキュメントが作成されると、フレームワークは、ドキュメントを自動的に OLE システム Dll に登録します。 これにより、サーバーのドキュメントを識別する Dll です。

詳細については、次を参照してください。 [COleServerItem](../mfc/reference/coleserveritem-class.md)と[COleServerDoc](../mfc/reference/coleserverdoc-class.md)で、*クラス ライブラリ リファレンス*します。

## <a name="see-also"></a>関連項目

[サーバー](../mfc/servers.md)<br/>
[サーバー: サーバー アイテム](../mfc/servers-server-items.md)<br/>
[サーバー: サーバーの実装](../mfc/servers-implementing-a-server.md)<br/>
[サーバー: 埋め込み先フレーム ウィンドウの実装](../mfc/servers-implementing-in-place-frame-windows.md)
