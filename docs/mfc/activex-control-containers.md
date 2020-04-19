---
title: ActiveX コントロール コンテナー
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: e8340acafc81447052fcb8d90df8997e81dc4117
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394859"
---
# <a name="activex-control-containers"></a>ActiveX コントロール コンテナー

ActiveX コントロール コンテナーは ActiveX コントロールを完全にサポートするコンテナーであり、それらを独自のウィンドウまたはダイアログに組み込むことができます。 ActiveX コントロールは、多くの開発プロジェクトで使用できる再利用可能なソフトウェア要素です。 コントロールは、データベースへのアクセス、データを監視し、アプリケーション内でさまざまな項目を選択して、アプリケーションのユーザーを許可します。 ActiveX コントロールの詳細については、この記事を参照してください。 [MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

通常、コントロールのコンテナーは、プロジェクトの 2 つの形式を取ります。

- ダイアログとダイアログ ボックスでの ActiveX コントロールのどこかの使用 ダイアログのような windows フォーム ビューなど。

- ActiveX コントロールが、ツールバー、またはユーザーのウィンドウで他の場所で使用されているアプリケーションでは、Windows。

ActiveX コントロール コンテナーと対話を使用してコントロールに公開される[メソッド](../mfc/mfc-activex-controls-methods.md)と[プロパティ](../mfc/mfc-activex-controls-properties.md)します。 これらのメソッドとプロパティは、アクセスおよび変更できるコントロール コンテナーは、ActiveX コントロール コンテナーのプロジェクト内のラッパー クラスを通じてアクセスされます。 埋め込みの ActiveX コントロールが (送信) を発生させることによって、コンテナーと対話できますも[イベント](../mfc/mfc-activex-controls-events.md)アクションが発生したコンテナーに通知します。 かどうか、これらの通知時に機能するコントロールのコンテナーを選択できます。

その他の記事では、Visual C でビルドされた ActiveX コントロール コンテナーに関連する基本的な実装の問題に ActiveX コントロール コンテナー プロジェクトの作成から、いくつかのトピックについて説明します。

- [MFC ActiveX コントロール コンテナーの作成](../mfc/reference/creating-an-mfc-activex-control-container.md)

- [ActiveX コントロールのコンテナー](../mfc/containers-for-activex-controls.md)

- [ActiveX コントロール コンテナー: ActiveX コントロール サポートの手動による有効化](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX コントロール コンテナー: コントロール コンテナー アプリケーションへのコントロールの追加](../mfc/inserting-a-control-into-a-control-container-application.md)

- [ActiveX コントロール コンテナー: ActiveX コントロールとメンバー変数の関連付け](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX コントロール コンテナー: ActiveX コントロールからイベントの処理](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX コントロール コンテナー: コントロール プロパティの表示と変更](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX コントロール コンテナー: ActiveX コントロール コンテナーでの ActiveX コントロールのプログラミング](../mfc/programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX コントロール コンテナー: ダイアログ ベースではないコンテナーでのコントロールの使用](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)

ダイアログ ボックスに ActiveX コントロールの使用方法の詳細については、次を参照してください。、[ダイアログ エディター](../windows/dialog-editor.md)トピック。

Visual C と MFC ActiveX コントロールのクラスを使用して ActiveX コントロールの開発の詳細を説明する記事の一覧は、次を参照してください。 [MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)します。 記事は、機能カテゴリでグループ化されます。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
