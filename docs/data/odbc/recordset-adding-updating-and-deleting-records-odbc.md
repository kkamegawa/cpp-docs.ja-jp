---
title: レコード セット:追加、更新、および削除 (Odbc)
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 28c885119816c1df662cc0b941e02cb3cf747f3d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395626"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>レコード セット:追加、更新、および削除 (Odbc)

このトピックの内容は、MFC ODBC クラスに該当します。

> [!NOTE]
>  大量のレコードをより効率的に追加する方法もあります。 詳細については、次を参照してください。[レコード セット。レコードを追加する方法 (ODBC) で](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)します。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを使用している場合は、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

更新できるスナップショットとダイナセットでは、レコードを追加、編集 (更新)、削除できます。 このトピックでは、次の内容について説明します。

- [レコード セットは更新可能かどうかを確認する](#_core_determining_whether_your_recordset_is_updatable)します。

- [新しいレコードを追加する方法](#_core_adding_a_record_to_a_recordset)します。

- [既存のレコードを編集する方法](#_core_editing_a_record_in_a_recordset)します。

- [レコードを削除する方法](#_core_deleting_a_record_from_a_recordset)します。

更新プログラムを実行する方法の詳細については、out し、更新プログラムが他のユーザーに表示する方法を参照してください。[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)します。 通常は、レコードを追加、編集、または削除すると、すぐにレコードセットによってデータ ソースが更新されます。 また、一連の更新処理をトランザクションにまとめることもできます。 トランザクションを開始すると、そのトランザクションをコミットするまで、更新処理は終了しません。 したがって、更新をやり直すことができます。 トランザクションについては、次を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

レコードセットの更新方法と更新設定の関係を次の表に示します。

### <a name="recordset-readupdate-options"></a>レコードセットの読み出し/更新用の選択肢

|型|読み取り|レコードの編集|レコードの削除|新規作成 (追加)|
|----------|----------|-----------------|-------------------|------------------------|
|読み取り専用|Y|N|N|N|
|追加のみ可能 (Append-only)|Y|N|N|Y|
|すべて更新可能|Y|Y|Y|Y|

##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> 確認するかどうか、レコード セットは更新

レコードセット オブジェクトは、データ ソースが更新可能であり、レコードセットが更新できるという設定で開かれている場合に更新できます。 また、使用する SQL ステートメント、ODBC ドライバーの機能、ODBC カーソル ライブラリがメモリ内にあるかどうかなどに応じて更新できるかどうかが決まります。 レコードセットかデータ ソースが読み取り専用のときは、更新できません。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>レコードセットが更新可能かどうかを調べるには

1. レコード セット オブジェクトの[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)メンバー関数。

   `CanUpdate` は、レコードセットが更新可能なときは 0 以外の値を返します。

既定では、レコード セットは、完全に更新可能な (を実行できます`AddNew`、 `Edit`、および`Delete`操作)。 使用することもできますが、 [appendOnly](../../mfc/reference/crecordset-class.md#open)更新可能なレコード セットを開くにはオプションです。 この方法で開いたレコードセットでは、`AddNew` を使用して新しいレコードを追加することだけができます。 既存のレコードを編集または削除することはできません。 レコード セットが呼び出すことによって追加のためだけに開いているかどうかをテストすることができます、 [CanAppend](../../mfc/reference/crecordset-class.md#canappend)メンバー関数。 レコードセットがすべて更新できる場合、または追加のためだけに開かれている場合は、`CanAppend` が 0 以外の値を返します。

次の例では、レコードセット オブジェクト `CanUpdate` に対して `rsStudentSet` を使用しています。

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
>  呼び出してレコード セットを更新する前に`Update`、レコード セットが、テーブル (または、すべてのテーブルの一意のインデックスの列) の主キーを作成するすべての列が含まれることに注意します。 場合によっては、フレームワークは、レコードセット内で選択されている列だけに基づいてテーブル内の更新するレコードを特定します。 選択されている列数が不足していると、テーブル内の複数のレコードが更新されることがあり、場合によっては、テーブルの参照整合性が損なわれます。 呼び出すときにフレームワークが例外をスローするこの例では、`Update`します。

##  <a name="_core_adding_a_record_to_a_recordset"></a> レコード セットにレコードを追加します。

場合、新しいレコードをレコード セットに追加することができます、 [CanAppend](../../mfc/reference/crecordset-class.md#canappend)メンバー関数は 0 以外の値を返します。

#### <a name="to-add-a-new-record-to-a-recordset"></a>新しいレコードをレコードセットに追加するには

1. レコードセットがレコード追加可能レコードセットであることを確認します。

1. レコード セット オブジェクトの[AddNew](../../mfc/reference/crecordset-class.md#addnew)メンバー関数。

   `AddNew` は、レコードセットをエディット バッファーとして利用できるようにします。 すべてのフィールド データ メンバーが特殊な値が Null に設定し、未変更の印を呼び出すときに、値がデータ ソースに書き込まれます (ダーティ) に変更されただけ[Update](../../mfc/reference/crecordset-class.md#update)します。

1. 新しいレコードのフィールド データ メンバーの値を設定します。

   フィールド データ メンバーに値を代入します。 代入しなかったフィールドはデータ ソースに書き出されません。

1. レコード セット オブジェクトの`Update`メンバー関数。

   `Update` データ ソースに新しいレコードを書き込むことで、追加を完了します。 呼び出しに失敗した場合に処理する方法について`Update`を参照してください[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)します。

追加したレコードをレコード セットに表示されるのとレコード追加のしくみについては、次を参照してください。[レコード セット。AddNew の編集、および削除 (ODBC) の作業](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)します。

次に、新しいレコードを追加する例を示します。

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
>  キャンセルする、`AddNew`または`Edit`呼び出し、単に別の呼び出しを行う`AddNew`または`Edit`呼び出したり`Move`で、 *AFX_MOVE_REFRESH*パラメーター。 データ メンバーは前回の値にリセットされにまだいる`Edit`または`Add`モード。

##  <a name="_core_editing_a_record_in_a_recordset"></a> レコード セットのレコードの編集

既存のレコードを編集するには、場合、レコード セットの[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)メンバー関数は 0 以外の値を返します。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>レコードセット内の既存のレコードを編集するには

1. レコードセットが更新可能であることを確認します。

1. 更新するレコードに移動 (スクロール) します。

1. レコード セット オブジェクトの[編集](../../mfc/reference/crecordset-class.md#edit)メンバー関数。

   `Edit` は、レコードセットをエディット バッファーとして利用できるようにします。 すべてのフィールド データ メンバーに未変更の印が付けられます。 呼び出すと、データ ソースに変更されたフィールド データ メンバーの新しい値が書き込まれる[Update](../../mfc/reference/crecordset-class.md#update)します。

1. 新しいレコードのフィールド データ メンバーの値を設定します。

   フィールド データ メンバーに値を代入します。 値を代入しなかったフィールドには変更前の値が残ります。

1. レコード セット オブジェクトの`Update`メンバー関数。

   `Update` データ ソースに変更されたレコードを書き込むことで、編集を完了します。 呼び出しに失敗した場合に処理する方法について`Update`を参照してください[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)します。

編集終了後は、編集されたレコードが現在のレコードになります。

次の例は、`Edit`操作。 ここでは、編集するレコードに既に移動しているものと想定しています。

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> キャンセルする、`AddNew`または`Edit`呼び出し、単に別の呼び出しを行う`AddNew`または`Edit`呼び出したり`Move`で、 *AFX_MOVE_REFRESH*パラメーター。 データ メンバーは前回の値にリセットされにまだいる`Edit`または`Add`モード。

##  <a name="_core_deleting_a_record_from_a_recordset"></a> レコード セットからレコードを削除します。

レコードを削除するには、場合、レコード セットの[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)メンバー関数は 0 以外の値を返します。

#### <a name="to-delete-a-record"></a>レコードを削除するには

1. レコードセットが更新可能であることを確認します。

1. 更新するレコードに移動 (スクロール) します。

1. レコード セット オブジェクトの[削除](../../mfc/reference/crecordset-class.md#delete)メンバー関数。

   `Delete` すぐに削除されたレコード セットと、データ ソースの両方としては、レコードをマークします。

   異なり`AddNew`と`Edit`、`Delete`対応持たない`Update`呼び出します。

1. 別のレコードに移動 (スクロール) します。

   > [!NOTE]
   >  レコードセット内を移動する場合、削除したレコードがスキップされないことがあります。 詳細については、次を参照してください。、 [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)メンバー関数。

次の例は、`Delete`操作。 ここでは、削除するレコードに既に移動しているものと想定しています。 後`Delete`が呼び出されると、することが重要新しいレコードに移動します。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

影響の詳細については、 `AddNew`、 `Edit`、および`Delete`メンバー関数を参照してください[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードのロック (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)