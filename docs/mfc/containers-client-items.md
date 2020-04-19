---
title: コンテナー:クライアント アイテム
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: 0c7f4a63cb9a31b52be2d3574ddad29313df6a4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153360"
---
# <a name="containers-client-items"></a>コンテナー:クライアント アイテム

この記事では、クライアント アイテムについて説明し、そのクライアント アイテムをアプリケーションのクラスから派生させてください。

クライアント アイテムとは別のアプリケーションに含まれているかによって OLE コンテナー アプリケーションのドキュメント参照に属しているデータ項目です。 データは、ドキュメント内に含まれるクライアント アイテムが埋め込まれます。コンテナーのドキュメントで参照されている別の場所にデータが保存されているものがリンクされます。

OLE アプリケーションでドキュメント クラスは、クラスから派生[COleDocument](../mfc/reference/coledocument-class.md)からではなく`CDocument`します。 `COleDocument`クラスから継承`CDocument`する MFC アプリケーションの基にドキュメント/ビュー アーキテクチャを使用するために必要なすべての機能です。 `COleDocument` コレクションとしてドキュメントを処理するインターフェイスも定義`CDocItem`オブジェクト。 いくつか`COleDocument`の追加、取得、およびそのコレクションの要素を削除するためのメンバー関数が用意されています。

すべてのコンテナー アプリケーションを少なくとも 1 つのクラスから派生させてください`COleClientItem`します。 このクラスのオブジェクトは、埋め込みまたはリンク、OLE ドキュメント内の項目を表します。 ドキュメントから削除される場合を除き、これらのオブジェクトは、それらが格納されたドキュメントの有効期間存在します。

`CDocItem` 基本クラスは、`COleClientItem`と`COleServerItem`します。 これらの 2 つから派生したクラスのオブジェクトは、それぞれ OLE アイテムと、クライアントとサーバー アプリケーション間の仲介役として機能します。 新しい OLE 項目は、ドキュメントに追加されるたびに、MFC フレームワークは、クライアント アプリケーションの新しいオブジェクトを追加します`COleClientItem`-クラスを派生クラスのドキュメントのコレクションから`CDocItem`オブジェクト。

## <a name="see-also"></a>関連項目

[コンテナー](../mfc/containers.md)<br/>
[コンテナー:複合ファイル](../mfc/containers-compound-files.md)<br/>
[コンテナー:ユーザー インターフェイスの問題](../mfc/containers-user-interface-issues.md)<br/>
[コンテナー:高度な機能](../mfc/containers-advanced-features.md)<br/>
[COleClientItem クラス](../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem クラス](../mfc/reference/coleserveritem-class.md)
