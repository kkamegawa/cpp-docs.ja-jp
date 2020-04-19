---
title: OLE アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b7fa989d1a3b799cf6b427e27142d4479be900bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308187"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>OLE アプリケーションの作成手順

次の表は、OLE リンク、埋め込みアプリケーションを作成することで、役割、およびフレームワークの役割を示します。 これらを実行する手順のシーケンスではなく使用できるオプションを表します。

### <a name="creating-ole-applications"></a>OLE アプリケーションの作成

|タスク|そうですよね|フレームワークを動作します。|
|----------|------------|------------------------|
|COM コンポーネントを作成します。|MFC アプリケーション ウィザードを実行します。 選択**フル サーバー**または**ミニ サーバー**で、**複合ドキュメント サポート**タブ。|フレームワークは、COM コンポーネントの機能が有効になっていると、スケルトン アプリケーションを生成します。 すべての COM 機能は、わずかな変更だけで、既存のアプリケーションに転送できます。|
|コンテナー アプリケーションをゼロから作成します。|MFC アプリケーション ウィザードを実行します。 選択**コンテナー**で、**複合ドキュメント サポート**タブ。クラス ビューを使用すると、ソース コード エディターに移動します。 COM ハンドラー関数のコードを入力します。|フレームワークでは、COM コンポーネント (サーバー) のアプリケーションによって作成された COM オブジェクトを挿入できる、スケルトン アプリケーションを生成します。|
|最初からオートメーションをサポートするアプリケーションを作成します。|MFC アプリケーション ウィザードを実行します。 選択**Automation**から、**高度な機能**タブ。お使いの automation のメソッドとプロパティを公開するのにには、クラス ビューを使用します。|フレームワークには、スケルトン アプリケーションをアクティブ化し、他のアプリケーションによって自動化できますが生成されます。|

## <a name="see-also"></a>関連項目

[フレームワークを使ったアプリケーションの作成](../mfc/building-on-the-framework.md)<br/>
[MFC アプリケーションの作成手順](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[ActiveX コントロールの作成手順](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[データベース アプリケーションの作成手順](../mfc/sequence-of-operations-for-creating-database-applications.md)
