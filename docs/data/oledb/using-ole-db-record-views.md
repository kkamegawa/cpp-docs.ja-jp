---
title: OLE DB レコード ビューの使用
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
ms.openlocfilehash: 83f4d64252ab5c2b80d62419ea448c1ffd0cdd69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375185"
---
# <a name="using-ole-db-record-views"></a>OLE DB レコード ビューの使用

MFC アプリケーションで OLE DB 行セットのデータを表示する場合は、MFC クラスを使用して[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)します。 レコード ビュー オブジェクトから作成`COleDBRecordView`MFC コントロールでのデータベース レコードを表示することができます。 レコード ビューが作成された OLE DB 行セット オブジェクトに直接接続ダイアログ フォーム ビュー、`CRowset`テンプレート クラス。 行セット オブジェクトを識別するハンドルを取得するは簡単です。

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

ビューのフィールドの表示、 `CRowset`  ダイアログ ボックスのコントロール内のオブジェクト。 `COleDBRecordView`オブジェクトは、ダイアログ Data Exchange (DDX) を使用し、ナビゲーションの機能に組み込まれて`CRowset`(`MoveFirst`、 `MoveNext`、 `MovePrev`、および`MoveLast`)、フォーム上のコントロール間のデータの移動を自動化するには行セットのフィールド。 `COleDBRecordView` レコード ビューは、ユーザー インターフェイスと提供を更新できるようにに、行セット内のユーザーの位置はの追跡、 [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove)間で移動する前に、現在のレコードを更新するためのメソッド。

DDX 関数を使用する`COleDbRecordView`をデータベースのレコード セットから直接データを取得し、ダイアログ コントロールに表示します。 使用して、 **DDX_** <strong>\*</strong>メソッド (など`DDX_Text`) ではなく、 **DDX_Field** <strong>\*</strong> (関数など`DDX_FieldText`) と`COleDbRecordView`します。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView クラス](../../mfc/reference/coledbrecordview-class.md)<br/>
