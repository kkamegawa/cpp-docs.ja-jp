---
title: MFC で使用できる派生ビュー クラス
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 61b38f6147a8bde4f6eb42cd144f9f64dac8dbd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152905"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC で使用できる派生ビュー クラス

次の表は、MFC のビュー クラスおよび相互の関係を示します。 ビュー クラスの機能は、派生元である MFC ビュー クラスに依存します。

### <a name="view-classes"></a>ビュー クラス

|クラス|説明|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|すべてのビューの基本クラスです。|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|基本クラスの`CTreeView`、 `CListView`、 `CEditView`、および`CRichEditView`します。 これらのクラスを使用して、指定された Windows のコモン コントロールとドキュメント/ビュー アーキテクチャを使用できます。|
|[CEditView](../mfc/reference/ceditview-class.md)|Windows に基づく単純なビューでは、ボックス コントロールを編集します。 入力とテキストの編集は、単純なテキスト エディター アプリケーションの基礎として使用できます。 参照 `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|ビューを含む、 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)オブジェクト。 このクラスに似ています`CEditView`とは異なり、 `CEditView`、`CRichEditView`書式設定されたテキストのハンドル。|
|[CListView](../mfc/reference/clistview-class.md)|ビューを含む、 [CListCtrl](../mfc/reference/clistctrl-class.md)オブジェクト。|
|[Ctreeview の比較](../mfc/reference/ctreeview-class.md)|ビューを含む、 [CTreeCtrl](../mfc/reference/ctreectrl-class.md) Visual C でソリューション エクスプ ローラー ウィンドウのようにビューのオブジェクト。|
|[CScrollView](../mfc/reference/cscrollview-class.md)|基本クラスの`CFormView`、 `CRecordView`、および`CDaoRecordView`します。 ビューの内容をスクロールを実装します。|
|[CFormView](../mfc/reference/cformview-class.md)|フォーム ビューでは、コントロールを含むビュー。 フォーム ベースのアプリケーションでは、1 つ以上このようなフォーム インターフェイスを提供します。|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|アプリケーションのユーザー サイトを参照できます、World Wide Web のほかフォルダーで、ネットワークおよびローカル ファイル システムで Web ブラウザー ビュー。 Web ブラウザーの表示は、Active ドキュメント コンテナーとしても作業できます。|
|[CRecordView](../mfc/reference/crecordview-class.md)|ODBC データベース レコードをコントロールに表示するフォーム ビュー。 ODBC サポート、プロジェクトを選択した場合、ビューの基底クラスは、`CRecordView`します。 接続されているビューを`CRowset`オブジェクト。|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|DAO データベース レコードをコントロールに表示するフォーム ビュー。 DAO サポート、プロジェクトを選択した場合、ビューの基底クラスは、`CDaoRecordView`します。 接続されているビューを`CDaoRecordset`オブジェクト。|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|コントロールでの OLE DB レコードを表示するフォーム ビュー。 OLE DB のサポートをプロジェクトを選択した場合、ビューの基底クラスは、`COleDBRecordView`します。 接続されているビューを`CRowset`オブジェクト。|

> [!NOTE]
>  MFC バージョン 4.0 の時点で`CEditView`から派生`CCtrlView`します。

これらのクラスを使用して、アプリケーションには、そこから、アプリケーションのビュー クラスを派生します。 関連情報については、次を参照してください。[スケール ビューのスクロールと](../mfc/scrolling-and-scaling-views.md)します。 データベース クラスの詳細については、次を参照してください。[概要。データベース プログラミング](../data/data-access-programming-mfc-atl.md)します。

## <a name="see-also"></a>関連項目

[ビューの使い方](../mfc/using-views.md)
