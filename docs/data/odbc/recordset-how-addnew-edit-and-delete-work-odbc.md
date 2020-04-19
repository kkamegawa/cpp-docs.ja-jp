---
title: レコード セット:AddNew が編集、および作業 (ODBC) を削除する方法
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: e5fc6ad2a1fe00367cd8a0b1c53ac914b95018ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397836"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>レコード セット:AddNew が編集、および作業 (ODBC) を削除する方法

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックで説明する方法、 `AddNew`、`Edit`と`Delete`クラスのメンバー関数`CRecordset`機能します。 取り上げるトピックは次のとおりです。

- [レコード追加のしくみ](#_core_adding_a_record)

- [追加したレコードの表示](#_core_visibility_of_added_records)

- [レコードの編集の動作方法](#_core_editing_an_existing_record)

- [削除するレコードのしくみ](#_core_deleting_a_record)

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチを使用している場合は、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

読み取りをする可能性がありますの補足として[レコード フィールド エクス チェンジ。RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)、更新操作での RFX の対応するロールをについて説明します。

##  <a name="_core_adding_a_record"></a> レコードを追加します。

レコード セットのレコード セットに新しいレコードを追加するのには[AddNew](../../mfc/reference/crecordset-class.md#addnew) 、メンバー関数は、新しいレコードのフィールド データ メンバーの値を設定して、呼び出し、 [Update](../../mfc/reference/crecordset-class.md#update)書き込むメンバー関数データ ソースのレコード。

呼び出し元の前提条件として`AddNew`、レコード セットする必要がありますが開かれていない読み取り専用です。 `CanUpdate`と`CanAppend`メンバー関数を使用して、これらの条件を確認できます。

呼び出すと`AddNew`:

- 編集のバッファー内のレコードが格納されるため、操作が取り消された場合、その内容を復元することができます。

- フィールド データ メンバーは、後でそれらの変更を検出することができますのでにフラグが設定されます。 (Unchanged) メンバーがでもマークされているフィールドのデータをクリーンアップし、Null に設定します。

呼び出した後`AddNew`、エディット バッファーを表す新しい、空のレコードの準備ができたら値が入力されます。 これを行うを割り当てることによって手動で値を設定するだけです。 フィールドの実際のデータ値を指定するには、代わりに呼び出すことができます`SetFieldNull`を Null 値を指定します。

変更をコミットするには、呼び出します`Update`します。 呼び出すと`Update`の新しいレコード。

- ODBC ドライバーがサポートしている場合、 `::SQLSetPos` MFC ODBC API 関数では、関数を使用して、データ ソースのレコードを追加します。 `::SQLSetPos`、MFC レコードを追加できるより効率的に構築し、SQL ステートメントの処理があるないためです。

- 場合`::SQLSetPos`することはできません MFC は、次を使用します。

   1. 変更が検出されない場合`Update`何も実行し、0 を返します。

   1. 変更がある場合`Update`SQL を構築します**挿入**ステートメント。 すべてのダーティ フィールド データ メンバーによって表される列に記載されて、**挿入**ステートメント。 含まれる列を強制的に、[き](../../mfc/reference/crecordset-class.md#setfielddirty)メンバー関数。

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` 新しいレコードをコミット:、**挿入**ステートメントが実行され、トランザクションが進行しない限り、レコードがデータ ソース (および、レコード セットいない場合、スナップショット) のテーブルにコミットします。

   1. レコードは、エディット バッファーに復元されます。 前に、の現在のレコード、`AddNew`呼び出しがかどうかにかかわらずもう一度最新では、**挿入**ステートメントが正常に実行します。

   > [!TIP]
   > 新しいレコードを完全に制御アプローチ: の値を持つを呼び出して Null のまま、すべてのフィールドを明示的に設定するフィールドの値を設定`SetFieldNull`フィールドと、パラメーターへのポインターを TRUE (既定値)。 フィールドがデータ ソース、呼び出しに書き込まれないことを確認する場合`SetFieldDirty`をフィールドにパラメーター FALSE、ポインターを使用し、フィールドの値を変更しないでください。 フィールドを Null にできるかどうかを確認するのには、呼び出す`IsFieldNullable`します。

   > [!TIP]
   > レコード セットのデータ メンバーの値を変更すると検出、MFC では、レコード セットに格納できるデータの種類ごとに適切な PSEUDO_ 値を使用します。 PSEUDO_ 値にフィールドを明示的に設定する必要がありますを Null としてマークするフィールドが既に動作にも呼び出す必要がある場合`SetFieldNull`、2 番目のパラメーターで、最初のパラメーターと FALSE でフィールドのアドレスを渡します。

##  <a name="_core_visibility_of_added_records"></a> 追加したレコードの表示

追加されたレコードはレコード セットに表示されるでしょうか。 追加したレコード表示することがあり、場合がありますは 2 つのことによって、表示されません。

- どのようなドライバーは、ことができます。

- どのようなフレームワークは、利用できます。

ODBC ドライバーがサポートしている場合、 `::SQLSetPos` MFC ODBC API 関数では、関数を使用して、レコードを追加します。 `::SQLSetPos`、追加したレコードは更新可能な MFC のレコード セットを表示します。 関数のサポートがなければ追加レコードを表示して、呼び出す必要があります`Requery`にそれらを参照してください。 使用して`::SQLSetPos`も効率的です。

##  <a name="_core_editing_an_existing_record"></a> 既存のレコードの編集

レコード セット内の既存のレコードを編集する場合は、レコード セットのレコードをスクロールする必要があります[編集](../../mfc/reference/crecordset-class.md#edit)、メンバー関数は、新しいレコードのフィールド データ メンバーの値を設定して、呼び出し、[更新](../../mfc/reference/crecordset-class.md#update)メンバー関数は、データ ソースに変更されたレコードを書き込めません。

呼び出し元の前提条件として`Edit`、更新可能なとレコードをレコード セットがある必要があります。 `CanUpdate`と`IsDeleted`メンバー関数を使用して、これらの条件を確認できます。 現在のレコードもする必要がありますが削除されておらず、およびレコード セットにレコードが必要です (両方`IsBOF`と`IsEOF`0 が返されます)。

呼び出すと`Edit`をエディット バッファー (現在のレコード) 内のレコードが格納されます。 ストアドのレコードの値は後で、任意のフィールドが変更されたかどうかを検出するために使用します。

呼び出した後`Edit`をエディット バッファーは、引き続き現在のレコードを表しますが、フィールド データ メンバーへの変更をそのまま使用する準備ができました。 レコードを変更するには、手動で編集するフィールドのデータ メンバーの値を設定する必要があります。 フィールドの実際のデータ値を指定するには、代わりに呼び出すことができます`SetFieldNull`を Null 値を指定します。 変更をコミットするには、呼び出す`Update`します。

> [!TIP]
> 活用する`AddNew`または`Edit`モードでは、呼び出し`Move`パラメーターと共に*AFX_MOVE_REFRESH*します。

呼び出し元の前提条件として`Update`レコード セットが空にする必要がありますは、現在のレコードする必要がありますが削除されていません。 `IsBOF`、 `IsEOF`、および`IsDeleted`0 を返す必要があります。

呼び出すと`Update`編集されたレコード。

- ODBC ドライバーがサポートしている場合、 `::SQLSetPos` MFC ODBC API 関数では、関数を使用して、データ ソースのレコードを更新します。 `::SQLSetPos`ドライバー、サーバー、2 つが異なる場合、サーバー上のレコードの更新の対応するレコードと、エディット バッファーを比較します。 `::SQLSetPos`、MFC レコードを更新できるより効率的に構築し、SQL ステートメントの処理があるないためです。

   \- または -

- 場合`::SQLSetPos`することはできません MFC は、次を使用します。

   1. 変更されてがいない場合`Update`何も実行し、0 を返します。

   1. 変更がある場合`Update`SQL を構築します**UPDATE**ステートメント。 示されている列、 **UPDATE**ステートメントが変更されたフィールド データ メンバーに基づきます。

   1. `Update` 変更をコミットします: を実行、**更新**ステートメント- と、データ ソースでレコードが変更されたがコミットされていない場合は、トランザクションが進行中です (を参照してください[トランザクション。レコード セット (ODBC) でトランザクションを実行する](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)については、トランザクションが、更新プログラムに与える影響)。 ODBC も変更すると、レコードのコピーを保持します。

   1. プロセスとは異なり`AddNew`、`Edit`ストアド レコードは復元されません。 編集済みのレコードは、現在のレコードとしての場所に残ります。

   > [!CAUTION]
   > 呼び出してレコード セットを更新する前に`Update`、レコード セットが、テーブル (または、すべてのテーブルにインデックスが一意な行を一意に識別するための十分な列の列) の主キーを作成するすべての列が含まれることに注意します。 場合によっては、フレームワークは、レコードセット内で選択されている列だけに基づいてテーブル内の更新するレコードを特定します。 すべての必要な列のない複数のレコードをテーブルの更新可能性があります。 呼び出すときにフレームワークが例外をスローするこの例では、`Update`します。

   > [!TIP]
   > 呼び出す場合`AddNew`または`Edit`以前がする前に、いずれの関数を呼び出したこと後呼び出す`Update`をエディット バッファーが進行中の新規または編集されたレコードを置き換えるストアドのレコードが更新されます。 この動作により、中止する方法、`AddNew`または`Edit`および新しい 1 つの開始: 進行中のレコードが障害であると判断した場合を呼び出すだけです`Edit`または`AddNew`もう一度です。

##  <a name="_core_deleting_a_record"></a> レコードを削除します。

レコード セットからレコードを削除するには、レコードをスクロールし、レコード セットの[削除](../../mfc/reference/crecordset-class.md#delete)メンバー関数。 異なり`AddNew`と`Edit`、`Delete`に一致する呼び出しは必要ありません`Update`します。

呼び出し元の前提条件として`Delete`レコード セットは更新可能である必要があります、レコードにする必要があります。 `CanUpdate`、 `IsBOF`、 `IsEOF`、および`IsDeleted`メンバー関数を使用して、これらの条件を確認できます。

呼び出すと`Delete`:

- ODBC ドライバーがサポートしている場合、 `::SQLSetPos` MFC ODBC API 関数では、関数を使用して、データ ソースのレコードを削除します。 使用して`::SQLSetPos`より SQL を使用した方が効率的です。

   \- または -

- 場合`::SQLSetPos`することはできません MFC は、次を使用します。

   1. エディット バッファーの現在のレコードはバックアップされませんとして`AddNew`と`Edit`します。

   1. `Delete` SQL を構築します**削除**レコードを削除するステートメント。

      エディット バッファーの現在のレコードとしてでは保存されません`AddNew`と`Edit`します。

   1. `Delete` 削除コミット: を実行、**削除**ステートメント。 レコードのデータ ソースが削除済みとマークされ、レコードが ODBC でのスナップショット。

   1. 削除されたレコードの値は引き続き、レコード セットのフィールド データ メンバーがフィールド データ メンバーには Null と、レコード セットのマーク`IsDeleted`メンバー関数は 0 以外の値を返します。

   > [!NOTE]
   > レコードを削除すると、新しいレコードのデータをエディット バッファーを補充する別のレコードをスクロールする必要があります。 呼び出すとエラーが`Delete`もう一度呼び出すまたは`Edit`します。

更新操作で使用される SQL ステートメントの詳細については、次を参照してください。 [SQL](../../data/odbc/sql.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 更新処理の詳細 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)