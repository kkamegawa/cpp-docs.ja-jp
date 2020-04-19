---
title: OLE コンテナー クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 87db824e5ab4daec15870b245ea8341be7442109
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186011"
---
# <a name="ole-container-classes"></a>OLE コンテナー クラス

これらのクラスは、コンテナーのアプリケーションによって使用されます。 両方`COleLinkingDoc`と`COleDocument`のコレクションを管理`COleClientItem`オブジェクト。 ドキュメント クラスから派生するのではなく`CDocument`から派生します`COleLinkingDoc`または`COleDocument`ドキュメントに埋め込まれたオブジェクトへのリンクのサポートが必要かどうかによって異なります。

使用して、`COleClientItem`をドキュメント別のドキュメントからに埋め込まれたか、別のドキュメントへのリンクの各 OLE 項目を表すオブジェクト。

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Active ドキュメント コンテインメントをサポートしています。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
基本的なコンテナーのサポートだけでなく、複合ドキュメントの実装に使用されます。 派生したクラスのコンテナーとして機能します`CDocItem`します。 このクラスは、文書化しの基本クラスは、コンテナーの基底クラスとして使用できます`COleServerDoc`します。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
派生したクラス`COleDocument`をリンクするため、インフラストラクチャを提供します。 代わりにこのクラスから、コンテナー アプリケーションのドキュメント クラスを派生する必要があります`COleDocument`埋め込みオブジェクトへのリンクをサポートするためにしたい場合。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
リッチ エディット コントロールに含まれる OLE クライアント アイテムの一覧を保持します。 併用[CRichEditView](../mfc/reference/cricheditview-class.md)と[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)します。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象基本クラスの`COleClientItem`と`COleServerItem`します。 派生したクラスのオブジェクトを`CDocItem`文書の一部を表します。

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
埋め込みまたはリンクされている OLE アイテムへの接続のクライアント側を表すクライアント項目クラス。 クライアント アイテムは、このクラスから派生します。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Ole 項目で使用する場合は、リッチ エディット コントロールに格納されているクライアント側のアクセスを提供します。`CRichEditView`と`CRichEditDoc`します。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE の処理中のエラーによる例外。 このクラスは、コンテナーとサーバーの両方で使用されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
