---
title: Active ドキュメント サーバー
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394976"
---
# <a name="active-document-servers"></a>Active ドキュメント サーバー

その他のアプリケーションの種類のホスト ドキュメントの Word、Excel、または PowerPoint などの active ドキュメント サーバーでは、アクティブなドキュメントと呼ばれます。 OLE の埋め込み (これは、別のドキュメントのページに表示されるだけ) オブジェクトでは、アクティブなドキュメントが、完全なインターフェイスとそれを作成したサーバー アプリケーションの完全なネイティブ機能を提供します。 ユーザーがドキュメントを作成できます (有効になっているアクティブなドキュメントの場合) は、使い慣れたアプリケーションの全機能を使用してまだ扱うことができます、結果として得られるプロジェクトとして 1 つのエンティティ。

アクティブなドキュメントでは、1 ページ以上を持つことができ、インプレース アクティブでは常にします。 アクティブなドキュメントで、メニューのマージ、ユーザー インターフェイスの一部の制御、**ファイル**と**ヘルプ**コンテナーのメニュー。 コンテナーの編集領域全体を占めるいて、ビューとプリンターのページ (余白やページ フッター、) のレイアウトを制御します。

MFC では、active ドキュメント サーバーには、ドキュメント/ビューのインターフェイス、コマンドのディスパッチ マップ、印刷、メニューの管理、およびレジストリの管理を実装します。 特定のプログラミング要件については[active ドキュメント](../mfc/active-documents.md)します。

MFC でのアクティブなドキュメントをサポートしています、 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)クラスから派生した[CCmdTarget](../mfc/reference/ccmdtarget-class.md)、および[CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)から派生した[COleServerItem](../mfc/reference/coleserveritem-class.md)します。 MFC での active ドキュメント コンテナーをサポートしています、 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)クラスから派生した[COleClientItem](../mfc/reference/coleclientitem-class.md)します。

`CDocObjectServer` アクティブなドキュメントは、インターフェイスしを初期化し、アクティブ ドキュメントをアクティブにマップされます。 MFC には、コマンドは、アクティブなドキュメントのルーティングを処理するためにマクロも用意されています。 アプリケーションでアクティブなドキュメントを使用するには、StdAfx.h ファイルに AfxDocOb.h を含めます。

通常の MFC サーバー フック独自`COleServerItem`-クラスを派生します。 MFC アプリケーション ウィザードは、選択した場合のこのクラスを生成、**ミニ サーバー**または**フル サーバー**複合ドキュメント サポートをアプリケーション サーバーに付与する チェック ボックス。 選択した場合、 **Active ドキュメント サーバー**チェック ボックスをオンから派生したクラスを生成する MFC アプリケーション ウィザード`CDocObjectServerItem`代わりにします。

`COleDocObjectItem`クラスが、OLE コンテナーの active ドキュメント コンテナーになることができます。 MFC アプリケーション ウィザードを使用して、選択して、active ドキュメント コンテナーを作成することができます、 **Active ドキュメント コンテナー** MFC アプリケーション ウィザードの [複合ドキュメント サポート] ページでチェック ボックスをオンします。 詳細については、次を参照してください。 [Active ドキュメント コンテナー アプリケーションを作成する](../mfc/creating-an-active-document-container-application.md)します。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテインメント](../mfc/active-document-containment.md)
