---
title: トランザクション:トランザクション (ODBC) の更新プログラムに与える影響
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 996b8410366661cb91cf82cfff823f17d3aad8b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329908"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>トランザクション:トランザクション (ODBC) の更新プログラムに与える影響

更新、[データソース](../../data/odbc/data-source-odbc.md)をエディット バッファー (トランザクションの外部で使用される同じメソッド) を使用してトランザクションの中に管理されます。 レコード セットのフィールド データ メンバーは、まとめて、レコード セットを中に一時的にバックアップの現在のレコードを含むをエディット バッファーとして機能する`AddNew`または`Edit`します。 中に、`Delete`操作、現在のレコードはトランザクション内でバックアップされません。 エディット バッファーと更新プログラムが現在のレコードを格納する方法の詳細については、次を参照してください。[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)します。

> [!NOTE]
>  バルク行フェッチを実装した場合を呼び出すことはできません`AddNew`、 `Edit`、または`Delete`します。 代わりに、データ ソースへの更新を実行する独自の関数を記述する必要があります。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

トランザクション中に`AddNew`、 `Edit`、および`Delete`操作をコミットまたはロールバックすることができます。 効果`CommitTrans`と`Rollback`現在のレコードをエディット バッファーに復元されない場合があります。 理解しておく必要が現在のレコードが正しく復元されていることを確認する方法、`CommitTrans`と`Rollback`のメンバー関数`CDatabase`の更新関数と連携して`CRecordset`します。

##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans が更新プログラムに与える影響

次の表の説明の効果`CommitTrans`トランザクションにします。

### <a name="how-committrans-affects-updates"></a>CommitTrans が更新プログラムに与える影響

|操作|データ ソースの状態|
|---------------|---------------------------|
|`AddNew` `Update`、し、 `CommitTrans`|新しいレコードは、データ ソースに追加されます。|
|`AddNew` (なし`Update`)、し、 `CommitTrans`|新しいレコードが失われます。 レコードがデータ ソースに追加されません。|
|`Edit` `Update`、し、 `CommitTrans`|データ ソースにコミットを編集します。|
|`Edit` (なし`Update`)、し、 `CommitTrans`|レコードの編集に失われます。 レコードは、データ ソースでは変更されません。|
|`Delete` そうしたら `CommitTrans`|レコードのデータ ソースから削除します。|

##  <a name="_core_how_rollback_affects_updates"></a> ロールバックがトランザクションに与える影響

次の表の説明の効果`Rollback`トランザクションにします。

### <a name="how-rollback-affects-transactions"></a>ロールバックがトランザクションに与える影響

|操作|現在のレコードの状態|する必要があります。|データ ソースの状態|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` `Update`、し、 `Rollback`|現在のレコードのコンテンツは、新しいレコードを確保するために一時的に格納されます。 新しいレコードは、エディット バッファーに入力されます。 後`Update`を呼び出すと、現在のレコードをエディット バッファーに復元します。||によるデータ ソースへの追加`Update`は逆になります。|
|`AddNew` (なし`Update`)、し、 `Rollback`|現在のレコードのコンテンツは、新しいレコードを確保するために一時的に格納されます。 編集バッファーに新しいレコードが含まれています。|呼び出す`AddNew`に空の新しいレコードをエディット バッファーを復元します。 呼び出しまたは`Move`エディット バッファーに古い値を復元するには、(0)。|`Update`が呼び出されていないデータ ソースに加えられた変更はありませんでした。|
|`Edit` `Update`、し、 `Rollback`|現在のレコードの編集前のバージョンは、一時的に格納されます。 エディット バッファーの内容が編集されています。 後`Update`が呼び出されると、編集前のレコードのバージョンがまだ一時的に格納されています。|*ダイナセット*:現在のレコードからエディット バッファーに、レコードの編集前のバージョンを復元するバックアップをスクロールします。<br /><br /> *スナップショット*:呼び出す`Requery`をデータ ソースからレコード セットを更新します。|によるデータ ソースへの変更`Update`は逆になります。|
|`Edit` (なし`Update`)、し、 `Rollback`|現在のレコードの編集前のバージョンは、一時的に格納されます。 エディット バッファーの内容が編集されています。|呼び出す`Edit`にエディット バッファーに、レコードの編集前のバージョンを復元します。|`Update`が呼び出されていないデータ ソースに加えられた変更はありませんでした。|
|`Delete` そうしたら `Rollback`|現在のレコードの内容は削除されます。|呼び出す`Requery`データ ソースから現在のレコードの内容を復元します。|データ ソースからデータの削除が取り消されます。|

## <a name="see-also"></a>関連項目

[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[トランザクション: レコードセットでのトランザクションの実行 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)