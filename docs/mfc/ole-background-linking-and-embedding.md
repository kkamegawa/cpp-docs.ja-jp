---
title: OLE の背景知識:リンクと埋め込み
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 02607df2a8fa086c5751f2b446e349a3efdbcd20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186803"
---
# <a name="ole-background-linking-and-embedding"></a>OLE の背景知識:リンクと埋め込み

コンテナー アプリケーションに貼り付けコマンドを使用して、埋め込まれたコンポーネント、または埋め込みアイテムを作成できます。 埋め込みアイテムのソース データが含まれている OLE ドキュメントの一部として格納されます。 この方法では、ワード プロセッサのドキュメントのドキュメント ファイルは、テキストを含めることができ、ビットマップ、グラフ、式、またはその他のあらゆる種類のデータも含めることができます。

別のアプリケーションからデータを組み込む別の方法を提供する OLE: リンクされたコンポーネント、またはリンクされた項目、またはリンクを作成します。 貼り付けコマンドではなくリンク貼り付け コマンドを使用することを除いて、リンクされた項目を作成する手順は、埋め込みアイテムを作成するためのものに似ています。 埋め込みのコンポーネントとは異なりは、リンクされたコンポーネントは、別のファイルには、多くの場合、元のデータへのパスを格納します。

たとえば、ワード プロセッサ ドキュメントの操作は、スプレッドシートのセルへのリンクされた項目を作成して場合、リンクされた項目のデータはスプレッドシートの元のドキュメントに格納されます。 ワード プロセッサのドキュメントには、項目がある、つまり、元のスプレッドシートのドキュメントへのリンクが含まれているを指定する情報のみが含まれています。 セルをダブルクリックすると、スプレッドシート アプリケーションが起動され、スプレッドシートの元のドキュメントが保存された場所から読み込まれます。

すべての OLE 項目埋め込みまたはリンクされた、かどうかを作成したアプリケーションに基づいてに関連付けられている型があります。 たとえば、Microsoft ペイント ブラシの項目が項目の 1 つの種類と Microsoft Excel の項目が別の型。 ただし、一部のアプリケーションでは、1 つ以上の項目の種類を作成できます。 たとえば、Microsoft Excel では、ワークシートの項目、グラフの項目、およびマクロ シートの項目を作成できます。 クラス識別子を使用して、システムによって一意に識別の各アイテムまたは**CLSID**します。

## <a name="see-also"></a>関連項目

[OLE の背景知識](../mfc/ole-background.md)<br/>
[OLE の背景知識: コンテナーとサーバー](../mfc/ole-background-containers-and-servers.md)<br/>
[コンテナー: クライアント アイテム](../mfc/containers-client-items.md)<br/>
[サーバー: サーバー アイテム](../mfc/servers-server-items.md)
