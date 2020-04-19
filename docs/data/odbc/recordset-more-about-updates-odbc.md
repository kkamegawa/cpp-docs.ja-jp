---
title: レコード セット:詳細については、更新 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: c29ff110fc507c4e449b2f3d082d98c159a35107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397771"
---
# <a name="recordset-more-about-updates-odbc"></a>レコード セット:詳細については、更新 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、次の内容について説明します。

- [トランザクションなどの他の操作が更新プログラムに与える影響](#_core_how_transactions_affect_updates)します。

- [更新プログラムや他のユーザーの](#_core_your_updates_and_the_updates_of_other_users)します。

- [詳細については、Update および Delete のメンバー関数は](#_core_more_about_update_and_delete)します。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを実装した場合、情報の一部は適用されません。 たとえば、呼び出すことはできません、 `AddNew`、 `Edit`、`Delete`と`Update`メンバー関数。 ただし、トランザクションを実行することができます。 バルク行フェッチの詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

##  <a name="_core_how_other_operations_affect_updates"></a> 更新プログラムの他の操作の影響

更新による影響はトランザクション有効で、更新時にトランザクションを完了する前にスクロールして、トランザクションを完了する前に、レコード セットを閉じることで。

###  <a name="_core_how_transactions_affect_updates"></a> トランザクションが更新プログラムに与える影響

理解を超える方法`AddNew`、 `Edit`、および`Delete`作業を理解しておく必要が方法、 `BeginTrans`、 `CommitTrans`、および`Rollback`のメンバー関数[CDatabase](../../mfc/reference/cdatabase-class.md)と連携更新関数[CRecordset](../../mfc/reference/crecordset-class.md)します。

既定では、呼び出し`AddNew`と`Edit`データ ソースを呼び出すとすぐに影響`Update`します。 `Delete` 呼び出しは直ちに有効にします。 ただし、トランザクションを確立し、このような呼び出しのバッチを実行できます。 コミットするまでは、更新プログラムが永続的なされません。 頭を変更する場合をロールバックできますから、そのコミットではなく、トランザクション。

トランザクションの詳細については、次を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> 更新プログラムの影響、レコード セットを閉じる

レコード セット、またはそれに関連を閉じた場合`CDatabase`進行中のトランザクションでのオブジェクト (呼び出さないが[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)または[CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback))、トランザクションはロールバックされます自動的に (がない限り、データベース バックエンド Microsoft Jet データベース エンジン) をバックアップします。

> [!CAUTION]
>  Microsoft Jet データベース エンジンを使用している場合、明示的なトランザクション内でレコード セットを閉じるは発生しませんに変更された行または明示的なトランザクションがコミットまたはロールバックされるまでに配置されていたロックの解除。 そのを常に両方開いて閉じるレコード セットは、内部または外部 Jet の明示的なトランザクションをお勧めします。

###  <a name="_core_how_scrolling_affects_updates"></a> 更新プログラムの影響のスクロール

ときにする[レコード セット。スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) 、レコード セット (前のレコードが最初に保存されませんが) 新しい現在のレコードをエディット バッファーを入力します。 削除されたレコードには、スキップをスクロールします。 後にスクロールする場合、`AddNew`または`Edit`呼び出さずに呼び出し`Update`、 `CommitTrans`、または`Rollback`最初に、変更は失われます (に警告がありません) に新しいレコードが編集のバッファーに読み込まれるとします。 エディット バッファーのスクロール レコードが挿入、レコードが解放されると、およびデータ ソースの変更は行われません。 両方に適用`AddNew`と`Edit`します。

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> 更新プログラムと他のユーザーの更新プログラム

レコード セットを使用してデータを更新するときに、更新プログラムは他のユーザーに影響します。 同様に、レコード セットの有効期間中に他のユーザーの更新プログラムに影響します。

マルチ ユーザー環境では、他のユーザーは、レコード セットで選択した同じレコードの一部が含まれているレコード セットを開くことができます。 レコード セットには、取得する前にレコードへの変更が反映されます。 ダイナセットを使う場合は、スクロールするたびにレコードを取得、ためダイナセットを使う場合は、レコードをスクロールするたびに変更を反映します。 スナップショットは、スナップショットが最初に、レコードをスクロールする前に発生した変更のみを反映させるために、スクロールする初めてのレコードを取得します。

レコード セットには再実行する場合を除き、レコード セットを開いた後、他のユーザーによって追加されたレコードは表示されません。 レコード セットがダイナセットである場合は、影響を受けるレコードをスクロールすると、他のユーザーが既存のレコードを編集は、ダイナセットで表示します。 レコード セットがスナップショットである場合は、スナップショットを再実行するまで、編集内容は表示されません。 追加されたレコードを参照してください。 または、スナップショット、または、ダイナセットでは、他のユーザーによって追加されたレコードの他のユーザーによって削除する場合[:requery](../../mfc/reference/crecordset-class.md#requery) 、レコード セットを再構築します。 (他のユーザーの削除がダイナセットで表示されるメモ。)呼び出すことがありますも`Requery`のレコードを追加するに、削除が表示されないが、します。

> [!TIP]
>  一度にスナップショット全体のキャッシュを強制的に呼び出す`MoveLast`スナップショットを開いた後すぐにします。 呼び出して`MoveFirst`レコードを使用して作業を開始します。 `MoveLast` すべてのレコードをスクロールすると同じですが、それらを一度に取得します。 ただし、パフォーマンスが低下して、一部のドライバーに必要なことができない可能性がありますこのことに注意してください。

他のユーザーに、更新プログラムの効果は、影響と似ています。

##  <a name="_core_more_about_update_and_delete"></a> 詳細については、Update および Delete

このセクションを使用するのに役立つ追加情報を提供します。`Update`と`Delete`します。

### <a name="update-success-and-failure"></a>更新プログラムの成功と失敗

場合`Update`が成功した、`AddNew`または`Edit`モードが終了します。 開始する、`AddNew`または`Edit`モードをもう一度、呼び出し`AddNew`または`Edit`します。

場合`Update`が失敗した (FALSE を返しますまたは例外をスローします) のままにする`AddNew`または`Edit`モードに応じてどの関数が最後に呼び出されます。 次のいずれかを実行できます。

- フィールド データ メンバーを変更して再試行してください、`Update`もう一度です。

- 呼び出す`AddNew`フィールド データ メンバーを Null にリセットする、フィールド データ メンバーの値の設定を呼び出して`Update`もう一度です。

- 呼び出す`Edit`最初の呼び出しの前に、レコード セットに含まれていた値を再読み込みする`AddNew`または`Edit`、フィールド データ メンバーの値を設定、および、呼び出して`Update`もう一度です。 成功したら`Update`呼び出し (後を除き、`AddNew`呼び出し)、フィールド データ メンバーは、新しい値を保持します。

- 呼び出す`Move`(を含む`Move`AFX_MOVE_REFRESH、または 0 のパラメーターを持つ)、変更をすべて消去して、いずれかが終了`AddNew`または`Edit`モードを有効にします。

### <a name="update-and-delete"></a>更新および削除

このセクションの両方に適用されます`Update`と`Delete`します。

`Update`または`Delete`操作では、1 つだけのレコードを更新する必要があります。 そのレコードは、レコード セットのフィールド内のデータ値に対応する現在のレコードです。 場合は、次のいずれかを含むレコードに影響はありませんか、1 つ以上のレコードが影響を受けるなんらかの理由により、例外がスロー **RETCODE**値。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

これらの例外がスローされたときの維持、`AddNew`または`Edit`を呼び出したときにされていた状態`Update`または`Delete`します。 これらの例外が表示される最も一般的なシナリオを次に示します。 最もよく見できました。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED オプティミスティック ロック モードを使用すると、別のユーザーの方法でレコードが変更から正しい更新または削除するレコードを識別するフレームワークを阻止します。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED テーブルを更新するときに、主キーがないか、一意なインデックスとする十分な列でないテーブルの行を一意に識別するレコード セット。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードセットでのレコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[例外: データベースの例外](../../mfc/exceptions-database-exceptions.md)