---
title: レコード セット:スクロール (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 5df8151664bd7e726087cb5323c1e4622264ad23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397722"
---
# <a name="recordset-scrolling-odbc"></a>レコード セット:スクロール (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

レコード セットを開いた後、必要があります値を表示するレコードにアクセスする計算を行う、レポートを生成したり。 スクロールのセット内のレコード間を移動できます。

このトピックでは、次の内容について説明します。

- [1 つのレコードをレコード セット内の別のスクロール方法](#_core_scrolling_from_one_record_to_another)します。

- [スクロールの状況を通知し、サポートされていません ](#_core_when_scrolling_is_supported)します。

##  <a name="_core_scrolling_from_one_record_to_another"></a> 1 つのレコードをスクロール

クラス`CRecordset`提供、`Move`レコード セット内でのスクロール用のメンバー関数。 これらの関数は、行セットによって、現在のレコードを移動します。 バルク行フェッチを実装している場合、`Move`操作は、行セットのサイズによって、レコード セットを再配置されます。 バルク行フェッチへの呼び出しを実装していないかどうか、`Move`関数の位置を変更、レコード セットを 1 つのレコードごとにします。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

> [!NOTE]
>  レコード セットを表示するとき、削除されたレコードがスキップされない可能性があります。 詳細については、次を参照してください。、 [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)メンバー関数。

加え、`Move`関数、`CRecordset`レコード セットの先頭または末尾のスクロールしたかどうかを確認するためのメンバー関数を提供します。

スクロールがレコード セットで使用できるかどうかを確認するのには、呼び出し、`CanScroll`メンバー関数。

#### <a name="to-scroll"></a>スクロールするには

1. 1 つのレコードまたは 1 つの行セットを転送: 呼び出す、 [MoveNext](../../mfc/reference/crecordset-class.md#movenext)メンバー関数。

1. 旧バージョンとの 1 つのレコードまたは 1 つの行セット: 呼び出す、 [MovePrev](../../mfc/reference/crecordset-class.md#moveprev)メンバー関数。

1. レコード セットの最初のレコードを: 呼び出す、 [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)メンバー関数。

1. レコード セットの最後のレコードまたは最後の行セット: 呼び出す、 [MoveLast](../../mfc/reference/crecordset-class.md#movelast)メンバー関数。

1. *N*現在位置を基準レコード: 呼び出す、[移動](../../mfc/reference/crecordset-class.md#move)メンバー関数。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>末尾または先頭のレコード セットをテストするには

1. 最後のレコードまでスクロールしたでしょうか。 呼び出す、 [IsEOF](../../mfc/reference/crecordset-class.md#iseof)メンバー関数。

1. (逆方向に移動する) 最初のレコードをスクロールしたでしょうか。 呼び出す、 [IsBOF](../../mfc/reference/crecordset-class.md#isbof)メンバー関数。

次のコード例では`IsBOF`と`IsEOF`どちらの方向にスクロールする場合は、レコード セットの制限を検出します。

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF` 過去の最後のレコードのレコード セットが配置されている場合は、0 以外の値を返します。 `IsBOF` (すべてのレコード) の前に、最初のレコードの前に、レコード セットが配置されている場合は、0 以外の値を返します。 どちらの場合は、操作の対象の現在のレコードはありません。 呼び出す場合`MovePrev`とき`IsBOF`は既に TRUE または`MoveNext`とき`IsEOF`が既に TRUE の場合、スロー、 `CDBException`。 使用することも`IsBOF`と`IsEOF`空のレコード セットを確認します。

レコード セットのナビゲーションの詳細については、次を参照してください。[レコード セット。ブックマークと絶対位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)します。

##  <a name="_core_when_scrolling_is_supported"></a> スクロールがサポートされている場合

設計された、としては、前方スクロール SQL が提供されるが、ODBC がスクロール機能を拡張できます。 スクロールのサポート レベルが ODBC ドライバーを使用すると、ドライバーの ODBC API への準拠レベルでは、アプリケーションの動作に依存し、ODBC カーソル ライブラリがメモリに読み込まれるかどうか。 詳細については、次を参照してください[ODBC](../../data/odbc/odbc-basics.md)と[ODBC:。ODBC カーソル ライブラリ](../../data/odbc/odbc-the-odbc-cursor-library.md)します。

> [!TIP]
>  カーソル ライブラリを使用するかどうかを制御できます。 参照してください、*データ*と*dwOptions*パラメーター [cdatabase::open](../../mfc/reference/cdatabase-class.md#open)します。

> [!NOTE]
>  MFC DAO クラスとは異なり、MFC ODBC クラスに渡さないように一連の`Find`関数の指定した条件を満たす次 (または前) のレコードを検索します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[レコードセット: レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)