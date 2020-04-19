---
title: OLE サーバー クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 99dd7f58b862fadc86ee2515bb8ef2008bc538fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385324"
---
# <a name="ole-server-classes"></a>OLE サーバー クラス

これらのクラスは、サーバー アプリケーションによって使用されます。 サーバー ドキュメントがから派生した`COleServerDoc`からではなく`CDocument`します。 ため`COleServerDoc`から派生`COleLinkingDoc`、サーバー ドキュメントのリンクをサポートするコンテナーをすることもできます。

`COleServerItem`クラスは、ドキュメントまたは別のドキュメントに埋め込まれたまたはにリンクできるドキュメント内の部分を表します。

`COleIPFrameWnd` `COleResizeBar`インプレース オブジェクトが、コンテナーの間の編集をサポートし、 `COleTemplateServer` OLE オブジェクト他のアプリケーションからを編集できるように、ドキュメント/ビューのペアの作成をサポートします。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
サーバー アプリケーションのドキュメント クラスの基底クラスとして使用します。 `COleServerDoc` オブジェクトとの対話を通じてサーバーのサポートの大部分を提供する`COleServerItem`オブジェクト。 クラス ライブラリのドキュメント/ビュー アーキテクチャを使用してビジュアル編集機能が提供されます。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象基本クラスの`COleClientItem`と`COleServerItem`します。 派生したクラスのオブジェクトを`CDocItem`文書の一部を表します。

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
OLE インターフェイスを表すために使用`COleServerDoc`項目。 通常、1 つである`COleServerDoc`、埋め込まれたドキュメントの部分を表すオブジェクト。 ドキュメントの部分へのリンクをサポートするサーバーであります多く`COleServerItem`ドキュメントの一部をリンクを表すオブジェクト。

[クラスからではなく、](../mfc/reference/coleipframewnd-class.md)<br/>
インプレース サーバー ドキュメントを編集するときに、フレーム ウィンドウ ビューを提供します。

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
インプレースでサイズを変更するには、標準のユーザー インターフェイスを提供します。 このクラスのオブジェクトは常に組み合わせて使用`COleIPFrameWnd`オブジェクト。

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
フレームワークのドキュメント/ビュー アーキテクチャを使用してドキュメントを作成するために使用します。 A`COleTemplateServer`オブジェクトは、ほとんどの関連付けられている作業を委任`CDocTemplate`オブジェクト。

[COleException](../mfc/reference/coleexception-class.md)<br/>
OLE の処理中のエラーによる例外。 このクラスは、コンテナーとサーバーの両方で使用されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
