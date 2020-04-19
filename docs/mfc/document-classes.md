---
title: ドキュメント クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219796"
---
# <a name="document-classes"></a>ドキュメント クラス

ドキュメント テンプレートのオブジェクトによって作成された、ドキュメント クラスのオブジェクトは、アプリケーションのデータを管理します。 これらのクラスのいずれかから、ドキュメントのクラスが派生されます。

ドキュメント クラスのオブジェクトは、オブジェクトの表示と対話します。 ビューのオブジェクトは、ウィンドウのクライアント領域を表す、ドキュメントのデータを表示および対話するユーザーを許可します。 ドキュメントとビューは、ドキュメント テンプレート オブジェクトによって作成されます。

[CDocument](../mfc/reference/cdocument-class.md)<br/>
アプリケーション固有のドキュメントの基本クラス。 ドキュメント クラスまたはクラスから派生`CDocument`します。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
基本的なコンテナーのサポートだけでなく、複合ドキュメントの実装に使用されます。 派生したクラスのコンテナーとして機能します[CDocItem](../mfc/reference/cdocitem-class.md)します。 このクラスは、文書化しの基本クラスは、コンテナーの基底クラスとして使用できます`COleServerDoc`します。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
派生したクラス`COleDocument`をリンクするため、インフラストラクチャを提供します。 代わりにこのクラスから、コンテナー アプリケーションのドキュメント クラスを派生する必要があります`COleDocument`埋め込みオブジェクトへのリンクをサポートするためにしたい場合。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
リッチ エディット コントロールに含まれる OLE クライアント アイテムの一覧を保持します。 併用[CRichEditView](../mfc/reference/cricheditview-class.md)と[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)します。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
サーバー アプリケーションのドキュメント クラスの基底クラスとして使用します。 `COleServerDoc` オブジェクトとの対話を通じてサーバーのサポートの大部分を提供する[COleServerItem](../mfc/reference/coleserveritem-class.md)オブジェクト。 クラス ライブラリのドキュメント/ビュー アーキテクチャを使用してビジュアル編集機能が提供されます。

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
で[CHtmlEditView](../mfc/reference/chtmleditview-class.md)MFC のドキュメント/ビュー アーキテクチャのコンテキスト内で HTML の WebBrowser 編集プラットフォームの機能です。

## <a name="related-classes"></a>関連するクラス

ドキュメント クラスのオブジェクトを永続的なことができるなどの状態をストレージ メディアに書き込むし、それを読み出す、つまり、します。 MFC に用意されて、`CArchive`ドキュメントのデータをストレージ メディアに転送を容易にするクラス。

[CArchive](../mfc/reference/carchive-class.md)<br/>
使用と連携して、 [CFile](../mfc/reference/cfile-class.md)永続的ストレージにシリアル化を通じてオブジェクトを実装するオブジェクト (を参照してください[cobject::serialize](../mfc/reference/cobject-class.md#serialize))。

ドキュメントは、OLE オブジェクトを含めることもできます。 `CDocItem` サーバーとクライアントの項目の基本クラスです。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象基本クラスの[COleClientItem](../mfc/reference/coleclientitem-class.md)と[COleServerItem](../mfc/reference/coleserveritem-class.md)します。 派生したクラスのオブジェクトを`CDocItem`文書の一部を表します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
