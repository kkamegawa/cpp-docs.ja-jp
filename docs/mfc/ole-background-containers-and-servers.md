---
title: OLE の背景知識:コンテナーとサーバー
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: c154562e58cf8f37d77df61556fe25b19ca54c70
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346109"
---
# <a name="ole-background-containers-and-servers"></a>OLE の背景知識:コンテナーとサーバー

コンテナー アプリケーションは、独自のドキュメントに埋め込まれたまたはリンクされた項目を取り入れることのできるアプリケーションです。 コンテナーのアプリケーションによって管理されているドキュメントを保存して、アプリケーション自体によって作成されたデータと同様に OLE ドキュメント コンポーネントを表示できる必要があります。 コンテナー アプリケーションは、ユーザーが新しい項目を挿入または既存の項目を編集するには、必要な場合に、サーバー アプリケーションをアクティブ化を許可することもあります。 コンテナー アプリケーションのユーザー インターフェイスの要件は、記事に記載されて[コンテナー。ユーザー インターフェイスの問題](../mfc/containers-user-interface-issues.md)します。

サーバー アプリケーションまたはコンポーネントのアプリケーションは、コンテナー アプリケーションで使用する OLE ドキュメント コンポーネントを作成できるアプリケーションです。 通常、サーバー アプリケーションは、ドラッグ アンド ドロップするか、コンテナー アプリケーションが埋め込みまたはリンクされた項目としてデータを挿入するためのデータをクリップボードにコピーをサポートします。 アプリケーションは、コンテナーとサーバーの両方にあります。

ほとんどのサーバーは、スタンドアロンのアプリケーションまたは完全なサーバーです。これらは、スタンドアロン アプリケーションとして実行することができますかや、コンテナー アプリケーションを起動できます。 ミニサーバーは特殊なコンテナーでのみ起動できるサーバー アプリケーションです。 スタンドアロン アプリケーションとして実行できません。 Microsoft の描画と Microsoft Graph のサーバーでは、miniservers の例を示します。

コンテナーとサーバーは直接通信できません。 代わりに、OLE システム ダイナミック リンク ライブラリ (DLL) を介して通信します。 これらの Dll は、コンテナーとサーバーを呼び出すと、関数を提供し、コンテナーとサーバーは、Dll が呼び出すコールバック関数を提供します。

この通信手段を使用して、サーバー アプリケーションの実装の詳細を把握するコンテナーは必要ありません。 これにより、使用するサーバーの種類を定義することがなく、任意のサーバーによって作成された項目をそのまま使用するためのコンテナーです。 その結果、コンテナー アプリケーションのユーザーには、将来のアプリケーションとデータ形式の利点がかかります。 これらの新しいアプリケーションが OLE コンポーネントである場合は、複合ドキュメントは、これらのアプリケーションによって作成された項目を組み込むためなります。

## <a name="see-also"></a>関連項目

[OLE の背景知識](../mfc/ole-background.md)<br/>
[OLE の背景知識: MFC の実装](../mfc/ole-background-mfc-implementation.md)<br/>
[コンテナー](../mfc/containers.md)<br/>
[サーバー](../mfc/servers.md)<br/>
[コンテナー: クライアント アイテム](../mfc/containers-client-items.md)<br/>
[サーバー: サーバー アイテム](../mfc/servers-server-items.md)
