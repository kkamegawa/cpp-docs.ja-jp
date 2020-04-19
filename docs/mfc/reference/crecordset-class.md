---
title: CRecordset クラス
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626190"
---
# <a name="crecordset-class"></a>CRecordset クラス

データ ソースから選択された 1 組のレコードセットを表現します。

## <a name="syntax"></a>構文

```
class CRecordset : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名|説明|
|----------|-----------------|
|[CRecordset:: CRecordset](#crecordset)|`CRecordset` オブジェクトを構築します。 派生クラスは、このクラスを呼び出すコンストラクターを提供する必要があります。|

### <a name="public-methods"></a>パブリック メソッド

|名|説明|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|新しいレコードを追加するための準備をします。 `Update` を呼び出して、追加を完了します。|
|[CRecordset:: CanAppend](#canappend)|`AddNew` メンバー関数を使用してレコードセットに新しいレコードを追加できる場合は、0以外の値を返します。|
|[CRecordset:: CanBookmark](#canbookmark)|レコードセットがブックマークをサポートしている場合は0以外の値を返します。|
|[CRecordset:: Cancel](#cancel)|2番目のスレッドから非同期操作またはプロセスをキャンセルします。|
|[CRecordset:: CancelUpdate](#cancelupdate)|`AddNew` または `Edit` 操作により、保留中の更新をキャンセルします。|
|[CRecordset:: CanRestart](#canrestart)|レコードセットのクエリを再実行するために `Requery` を呼び出すことができる場合は、0以外の値を返します。|
|[CRecordset:: CanScroll](#canscroll)|レコードをスクロールできる場合は0以外の値を返します。|
|[CRecordset:: CanTransact](#cantransact)|データソースがトランザクションをサポートしている場合は0以外の値を返します。|
|[CRecordset:: CanUpdate](#canupdate)|レコードセットを更新できる場合は0以外の値を返します (レコードを追加、更新、または削除できます)。|
|[CRecordset:: CheckRowsetError](#checkrowseterror)|レコードのフェッチ中に生成されたエラーを処理するために呼び出されます。|
|[CRecordset:: Close](#close)|レコードセットと、それに関連付けられている ODBC HSTMT を閉じます。|
|[CRecordset::D e)](#delete)|レコードセットから現在のレコードを削除します。 削除後は、明示的に別のレコードにスクロールする必要があります。|
|[CRecordset::D oBulkFieldExchange](#dobulkfieldexchange)|データソースからレコードセットにデータの一括行を交換するために呼び出されます。 バルクレコードフィールドエクスチェンジ (Bulk RFX) を実装します。|
|[CRecordset::D oFieldExchange](#dofieldexchange)|レコードセットのフィールドデータメンバーとデータソースの対応するレコードとの間で、双方向のデータ交換を行うために呼び出されます。 レコードフィールドエクスチェンジ (RFX) を実装します。|
|[CRecordset:: Edit](#edit)|現在のレコードへの変更を準備します。 `Update` を呼び出して、編集を完了します。|
|[CRecordset:: FlushResultSet](#flushresultset)|定義済みのクエリを使用する場合、別の結果セットが取得されると、0以外の値を返します。|
|[CRecordset:: GetBookmark](#getbookmark)|レコードのブックマーク値をパラメーターオブジェクトに割り当てます。|
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|既定の接続文字列を取得するために呼び出されます。|
|[CRecordset:: GetDefaultSQL](#getdefaultsql)|実行する既定の SQL 文字列を取得するために呼び出されます。|
|[CRecordset:: GetFieldValue](#getfieldvalue)|レコードセット内のフィールドの値を返します。|
|[CRecordset:: GetODBCFieldCount](#getodbcfieldcount)|レコードセット内のフィールドの数を返します。|
|[CRecordset:: GetODBCFieldInfo](#getodbcfieldinfo)|レコードセット内のフィールドに関する特定の種類の情報を返します。|
|[CRecordset:: GetRecordCount](#getrecordcount)|レコードセット内のレコードの数を返します。|
|[CRecordset:: GetRowsetSize](#getrowsetsize)|1回のフェッチ中に取得するレコードの数を返します。|
|[CRecordset:: GetRowsFetched](#getrowsfetched)|フェッチ中に取得された実際の行数を返します。|
|[CRecordset:: GetRowStatus](#getrowstatus)|フェッチ後の行の状態を返します。|
|[CRecordset:: GetSQL](#getsql)|レコードセットのレコードを選択するために使用する SQL 文字列を取得します。|
|[CRecordset:: GetStatus](#getstatus)|レコードセットの状態を取得します。現在のレコードのインデックスと、レコードの最終カウントが取得されたかどうかを取得します。|
|[CRecordset:: GetTableName](#gettablename)|レコードセットの基になるテーブルの名前を取得します。|
|[CRecordset:: IsBOF](#isbof)|レコードセットが最初のレコードの前に配置されている場合は、0以外の値を返します。 現在のレコードがありません。|
|[CRecordset:: IsDeleted](#isdeleted)|レコードセットが削除されたレコードに配置されている場合は、0以外の値を返します。|
|[CRecordset:: IsEOF](#iseof)|レコードセットが最後のレコードの後に配置されている場合は0以外の値を返します。 現在のレコードがありません。|
|[CRecordset:: IsFieldDirty](#isfielddirty)|現在のレコード内の指定されたフィールドが変更されている場合は、0以外の値を返します。|
|[CRecordset:: IsFieldNull](#isfieldnull)|現在のレコード内の指定されたフィールドが null (値がない) の場合は、0以外の値を返します。|
|[CRecordset:: IsFieldNullable](#isfieldnullable)|現在のレコード内の指定されたフィールドを null に設定できる場合 (値がない場合) は0以外の値を返します。|
|[CRecordset:: IsOpen](#isopen)|`Open` が既に呼び出されている場合は0以外の値を返します。|
|[CRecordset:: Move](#move)|現在のレコードから指定された数のレコードに、いずれかの方向でレコードセットを配置します。|
|[CRecordset:: MoveFirst](#movefirst)|レコードセット内の最初のレコードに現在のレコードを配置します。 最初に `IsBOF` をテストします。|
|[CRecordset:: MoveLast](#movelast)|最後のレコードまたは最後の行セットの現在のレコードを配置します。 最初に `IsEOF` をテストします。|
|[CRecordset:: MoveNext](#movenext)|現在のレコードを次のレコードまたは次の行セットに配置します。 最初に `IsEOF` をテストします。|
|[CRecordset:: MovePrev](#moveprev)|前のレコードまたは前の行セットの現在のレコードを配置します。 最初に `IsBOF` をテストします。|
|[CRecordset:: OnSetOptions](#onsetoptions)|指定された ODBC ステートメントのオプション (選択時に使用される) を設定するために呼び出されます。|
|[CRecordset:: OnSetUpdateOptions](#onsetupdateoptions)|指定された ODBC ステートメントに対してオプション (update で使用) を設定するために呼び出されます。|
|[CRecordset:: Open](#open)|テーブルを取得するか、レコードセットが表すクエリを実行して、レコードセットを開きます。|
|[CRecordset:: RefreshRowset](#refreshrowset)|指定された行のデータと状態を更新します。|
|[CRecordset:: Requery](#requery)|レコードセットのクエリを再実行して、選択したレコードを更新します。|
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|指定されたレコード番号に対応するレコードにレコードセットを配置します。|
|[CRecordset:: SetBookmark](#setbookmark)|ブックマークで指定されたレコードにレコードセットを配置します。|
|[CRecordset:: SetFieldDirty](#setfielddirty)|現在のレコード内の指定されたフィールドを変更済みとしてマークします。|
|[CRecordset:: SetFieldNull](#setfieldnull)|現在のレコード内の指定されたフィールドの値を null に設定します (値はありません)。|
|[CRecordset:: Setロックモード](#setlockingmode)|ロックモードを "オプティミスティック" ロック (既定値) または "ペシミスティック" ロックに設定します。 更新のためにレコードをロックする方法を指定します。|
|[CRecordset:: SetParamNull](#setparamnull)|指定されたパラメーターを null に設定します (値はありません)。|
|[CRecordset:: SetRowsetCursorPosition](#setrowsetcursorposition)|行セット内の指定された行にカーソルを移動します。|
|[CRecordset:: SetRowsetSize](#setrowsetsize)|フェッチ中に取得するレコードの数を指定します。|
|[CRecordset:: Update](#update)|新しいデータまたは編集されたデータをデータソースに保存することにより、`AddNew` または `Edit` 操作を完了します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名|説明|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|レコードセットの ODBC ステートメントハンドルを格納します。 「`HSTMT`」と入力します。|
|[CRecordset:: m_nFields](#m_nfields)|レコードセットのフィールドデータメンバーの数を格納します。 「`UINT`」と入力します。|
|[CRecordset:: m_nParams](#m_nparams)|レコードセット内のパラメーターデータメンバーの数を格納します。 「`UINT`」と入力します。|
|[CRecordset:: m_pDatabase](#m_pdatabase)|レコードセットをデータソースに接続するために使用する `CDatabase` オブジェクトへのポインターを格納します。|
|[CRecordset:: m_strFilter](#m_strfilter)|構造化照会言語 (SQL) `WHERE` 句を指定する `CString` が含まれています。 特定の条件を満たすレコードのみを選択するためのフィルターとして使用されます。|
|[CRecordset:: m_strSort](#m_strsort)|SQL `ORDER BY` 句を指定する `CString` が含まれています。 レコードの並べ替え方法を制御するために使用します。|

## <a name="remarks"></a> 解説

"レコードセット" と呼ばれる `CRecordset` オブジェクトは、通常、ダイナセットとスナップショットの2つの形式で使用されます。 ダイナセットは、他のユーザーが行ったデータの更新と同期したままになります。 スナップショットは、データの静的なビューです。 各フォームは、レコードセットを開いたときに固定されたレコードのセットを表しますが、ダイナセット内のレコードにスクロールすると、他のユーザーまたはアプリケーション内の他のレコードセットによってレコードに加えられた変更が反映されます。

> [!NOTE]
>  Open Database Connectivity (ODBC) クラスではなく、データアクセスオブジェクト (DAO) クラスを使用している場合は、代わりにクラス[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)を使用します。 詳細については、記事「[概要: データベースプログラミング](../../data/data-access-programming-mfc-atl.md)」を参照してください。

いずれかの種類のレコードセットを操作するには、通常、`CRecordset`からアプリケーション固有のレコードセットクラスを派生します。 レコードセットデータソースからレコードを選択すると、次のことができます。

- レコードをスクロールします。

- レコードを更新し、ロックモードを指定します。

- レコードセットをフィルター処理して、データソースで使用できるレコードのうち、どれを選択するかを制限します。

- レコードセットを並べ替えます。

- レコードセットをパラメーター化して、実行時まで知られていない情報で選択をカスタマイズします。

クラスを使用するには、データベースを開き、レコードセットオブジェクトを構築して、コンストラクターに `CDatabase` オブジェクトへのポインターを渡します。 次に、レコードセットの `Open` メンバー関数を呼び出します。この関数では、オブジェクトがダイナセットまたはスナップショットのどちらであるかを指定できます。 `Open` を呼び出すと、データソースからデータが選択されます。 レコードセットオブジェクトを開いた後、そのメンバー関数とデータメンバーを使用して、レコードをスクロールして操作します。 使用できる操作は、オブジェクトがダイナセットまたはスナップショットのどちらであるか、更新可能か読み取り専用か (これは、Open Database Connectivity (ODBC) データソースの機能によって異なります)、および一括行フェッチを実装したかどうかによって異なります。 `Open` の呼び出し以降に変更または追加された可能性があるレコードを更新するには、オブジェクトの `Requery` メンバー関数を呼び出します。 オブジェクトの `Close` メンバー関数を呼び出し、終了時にオブジェクトを破棄します。

派生 `CRecordset` クラスでは、レコードフィールドの読み取りと更新をサポートするために、レコードフィールドエクスチェンジ (RFX) フィールドまたはバルクレコードフィールドエクスチェンジ (Bulk RFX) が使用されます。

レコードセットとレコードフィールドエクスチェンジの詳細については、「[データベースプログラミング](../../data/data-access-programming-mfc-atl.md)、[レコードセット (odbc)](../../data/odbc/recordset-odbc.md)」、「レコード[セット: バルクデータフェッチ (odbc)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」、および「[レコードフィールドエクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)」を参照してください。 ダイナセットとスナップショットについては、「[ダイナセット](../../data/odbc/dynaset.md)と[スナップショット](../../data/odbc/snapshot.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>［要件］

**ヘッダー:** afxdb.h

##  <a name="addnew"></a>CRecordset:: AddNew

テーブルに新しいレコードを追加する準備をします。

```
virtual void AddNew();
```

### <a name="remarks"></a>Remarks

新しく追加されたレコードを表示するには、 [Requery](#requery)メンバー関数を呼び出す必要があります。 レコードのフィールドは、最初は Null になります。 (データベース用語では、Null は "値がありません" を意味し、でC++は null と同じではありません)。操作を完了するには、 [Update](#update)メンバー関数を呼び出す必要があります。 `Update` によって、データソースへの変更が保存されます。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`AddNew`を呼び出すことはできません。 これにより、アサーションは失敗します。 クラス `CRecordset` は、データの一括行を更新するためのメカニズムを提供していませんが、ODBC API 関数 `SQLSetPos`を使用して独自の関数を記述することができます。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

`AddNew` レコードセットのフィールドデータメンバーを使用して、新しい空のレコードを準備します。 `AddNew`を呼び出した後、レコードセットのフィールドデータメンバーに必要な値を設定します。 (この目的で[Edit](#edit)メンバー関数を呼び出す必要はありません。 `Edit` は、既存のレコードに対してのみ使用してください)。その後 `Update`を呼び出すと、フィールドのデータメンバーの値が変更され、データソースに保存されます。

> [!CAUTION]
>  `Update`を呼び出す前に新しいレコードにスクロールすると、新しいレコードは失われ、警告は表示されません。

データソースでトランザクションがサポートされている場合は、トランザクションの一部 `AddNew` 呼び出しを行うことができます。 トランザクションの詳細については、「クラス[CDatabase](../../mfc/reference/cdatabase-class.md)」を参照してください。 `AddNew`を呼び出す前に、 [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)を呼び出す必要があることに注意してください。

> [!NOTE]
>  ダイナセットの場合、最後のレコードとしてレコードセットに新しいレコードが追加されます。 追加されたレコードはスナップショットには追加されません。レコードセットを更新するには、`Requery` を呼び出す必要があります。

`Open` メンバー関数が呼び出されていないレコードセットに対して `AddNew` を呼び出すことはできません。 に追加できないレコードセットに対して `AddNew` を呼び出すと、`CDBException` がスローされます。 [CanAppend](#canappend)を呼び出すことで、レコードセットが更新可能かどうかを判断できます。

詳細については、「[レコードセット: レコード更新のしくみ (odbc)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)」、「レコード[セット: レコードの追加、更新、削除](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)(odbc)」、および「[トランザクション (odbc](../../data/odbc/transaction-odbc.md))」を参照してください。

### <a name="example"></a>例

「[トランザクション: レコードセットでのトランザクションの実行 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」を参照してください。

##  <a name="canappend"></a>CRecordset:: CanAppend

以前に開いたレコードセットで、新しいレコードを追加できるかどうかを判断します。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>戻り値

レコードセットで新しいレコードの追加が許可されている場合は0以外の。それ以外の場合は0です。 レコードセットを読み取り専用として開いた場合、`CanAppend` は0を返します。

##  <a name="canbookmark"></a>CRecordset:: CanBookmark

レコードセットでブックマークを使用してレコードをマークできるかどうかを決定します。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>戻り値

レコードセットがブックマークをサポートしている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数は、 [Open](#open)メンバー関数の*dwOptions*パラメーターの `CRecordset::useBookmarks` オプションに依存しません。 指定した ODBC ドライバーおよびカーソルの種類でブックマークがサポートされているかどうかを示す `CanBookmark` です。 サポートされている場合は、ブックマークを使用できるようにするかどうかを `CRecordset::useBookmarks` に示します。

> [!NOTE]
>  ブックマークは、順方向専用のレコードセットではサポートされていません。

ブックマークとレコードセットナビゲーションの詳細については、「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 」および「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md)」を参照してください。

##  <a name="cancel"></a>CRecordset:: Cancel

データソースが処理中の非同期操作または2番目のスレッドからのプロセスのいずれかをキャンセルすることを要求します。

```
void Cancel();
```

### <a name="remarks"></a>Remarks

MFC ODBC クラスで非同期処理が使用されなくなったことに注意してください。非同期操作を実行するには、ODBC API 関数 `SQLSetConnectOption`を直接呼び出す必要があります。 詳細については、『 *ODBC SDK プログラマーズガイド』* の「非同期関数の実行」を参照してください。

##  <a name="cancelupdate"></a>CRecordset:: CancelUpdate

[Update](#update)が呼び出される前に、[編集](#edit)または[AddNew](#addnew)操作によって発生した保留中の更新をキャンセルします。

```
void CancelUpdate();
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  このメンバー関数は、バルク行フェッチを使用しているレコードセットには適用されません。このようなレコードセットは、`Edit`、`AddNew`、または `Update`を呼び出すことができないためです。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

自動ダーティフィールドチェックが有効になっている場合、`CancelUpdate` は `Edit` または `AddNew` が呼び出される前のメンバー変数をその値に復元します。それ以外の場合、値の変更はすべて保持されます。 既定では、レコードセットが開かれると、自動フィールドチェックが有効になります。 無効にするには、 [Open](#open)メンバー関数の*dwOptions*パラメーターに `CRecordset::noDirtyFieldCheck` を指定する必要があります。

データの更新の詳細については、「レコード[セット: レコードの追加、更新、および削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)」を参照してください。

##  <a name="canrestart"></a>CRecordset:: CanRestart

`Requery` メンバー関数を呼び出すことによって、レコードセットでクエリを再起動できるかどうかを決定します (レコードを更新するため)。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>戻り値

Requery が許可される場合は0以外の。それ以外の場合は0です。

##  <a name="canscroll"></a>CRecordset:: CanScroll

レコードセットでスクロールが許可されているかどうかを判断します。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>戻り値

レコードセットでスクロールが許可されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

スクロールの詳細については、「[レコードセット: スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)」を参照してください。

##  <a name="cantransact"></a>CRecordset:: CanTransact

レコードセットでトランザクションが許可されるかどうかを判断します。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>戻り値

レコードセットでトランザクションが許可されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

詳細については、「[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)」を参照してください。

##  <a name="canupdate"></a>CRecordset:: CanUpdate

レコードセットを更新できるかどうかを決定します。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>戻り値

レコードセットを更新できる場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

基になるデータソースが読み取り専用の場合、またはレコードセットを開いたときに*dwOptions*パラメーターに `CRecordset::readOnly` を指定した場合は、レコードセットが読み取り専用になることがあります。

##  <a name="checkrowseterror"></a>CRecordset:: CheckRowsetError

レコードのフェッチ中に生成されたエラーを処理するために呼び出されます。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>パラメーター

*nRetCode*<br/>
ODBC API 関数のリターンコード。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

この仮想メンバー関数は、レコードがフェッチされるときに発生するエラーを処理します。これは、バルク行フェッチ時に役立ちます。 `CheckRowsetError` をオーバーライドして、独自のエラー処理を実装することもできます。

`CheckRowsetError` は、`Open`、`Requery`、`Move` 操作など、カーソルナビゲーション操作で自動的に呼び出されます。 これには、ODBC API 関数 `SQLExtendedFetch`の戻り値が渡されます。 次の表に、 *nRetCode*パラメーターの有効な値を示します。

|nRetCode|説明|
|--------------|-----------------|
|SQL_SUCCESS|関数は正常に完了しました。追加情報はありません。|
|SQL_SUCCESS_WITH_INFO|関数は正常に完了しました。致命的でないエラーが発生した可能性があります。 `SQLError`を呼び出すことによって、追加情報を取得できます。|
|SQL_NO_DATA_FOUND|結果セットのすべての行がフェッチされました。|
|SQL_ERROR|関数が失敗しました。 `SQLError`を呼び出すことによって、追加情報を取得できます。|
|SQL_INVALID_HANDLE|無効な環境ハンドル、接続ハンドル、またはステートメントハンドルが原因で関数が失敗しました。 これは、プログラミングエラーを示します。 `SQLError`から追加情報を入手することはできません。|
|SQL_STILL_EXECUTING|非同期的に開始された関数はまだ実行されています。 既定では、MFC はこの値を `CheckRowsetError`に渡さないことに注意してください。MFC では、SQL_STILL_EXECUTING が返されなくなるまで、`SQLExtendedFetch` の呼び出しを続けます。|

`SQLError`の詳細については、Windows SDK を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="close"></a>CRecordset:: Close

レコードセットを閉じます。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

レコードセットに割り当てられたフレームワークの ODBC HSTMT とすべてのメモリの割り当てが解除されます。 通常、`Close`を呼び出した後、 C++レコードセットオブジェクトが**new**で割り当てられている場合は、レコードセットオブジェクトを削除します。

`Close`を呼び出した後、`Open` をもう一度呼び出すことができます。 これにより、レコードセットオブジェクトを再利用できます。 別の方法として、`Requery`を呼び出すこともできます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset:: CRecordset

`CRecordset` オブジェクトを構築します。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>パラメーター

*pDatabase*<br/>
`CDatabase` オブジェクトへのポインターまたは NULL 値を格納します。 NULL ではなく、`CDatabase` オブジェクトの `Open` メンバー関数が呼び出されていない場合は、それをデータソースに接続するために、レコードセットは独自の `Open` 呼び出しの間に、その関数を開こうとします。 NULL を渡した場合、`CDatabase` オブジェクトが作成され、ClassWizard でレコードセットクラスを派生させるときに指定したデータソース情報を使用して接続されます。

### <a name="remarks"></a>Remarks

`CRecordset` を直接使用することも、`CRecordset`からアプリケーション固有のクラスを派生させることもできます。 ClassWizard を使用して、レコードセットクラスを派生させることができます。

> [!NOTE]
>  派生クラスは、独自のコンストラクターを提供*する必要があり*ます。 派生クラスのコンストラクターで `CRecordset::CRecordset`コンストラクターを呼び出し、適切なパラメーターを渡します。

レコードセットコンストラクターに NULL を渡して、`CDatabase` オブジェクトを自動的に構築および接続するようにします。 これは、レコードセットを構築する前に、`CDatabase` オブジェクトを構築して接続する必要のない短縮形です。

### <a name="example"></a>例

詳細については、「[レコードセット: テーブルのクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)」を参照してください。

##  <a name="delete"></a>CRecordset::D e)

現在のレコードを削除します。

```
virtual void Delete();
```

### <a name="remarks"></a>Remarks

削除が正常に完了すると、レコードセットのフィールドデータメンバーが Null 値に設定され、削除されたレコードから移動するために、`Move` 関数のいずれかを明示的に呼び出す必要があります。 削除されたレコードから移動すると、それに戻ることはできません。 データソースでトランザクションがサポートされている場合は、トランザクションの一部 `Delete` 呼び出しを行うことができます。 詳細については、「[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)」を参照してください。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`Delete`を呼び出すことはできません。 これにより、アサーションは失敗します。 クラス `CRecordset` は、データの一括行を更新するためのメカニズムを提供していませんが、ODBC API 関数 `SQLSetPos`を使用して独自の関数を記述することができます。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

> [!CAUTION]
>  レコードセットは更新可能である必要があります。 `Delete`を呼び出すときに、レコードセットの現在のレコードが有効である必要があります。それ以外の場合は、エラーが発生します。 たとえば、レコードを削除しても、`Delete` を再度呼び出す前に新しいレコードにスクロールしない場合、`Delete` は[CDBException](../../mfc/reference/cdbexception-class.md)をスローします。

[AddNew](#addnew)と[Edit](#edit)とは異なり、`Delete` を呼び出すと、その後に[Update](#update)を呼び出すことはできません。 `Delete` の呼び出しが失敗した場合、フィールドのデータメンバーは変更されません。

### <a name="example"></a>例

次の例では、関数のフレームに作成されたレコードセットを示します。 この例では、`m_dbCust`が存在することを前提としています。 `CDatabase` 型のメンバー変数は、既にデータソースに接続されています。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset::D oBulkFieldExchange

データソースからレコードセットにデータの一括行を交換するために呼び出されます。 バルクレコードフィールドエクスチェンジ (Bulk RFX) を実装します。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>パラメーター

*.Cer*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)オブジェクトへのポインター。 フレームワークでは、フィールド交換操作のコンテキストを指定するために、このオブジェクトが既に設定されています。

### <a name="remarks"></a>Remarks

バルク行フェッチが実装されている場合、フレームワークはこのメンバー関数を呼び出して、データソースからレコードセットオブジェクトにデータを自動的に転送します。 また `DoBulkFieldExchange` は、パラメーターデータメンバー (存在する場合) を、レコードセットの選択に使用する SQL ステートメント文字列のパラメータープレースホルダーにバインドします。

バルク行フェッチが実装されていない場合、フレームワークは[DoFieldExchange](#dofieldexchange)を呼び出します。 バルク行フェッチを実装するには、 [Open](#open)メンバー関数で*dwOptions*パラメーターの `CRecordset::useMultiRowFetch` オプションを指定する必要があります。

> [!NOTE]
> `DoBulkFieldExchange` は、`CRecordset`から派生したクラスを使用している場合にのみ使用できます。 `CRecordset`から直接レコードセットオブジェクトを作成した場合は、データを取得するために[GetFieldValue](#getfieldvalue)メンバー関数を呼び出す必要があります。

バルクレコードフィールドエクスチェンジ (Bulk RFX) は、レコードフィールドエクスチェンジ (RFX) に似ています。 データは、データソースからレコードセットオブジェクトに自動的に転送されます。 ただし、`AddNew`、`Edit`、`Delete`、または `Update` を呼び出して、変更をデータソースに転送することはできません。 現在、クラス `CRecordset` には、データの一括行を更新するためのメカニズムが用意されていません。ただし、ODBC API 関数 `SQLSetPos`を使用して独自の関数を記述することもできます。

ClassWizard では、一括レコードフィールドの交換がサポートされていないことに注意してください。そのため、Bulk RFX 関数の呼び出しを作成することによって、`DoBulkFieldExchange` を手動でオーバーライドする必要があります。 これらの関数の詳細については、「[レコードフィールドエクスチェンジ関数](../../mfc/reference/record-field-exchange-functions.md)」を参照してください。

バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。 関連情報については、「[レコードフィールドエクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)」を参照してください。

##  <a name="dofieldexchange"></a>CRecordset::D oFieldExchange

レコードセットのフィールドデータメンバーとデータソースの対応するレコードとの間で、双方向のデータ交換を行うために呼び出されます。 レコードフィールドエクスチェンジ (RFX) を実装します。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>パラメーター

*.Cer*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)オブジェクトへのポインター。 フレームワークでは、フィールド交換操作のコンテキストを指定するために、このオブジェクトが既に設定されています。

### <a name="remarks"></a>Remarks

バルク行フェッチが実装されていない場合、フレームワークはこのメンバー関数を呼び出して、レコードセットオブジェクトのフィールドデータメンバーと、データソースの現在のレコードの対応する列との間でデータを自動的に交換します。 また `DoFieldExchange` は、パラメーターデータメンバー (存在する場合) を、レコードセットの選択に使用する SQL ステートメント文字列のパラメータープレースホルダーにバインドします。

バルク行フェッチが実装されている場合、フレームワークは[DoBulkFieldExchange](#dobulkfieldexchange)を呼び出します。 バルク行フェッチを実装するには、 [Open](#open)メンバー関数で*dwOptions*パラメーターの `CRecordset::useMultiRowFetch` オプションを指定する必要があります。

> [!NOTE]
> `DoFieldExchange` は、`CRecordset`から派生したクラスを使用している場合にのみ使用できます。 `CRecordset`から直接レコードセットオブジェクトを作成した場合は、データを取得するために[GetFieldValue](#getfieldvalue)メンバー関数を呼び出す必要があります。

レコードフィールドエクスチェンジ (RFX) と呼ばれるフィールドデータの交換は、レコードセットオブジェクトのフィールドデータメンバーからデータソース上のレコードのフィールドへの変換と、データソースのレコードからレコードセットオブジェクトへの双方向で機能します。

派生レコードセットクラスの `DoFieldExchange` を実装するために通常必要な操作は、ClassWizard でクラスを作成し、フィールドデータメンバーの名前とデータ型を指定することです。 パラメーターデータメンバーを指定したり、動的にバインドする列を処理したりするために、ClassWizard が書き込むコードを追加することもできます。 詳細については、「[レコードセット: 動的にデータ列をバインドする (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)」を参照してください。

ClassWizard で派生したレコードセットクラスを宣言すると、ウィザードによって `DoFieldExchange` のオーバーライドが書き込まれます。これは、次の例のようになります。

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

RFX 関数の詳細については、「[レコードフィールドエクスチェンジ関数](../../mfc/reference/record-field-exchange-functions.md)」を参照してください。

`DoFieldExchange`に関するその他の例と詳細については、「RFX のしくみ」の「[レコードフィールドエクスチェンジ: RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)」を参照してください。 RFX に関する一般的な情報については、「[レコードフィールドエクスチェンジ](../../data/odbc/record-field-exchange-rfx.md)」を参照してください。

##  <a name="edit"></a>CRecordset:: Edit

現在のレコードを変更できるようにします。

```
virtual void Edit();
```

### <a name="remarks"></a>Remarks

`Edit`を呼び出した後、フィールドのデータメンバーを変更するには、その値を直接リセットします。 この操作は、後で[Update](#update)メンバー関数を呼び出して、変更内容をデータソースに保存すると完了します。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`Edit`を呼び出すことはできません。 これにより、アサーションは失敗します。 クラス `CRecordset` は、データの一括行を更新するためのメカニズムを提供していませんが、ODBC API 関数 `SQLSetPos`を使用して独自の関数を記述することができます。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

`Edit` では、レコードセットのデータメンバーの値が保存されます。 `Edit`を呼び出して変更を加え、`Edit` を再度呼び出すと、レコードの値は最初の `Edit` 呼び出しの前の値に復元されます。

場合によっては、Null (データを含まない) によって列を更新することが必要になることがあります。 これを行うには、パラメーターを TRUE に設定して[SetFieldNull](#setfieldnull)を呼び出し、フィールドを Null に設定します。これにより、列も更新されます。 値が変更されていない場合でも、データソースにフィールドを書き出す場合は、パラメーターを TRUE に設定して[SetFieldDirty](#setfielddirty)を呼び出します。 これは、フィールドの値が Null の場合でも機能します。

データソースでトランザクションがサポートされている場合は、トランザクションの一部 `Edit` 呼び出しを行うことができます。 `Edit` を呼び出す前と、レコードセットを開いた後に、 [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)を呼び出す必要があることに注意してください。 また、 [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)の呼び出しは、`Edit` 操作を完了するために `Update` を呼び出すための代替ではないことにも注意してください。 トランザクションの詳細については、「クラス[CDatabase](../../mfc/reference/cdatabase-class.md)」を参照してください。

現在のロックモードによっては、更新されるレコードが `Edit` によってロックされる可能性があります。これは、`Update` を呼び出すか別のレコードまでスクロールするか、`Edit` の呼び出し中にのみロックされることがあります。 [Setロッキングモード](#setlockingmode)でロックモードを変更できます。

`Update`を呼び出す前に新しいレコードにスクロールすると、現在のレコードの前の値が復元されます。 更新できないレコードセットに対して `Edit` を呼び出した場合、または現在のレコードが存在しない場合は、`CDBException` がスローされます。

詳細については、記事「[トランザクション (odbc)](../../data/odbc/transaction-odbc.md) 」および「[レコードセット: レコードのロック (odbc)](../../data/odbc/recordset-locking-records-odbc.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset:: FlushResultSet

複数の結果セットがある場合は、定義済みクエリ (ストアドプロシージャ) の次の結果セットを取得します。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>戻り値

取得する結果セットの数が多い場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

現在の結果セットでカーソルを完全に終了した場合にのみ、`FlushResultSet` を呼び出す必要があります。 `FlushResultSet`を呼び出して次の結果セットを取得すると、その結果セットでカーソルが有効にならないことに注意してください。`FlushResultSet`を呼び出した後、 [MoveNext](#movenext)メンバー関数を呼び出す必要があります。

定義済みのクエリで出力パラメーターまたは入出力パラメーターを使用する場合は、これらのパラメーター値を取得するために、`FALSE` (値 0) を返すまで `FlushResultSet` を呼び出す必要があります。

`FlushResultSet` は、ODBC API 関数 `SQLMoreResults`を呼び出します。 `SQLMoreResults` が SQL_ERROR または SQL_INVALID_HANDLE を返した場合、`FlushResultSet` は例外をスローします。 `SQLMoreResults`の詳細については、Windows SDK を参照してください。

`FlushResultSet`を呼び出す必要がある場合は、ストアドプロシージャにバインドされたフィールドが必要です。

### <a name="example"></a>例

次のコードでは、`COutParamRecordset` が、入力パラメーターと出力パラメーターを使用し、複数の結果セットを持つ定義済みのクエリに基づいて、`CRecordset`派生オブジェクトであることを前提としています。 [DoFieldExchange](#dofieldexchange)オーバーライドの構造を確認します。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset:: GetBookmark

現在のレコードのブックマーク値を取得します。

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>パラメーター

*varBookmark*<br/>
現在のレコードのブックマークを表す[CDBVariant](../../mfc/reference/cdbvariant-class.md)オブジェクトへの参照。

### <a name="remarks"></a>Remarks

レコードセットでブックマークがサポートされているかどうかを判断するには、 [Canbookmark](#canbookmark)を呼び出します。 サポートされている場合にブックマークを使用できるようにするには、 [Open](#open)メンバー関数の*dwOptions*パラメーターで `CRecordset::useBookmarks` オプションを設定する必要があります。

> [!NOTE]
>  ブックマークがサポートされていないか使用できない場合は、`GetBookmark` を呼び出すと、例外がスローされます。 ブックマークは、順方向専用のレコードセットではサポートされていません。

`GetBookmark` は、現在のレコードのブックマークの値を `CDBVariant` オブジェクトに割り当てます。 別のレコードに移動した後、いつでもそのレコードに戻るには、対応する `CDBVariant` オブジェクトを使用して[SetBookmark](#setbookmark)を呼び出します。

> [!NOTE]
>  特定のレコードセット操作の後、ブックマークが無効になることがあります。 たとえば、`GetBookmark` の後に `Requery`を呼び出した場合、`SetBookmark`を含むレコードに戻ることができなくなる可能性があります。 `SetBookmark`を安全に呼び出すことができるかどうかを確認するには、 [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)を呼び出します。

ブックマークとレコードセットナビゲーションの詳細については、「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 」および「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md)」を参照してください。

##  <a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect

既定の接続文字列を取得するために呼び出されます。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>戻り値

既定の接続文字列を含む `CString` です。

### <a name="remarks"></a>Remarks

フレームワークは、このメンバー関数を呼び出して、レコードセットの基になるデータソースの既定の接続文字列を取得します。 ClassWizard では、テーブルと列に関する情報を取得するために、ClassWizard で使用するのと同じデータソースを識別することで、この関数を実装しています。 アプリケーションの開発中にこの既定の接続を利用すると便利な場合があります。 ただし、既定の接続は、アプリケーションのユーザーには適していない場合があります。 その場合は、ClassWizard のバージョンを破棄して、この関数を再実装する必要があります。 接続文字列の詳細については、「[データソース (ODBC)](../../data/odbc/data-source-odbc.md)」を参照してください。

##  <a name="getdefaultsql"></a>CRecordset:: GetDefaultSQL

実行する既定の SQL 文字列を取得するために呼び出されます。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>戻り値

既定の SQL ステートメントを含む `CString` です。

### <a name="remarks"></a>Remarks

フレームワークは、このメンバー関数を呼び出して、レコードセットの基になる既定の SQL ステートメントを取得します。 テーブル名または SQL **SELECT**ステートメントを指定できます。

ClassWizard でレコードセットクラスを宣言することで、既定の SQL ステートメントを間接的に定義すると、ClassWizard がこのタスクを実行します。

使用する SQL ステートメント文字列が必要な場合は、`GetSQL`を呼び出します。これにより、レコードセットのレコードを開いたときに選択するために使用される SQL ステートメントが返されます。 クラスの `GetDefaultSQL`のオーバーライドで、既定の SQL 文字列を編集できます。 たとえば、 **call**ステートメントを使用して、事前定義されたクエリの呼び出しを指定できます。 ただし、`GetDefaultSQL`を編集する場合は、データソース内の列の数と一致するように `m_nFields` を変更する必要もあります。

詳細については、「[レコードセット: テーブルのクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)」を参照してください。

> [!CAUTION]
>  フレームワークがテーブル名を識別できなかった場合、複数のテーブル名が指定された場合、または**CALL**ステートメントを解釈できなかった場合、テーブル名は空になります。 **Call**ステートメントを使用する場合は、中かっこと**call**キーワードの間に空白を挿入しないでください。また、 **select**ステートメントの中かっこの前、または**select**キーワードの前に空白を挿入することもできません。

##  <a name="getfieldvalue"></a>CRecordset:: GetFieldValue

現在のレコード内のフィールドデータを取得します。

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
フィールドの名前。

*varValu*e フィールドの値を格納する[CDBVariant](../../mfc/reference/cdbvariant-class.md)オブジェクトへの参照。

*nFieldType*<br/>
フィールドの ODBC C データ型。 既定値の DEFAULT_FIELD_TYPE を使用すると、次の表に基づいて、`GetFieldValue` によって SQL データ型の C データ型が決定されます。 それ以外の場合は、データ型を直接指定するか、互換性のあるデータ型を選択することができます。たとえば、任意のデータ型を SQL_C_CHAR に格納できます。

|C データ型|SQL データ型|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

ODBC データ型の詳細については、Windows SDK の付録 D の「SQL データ型」および「C データ型」を参照してください。

*nIndex*<br/>
フィールドの0から始まるインデックス。

*strValue*<br/>
フィールドのデータ型に関係なく、テキストに変換されたフィールドの値を格納する[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトへの参照。

### <a name="remarks"></a>Remarks

名前またはインデックスを使用して、フィールドを検索できます。 フィールド値は、`CDBVariant` オブジェクトまたは `CString` オブジェクトのいずれかに格納できます。

バルク行フェッチを実装している場合、現在のレコードは常に行セットの最初のレコードに配置されます。 特定の行セット内のレコードに対して `GetFieldValue` を使用するには、まず、 [SetRowsetCursorPosition](#setrowsetcursorposition)メンバー関数を呼び出して、その行セット内の目的の行にカーソルを移動する必要があります。 その後、その行の `GetFieldValue` を呼び出します。 バルク行フェッチを実装するには、 [Open](#open)メンバー関数で*dwOptions*パラメーターの `CRecordset::useMultiRowFetch` オプションを指定する必要があります。

`GetFieldValue` を使用すると、デザイン時に静的にバインドするのではなく、実行時にフィールドを動的にフェッチできます。 たとえば、`CRecordset`から直接レコードセットオブジェクトを宣言した場合は、`GetFieldValue` を使用してフィールドデータを取得する必要があります。レコードフィールドエクスチェンジ (RFX)、またはバルクレコードフィールドエクスチェンジ (Bulk RFX) は実装されていません。

> [!NOTE]
>  `CRecordset`から派生せずにレコードセットオブジェクトを宣言する場合は、ODBC カーソルライブラリを読み込まないでください。 カーソルライブラリでは、レコードセットに少なくとも1つのバインドされた列が必要です。ただし、`CRecordset` を直接使用する場合は、どの列もバインドされません。 メンバー関数[cdatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex)および[CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open)は、カーソルライブラリが読み込まれるかどうかを制御します。

`GetFieldValue` は、ODBC API 関数 `SQLGetData`を呼び出します。 ドライバーがフィールド値の実際の長さの SQL_NO_TOTAL 値を出力した場合、`GetFieldValue` は例外をスローします。 `SQLGetData`の詳細については、Windows SDK を参照してください。

### <a name="example"></a>例

次のサンプルコードは、`CRecordset`から直接宣言されたレコードセットオブジェクトの `GetFieldValue` の呼び出しを示しています。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  DAO クラス `CDaoRecordset`とは異なり、`CRecordset` には `SetFieldValue` のメンバー関数がありません。 オブジェクトを `CRecordset`から直接作成した場合は、事実上読み取り専用になります。

バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="getodbcfieldcount"></a>CRecordset:: GetODBCFieldCount

レコードセットオブジェクトのフィールドの合計数を取得します。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>戻り値

レコードセット内のフィールドの数。

### <a name="remarks"></a>Remarks

レコードセットの作成の詳細については、「[レコードセット: レコードセットの作成と終了 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)」を参照してください。

##  <a name="getodbcfieldinfo"></a>CRecordset:: GetODBCFieldInfo

レコードセット内のフィールドに関する情報を取得します。

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
フィールドの名前。

*fieldinfo*<br/>
`CODBCFieldInfo` 構造体への参照。

*nIndex*<br/>
フィールドの0から始まるインデックス。

### <a name="remarks"></a>Remarks

関数の1つのバージョンでは、名前でフィールドを検索できます。 もう1つのバージョンでは、インデックスを使用してフィールドを検索できます。

返される情報の説明については、 [Codbcfieldinfo](../../mfc/reference/codbcfieldinfo-structure.md)構造体を参照してください。

レコードセットの作成の詳細については、「[レコードセット: レコードセットの作成と終了 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)」を参照してください。

##  <a name="getrecordcount"></a>CRecordset:: GetRecordCount

レコードセットのサイズを決定します。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>戻り値

レコードセット内のレコードの数。レコードセットにレコードが含まれていない場合は0。レコード数を特定できない場合は-1。

### <a name="remarks"></a>Remarks

> [!CAUTION]
>  レコード数は、ユーザーがレコードを移動したときに表示されている最も大きい番号のレコードである "high watermark" として維持されます。 レコードの合計数は、ユーザーが最後のレコードを超えた後にのみ認識されます。 パフォーマンス上の理由から、`MoveLast`を呼び出すと、カウントは更新されません。 レコードを自分でカウントするには、`IsEOF` が0以外の値を返すまで `MoveNext` を繰り返し呼び出します。 `CRecordset:AddNew` と `Update` を使用してレコードを追加すると、カウントが増加します。`CRecordset::Delete` を使用してレコードを削除すると、カウントが減少します。

##  <a name="getrowsetsize"></a>CRecordset:: GetRowsetSize

特定のフェッチ中に取得する行数の現在の設定を取得します。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>戻り値

特定のフェッチ中に取得する行の数。

### <a name="remarks"></a>Remarks

バルク行フェッチを使用している場合、レコードセットを開いたときの既定の行セットサイズは25です。それ以外の場合は1になります。

バルク行フェッチを実装するには、 [Open](#open)メンバー関数の*dwOptions*パラメーターで `CRecordset::useMultiRowFetch` オプションを指定する必要があります。 行セットサイズの設定を変更するには、 [SetRowsetSize](#setrowsetsize)を呼び出します。

バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="getrowsfetched"></a>CRecordset:: GetRowsFetched

フェッチ後に実際に取得されたレコードの数を決定します。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>戻り値

特定のフェッチの後にデータソースから取得された行の数。

### <a name="remarks"></a>Remarks

これは、バルク行フェッチを実装している場合に便利です。 行セットのサイズは通常、フェッチから取得する行の数を示します。ただし、レコードセット内の行の合計数は、行セットで取得される行の数にも影響します。 たとえば、レコードセットの行セットサイズが4に設定されたレコードが10個ある場合、`MoveNext` を呼び出すことによってレコードセットをループ処理すると、最終的な行セットには2つのレコードしか含まれません。

バルク行フェッチを実装するには、 [Open](#open)メンバー関数の*dwOptions*パラメーターで `CRecordset::useMultiRowFetch` オプションを指定する必要があります。 行セットのサイズを指定するには、 [SetRowsetSize](#setrowsetsize)を呼び出します。

バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset:: GetRowStatus

現在の行セットの行の状態を取得します。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>パラメーター

*wRow*<br/>
現在の行セット内の行の1から始まる位置。 この値の範囲は、1から行セットのサイズまでです。

### <a name="return-value"></a>戻り値

行の状態の値です。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

`GetRowStatus` は、データソースから最後に取得された行の状態を変更したか、 *Wrow*に対応する行がフェッチされなかったかを示す値を返します。 次の表は、可能性のある戻り値の一覧です。

|状態の値|説明|
|------------------|-----------------|
|SQL_ROW_SUCCESS|行は変更されません。|
|SQL_ROW_UPDATED|行が更新されました。|
|SQL_ROW_DELETED|行が削除されました。|
|SQL_ROW_ADDED|行が追加されました。|
|SQL_ROW_ERROR|エラーが発生したため、行が unretrievable されています。|
|SQL_ROW_NOROW|*Wrow*に対応する行がありません。|

詳細については、Windows SDK の ODBC API 関数 `SQLExtendedFetch` を参照してください。

##  <a name="getstatus"></a>CRecordset:: GetStatus

レコードセット内の現在のレコードのインデックスと、最後のレコードが表示されたかどうかを確認します。

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>パラメーター

*rStatus*<br/>
`CRecordsetStatus` オブジェクトへの参照。 詳細については、次の「解説」を参照してください。

### <a name="remarks"></a>Remarks

`CRecordset` インデックスの追跡を試みますが、状況によってはこれが不可能な場合があります。 説明については、「 [GetRecordCount](#getrecordcount) 」を参照してください。

`CRecordsetStatus` 構造体には、次の形式があります。

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

`CRecordsetStatus` の2つのメンバーの意味は次のとおりです。

- `m_lCurrentRecord` には、レコードセット内の現在のレコードの0から始まるインデックスが含まれます (既知の場合)。 インデックスを特定できない場合、このメンバーには AFX_CURRENT_RECORD_UNDEFINED (-2) が含まれます。 `IsBOF` が TRUE (空のレコードセットであるか、最初のレコードの前にスクロールしようとする) の場合、`m_lCurrentRecord` は AFX_CURRENT_RECORD_BOF (-1) に設定されます。 最初のレコードの場合は、0、2番目のレコード1などに設定されます。

- レコードセット内のレコードの合計数が決定された場合は、0以外の値を `m_bRecordCountFinal` ます。 通常、これを行うには、レコードセットの先頭から開始し、`IsEOF` が0以外の値を返すまで `MoveNext` を呼び出す必要があります。 このメンバーが0の場合、`GetRecordCount`によって返されるレコード数 (-1 ではない場合) は、レコードの "high watermark" カウントにすぎません。

##  <a name="getsql"></a>CRecordset:: GetSQL

レコードセットのレコードを開いたときにそのレコードを選択するために使用された SQL ステートメントを取得するには、このメンバー関数を呼び出します。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>戻り値

SQL ステートメントを含む `CString` への**const**参照。

### <a name="remarks"></a>Remarks

通常、これは SQL **SELECT**ステートメントです。 `GetSQL` によって返される文字列は読み取り専用です。

`GetSQL` によって返される文字列は、通常、`Open` メンバー関数の*lpszSQL*パラメーターのレコードセットに渡された文字列とは異なります。 これは、`Open`に渡された内容に基づいて完全な SQL ステートメントが作成されるため、ClassWizard で指定したもの、`m_strFilter` と `m_strSort` のデータメンバーで指定したもの、および指定したパラメーターに基づいて、完全な SQL ステートメントが作成されます。 レコードセットがこの SQL ステートメントを構築する方法の詳細については、「[レコードセット: レコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)」を参照してください。

> [!NOTE]
>  [Open](#open)を呼び出した後にのみ、このメンバー関数を呼び出します。

##  <a name="gettablename"></a>CRecordset:: GetTableName

レコードセットのクエリの基になっている SQL テーブルの名前を取得します。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>戻り値

レコードセットがテーブルに基づいている場合は、テーブル名を含む `CString` への**定数**参照。それ以外の場合は、空の文字列。

### <a name="remarks"></a>Remarks

`GetTableName` は、レコードセットがテーブルに基づいていて、複数のテーブルまたは定義済みのクエリ (ストアドプロシージャ) の結合ではない場合にのみ有効です。 名前は読み取り専用です。

> [!NOTE]
>  [Open](#open)を呼び出した後にのみ、このメンバー関数を呼び出します。

##  <a name="isbof"></a>CRecordset:: IsBOF

レコードセットが最初のレコードの前に配置されている場合は、0以外の値を返します。 現在のレコードがありません。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>戻り値

レコードセットにレコードが含まれていない場合、または最初のレコードの前に後方にスクロールした場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

レコードごとにスクロールしてレコードセットの最初のレコードの前に移動したかどうかを調べるには、このメンバー関数を呼び出します。 また、`IsBOF` を `IsEOF` と共に使用して、レコードセットにレコードが含まれているか、空であるかを判断することもできます。 `Open`を呼び出した直後、レコードセットにレコードが含まれていない場合、`IsBOF` は0以外の値を返します。少なくとも1つのレコードを含むレコードセットを開くと、最初のレコードが現在のレコードになり、`IsBOF` 0 が返されます。

最初のレコードが現在のレコードで、`MovePrev`を呼び出すと、`IsBOF` は0以外の値を返します。 `IsBOF` が0以外の値を返し、`MovePrev`を呼び出すと、エラーが発生します。 `IsBOF` が0以外の値を返した場合、現在のレコードは未定義であり、現在のレコードを必要とするすべてのアクションでエラーが発生します。

### <a name="example"></a>例

この例では、`IsBOF` と `IsEOF` を使用して、コードが双方向にレコードセットをスクロールするため、レコードセットの制限を検出します。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset:: IsDeleted

現在のレコードが削除されているかどうかを判断します。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>戻り値

レコードセットが削除されたレコードに配置されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

レコードまでスクロールし、`IsDeleted` が TRUE (0 以外) を返した場合は、他のレコードセット操作を実行する前に、別のレコードまでスクロールする必要があります。

`IsDeleted` の結果は、レコードセットの種類、レコードセットが更新可能かどうか、レコードセットを開いたときに `CRecordset::skipDeletedRecords` オプションを指定したかどうか、ドライバーが削除されたレコードをパックしているかどうか、および複数の要素があるかどうかなど、さまざまな要因によって異なります。ユーザ.

`CRecordset::skipDeletedRecords` とドライバーパッキングの詳細については、「 [Open](#open) member 関数」を参照してください。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`IsDeleted`を呼び出さないでください。 代わりに、 [Getrowstatus](#getrowstatus)メンバー関数を呼び出します。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="iseof"></a>CRecordset:: IsEOF

レコードセットが最後のレコードの後に配置されている場合は0以外の値を返します。 現在のレコードがありません。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>戻り値

レコードセットにレコードが含まれていない場合、または最後のレコードを超えてスクロールした場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

レコードごとにスクロールしてレコードセットの最後のレコードを超えたかどうかを確認するには、このメンバー関数を呼び出します。 `IsEOF` を使用して、レコードセットにレコードが含まれているか、空であるかどうかを確認することもできます。 `Open`を呼び出した直後、レコードセットにレコードが含まれていない場合、`IsEOF` は0以外の値を返します。 少なくとも1つのレコードを含むレコードセットを開くと、最初のレコードが現在のレコードになり、`IsEOF` 0 が返されます。

`MoveNext`を呼び出すと最後のレコードが現在のレコードの場合、`IsEOF` は0以外の値を返します。 `IsEOF` が0以外の値を返し、`MoveNext`を呼び出すと、エラーが発生します。 `IsEOF` が0以外の値を返した場合、現在のレコードは未定義であり、現在のレコードを必要とするすべてのアクションでエラーが発生します。

### <a name="example"></a>例

「 [IsBOF](#isbof)」の例を参照してください。

##  <a name="isfielddirty"></a>CRecordset:: IsFieldDirty

指定されたフィールドデータメンバーが、 [Edit](#edit)または[AddNew](#addnew)の呼び出し以降に変更されたかどうかを判断します。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
状態を確認するフィールドデータメンバーへのポインター。または、いずれかのフィールドがダーティかどうかを判断する場合は NULL。

### <a name="return-value"></a>戻り値

`AddNew` または `Edit`を呼び出した後に指定されたフィールドデータメンバーが変更された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

`CRecordset` の[更新](#update)メンバー関数 (`Edit` または `AddNew`) の呼び出しによって現在のレコードが更新されると、すべてのダーティフィールドデータメンバーのデータがデータソースのレコードに転送されます。

> [!NOTE]
>  このメンバー関数は、バルク行フェッチを使用しているレコードセットには適用されません。 バルク行フェッチを実装した場合、`IsFieldDirty` は常に FALSE を返し、アサーションは失敗します。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

`IsFieldDirty` を呼び出すと、フィールドのダーティステータスが再評価されるため、 [SetFieldDirty](#setfielddirty)への先行呼び出しの効果がリセットされます。 `AddNew` の場合、現在のフィールドの値が擬似的な null 値と異なる場合、フィールドの状態は "ダーティ" に設定されます。 `Edit` ケースでは、フィールドの値がキャッシュされた値と異なる場合、フィールドの状態は "ダーティ" に設定されます。

`IsFieldDirty` は[DoFieldExchange](#dofieldexchange)を介して実装されます。

ダーティフラグの詳細については、「レコード[セット: レコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)」を参照してください。

##  <a name="isfieldnull"></a>CRecordset:: IsFieldNull

現在のレコード内の指定されたフィールドが Null (値がない) の場合は、0以外の値を返します。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
状態を確認するフィールドデータメンバーへのポインター。または、いずれかのフィールドが Null かどうかを判断する場合は NULL。

### <a name="return-value"></a>戻り値

指定されたフィールドデータメンバーに Null のフラグが設定されている場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメンバー関数を呼び出して、レコードセットの指定したフィールドデータメンバーに Null としてフラグが設定されているかどうかを確認します。 (データベース用語では、Null は "値がありません" を意味し、でC++は null と同じではありません)。フィールドデータメンバーに Null のフラグが設定されている場合、そのメンバーは、値がない現在のレコードの列として解釈されます。

> [!NOTE]
>  このメンバー関数は、バルク行フェッチを使用しているレコードセットには適用されません。 バルク行フェッチを実装した場合、`IsFieldNull` は常に FALSE を返し、アサーションは失敗します。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

`IsFieldNull` は[DoFieldExchange](#dofieldexchange)を介して実装されます。

##  <a name="isfieldnullable"></a>CRecordset:: IsFieldNullable

現在のレコード内の指定されたフィールドを Null に設定できる場合 (値がない場合) は0以外の値を返します。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
状態を確認するフィールドデータメンバーへのポインター。または、いずれかのフィールドが Null 値に設定できるかどうかを判断する場合は NULL。

### <a name="remarks"></a>Remarks

このメンバー関数を呼び出して、指定されたフィールドデータメンバーが "nullable" である (Null 値に設定できる) かどうかを確認します。C++ Null は null と同じではありません。これは、データベース用語では、"値がない" ことを意味します。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`IsFieldNullable`を呼び出すことはできません。 代わりに、 [Getodbcfieldinfo](#getodbcfieldinfo)メンバー関数を呼び出して、フィールドを Null 値に設定できるかどうかを判断します。 バルク行フェッチが実装されているかどうかにかかわらず、常に `GetODBCFieldInfo`を呼び出すことができます。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

Null にできないフィールドには値が必要です。 レコードを追加または更新するときにこのようなフィールドを Null に設定しようとすると、データソースは追加または更新を拒否し、 [update](#update)は例外をスローします。 この例外は、 [SetFieldNull](#setfieldnull)を呼び出したときではなく `Update`を呼び出すと発生します。

関数の最初の引数に NULL を使用すると、関数が `param` フィールドではなく `outputColumn` フィールドにのみ適用されます。 たとえば、

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` フィールドのみを NULL に設定します。`param` のフィールドは影響を受けません。

`param` のフィールドを操作するには、次のように、作業する個々の `param` の実際のアドレスを指定する必要があります。

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

つまり、`outputColumn` フィールドの場合と同様に、すべての `param` フィールドを NULL に設定することはできません。

`IsFieldNullable` は[DoFieldExchange](#dofieldexchange)を介して実装されます。

##  <a name="isopen"></a>CRecordset:: IsOpen

レコードセットが既に開いているかどうかを判断します。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

レコードセットオブジェクトの[Open](#open)または[Requery](#requery)メンバー関数が既に呼び出されていて、レコードセットが閉じられていない場合は0以外。それ以外の場合は0です。

##  <a name="m_hstmt"></a>CRecordset:: m_hstmt

レコードセットに関連付けられた、HSTMT 型の ODBC ステートメントデータ構造体を表すハンドルを格納します。

### <a name="remarks"></a>Remarks

ODBC データソースに対する各クエリは、HSTMT に関連付けられています。

> [!CAUTION]
>  [Open](#open)が呼び出される前に `m_hstmt` を使用しないでください。

通常、HSTMT に直接アクセスする必要はありませんが、SQL ステートメントを直接実行するために必要になる場合があります。 クラス `CDatabase` の `ExecuteSQL` メンバー関数は、`m_hstmt`の使用例を示しています。

##  <a name="m_nfields"></a>CRecordset:: m_nFields

レコードセットクラスのフィールドデータメンバーの数を格納します。これは、データソースからレコードセットによって選択された列の数です。

### <a name="remarks"></a>Remarks

レコードセットクラスのコンストラクターは、正しい数値を使用して `m_nFields` を初期化する必要があります。 バルク行フェッチを実装していない場合、ClassWizard では、レコードセットクラスを宣言するときに、この初期化が書き込まれます。 また、手動で書き込むこともできます。

フレームワークは、この数値を使用して、フィールドデータメンバーと、データソースの現在のレコードの対応する列との間の対話を管理します。

> [!CAUTION]
>  この数値は、パラメーター `CFieldExchange::outputColumn`で[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)を呼び出した後、`DoFieldExchange` または `DoBulkFieldExchange` に登録されている "出力列" の数に対応している必要があります。

記事「レコードセット: 動的にデータ列をバインドする」で説明されているように、列を動的にバインドできます。 その場合は、`m_nFields` のカウントを増やして、動的にバインドされた列の `DoFieldExchange` または `DoBulkFieldExchange` メンバー関数内の RFX 関数または Bulk RFX 関数呼び出しの数を反映する必要があります。

詳細については、「レコード[セット: 動的にデータ列をバインドする (odbc)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) 」および「レコード[セット: レコードを一括でフェッチする (odbc)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

「[レコードフィールドエクスチェンジ: RFX の使用](../../data/odbc/record-field-exchange-using-rfx.md)」を参照してください。

##  <a name="m_nparams"></a>CRecordset:: m_nParams

Recordset クラスのパラメーターデータメンバーの数を格納します。つまり、レコードセットのクエリで渡されるパラメーターの数です。

### <a name="remarks"></a>Remarks

レコードセットクラスにパラメーターデータメンバーが含まれている場合、クラスのコンストラクターは、正しい数値を使用して `m_nParams` を初期化する必要があります。 `m_nParams` の値の既定値は0です。 パラメーターデータメンバー (手動で行う必要があります) を追加する場合は、パラメーターの数を反映するために、クラスコンストラクターに初期化を手動で追加する必要もあります (これは、`m_strFilter` のプレースホルダーの数と少なくとも同じである必要があり `m_strSort`文字列)。

フレームワークは、レコードセットのクエリをパラメーター化するときに、この数値を使用します。

> [!CAUTION]
>  この数値は、パラメーター値が `CFieldExchange::inputParam`、`CFieldExchange::param`、`CFieldExchange::outputParam`、または `CFieldExchange::inoutParam`の[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)を呼び出した後、`DoFieldExchange` または `DoBulkFieldExchange` に登録されている "params" の数に対応している必要があります。

### <a name="example"></a>例

  「レコードセット[: レコードセットのパラメーター化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 」および「[レコードフィールドエクスチェンジ: RFX の使用](../../data/odbc/record-field-exchange-using-rfx.md)」を参照してください。

##  <a name="m_pdatabase"></a>CRecordset:: m_pDatabase

レコードセットをデータソースに接続するために使用する `CDatabase` オブジェクトへのポインターを格納します。

### <a name="remarks"></a>Remarks

この変数は2つの方法で設定されます。 通常は、レコードセットオブジェクトを構築するときに、既に接続されている `CDatabase` オブジェクトへのポインターを渡します。 代わりに NULL を渡すと、`CRecordset` によって `CDatabase` オブジェクトが作成され、接続されます。 どちらの場合も、`CRecordset` によってこの変数にポインターが格納されます。

通常は、`m_pDatabase`に格納されているポインターを直接使用する必要はありません。 ただし、独自の拡張機能を `CRecordset`に記述する場合は、ポインターを使用する必要がある場合があります。 たとえば、独自の `CDBException`s をスローする場合は、ポインターが必要になることがあります。 または、トランザクションの実行、タイムアウトの設定、クラス `CDatabase` の `ExecuteSQL` メンバー関数の呼び出しなど、同じ `CDatabase` オブジェクトを使用して、SQL ステートメントを直接実行する必要がある場合にも必要になります。

##  <a name="m_strfilter"></a>CRecordset:: m_strFilter

レコードセットオブジェクトを作成した後、その `Open` メンバー関数を呼び出す前に、このデータメンバーを使用して、SQL **WHERE**句を含む `CString` を格納します。

### <a name="remarks"></a>Remarks

レコードセットは、この文字列を使用して、`Open` または `Requery` の呼び出し時に選択したレコードを制限 (またはフィルター) します。 これは、"カリフォルニアに基づくすべての販売員" ("state = CA") など、レコードのサブセットを選択する場合に便利です。 **WHERE**句の ODBC SQL 構文は、

`WHERE search-condition`

文字列に**WHERE**キーワードを含めないことに注意してください。 フレームワークによって提供されます。

また、フィルター文字列をパラメーター化するには、プレースホルダーに ' ' プレースホルダーを配置し、各プレースホルダーのクラスでパラメーターデータメンバーを宣言し、実行時にパラメーターをレコードセットに渡すこともできます。 これにより、実行時にフィルターを構築できます。 詳細については、「[レコードセット: レコードセットのパラメーター化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)」を参照してください。

SQL の**WHERE**句の詳細については、「 [sql](../../data/odbc/sql.md)」を参照してください。 レコードの選択とフィルター処理の詳細については、「レコード[セット: レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset:: m_strSort

レコードセットオブジェクトを作成した後、その `Open` メンバー関数を呼び出す前に、このデータメンバーを使用して、SQL **ORDER by**句を含む `CString` を格納します。

### <a name="remarks"></a>Remarks

レコードセットは、この文字列を使用して、`Open` または `Requery` の呼び出し時に選択したレコードを並べ替えます。 この機能を使用して、1つまたは複数の列のレコードセットを並べ替えることができます。 **ORDER by**句の ODBC SQL 構文は、

`ORDER BY sort-specification [, sort-specification]...`

ここで、並べ替え指定は整数または列名です。 また、並べ替え文字列の列リストに "ASC" または "DESC" を追加して、昇順または降順の順序を指定することもできます (既定では昇順です)。 選択したレコードは、最初にリストされている最初の列、次に2番目の列の順に並べ替えられます。 たとえば、"Customers" レコードセットを姓、名、および名で並べ替えることができます。 表示できる列の数は、データソースによって異なります。 詳細については、Windows SDK を参照してください。

文字列に**ORDER BY**キーワードを含めないことに注意してください。 フレームワークによって提供されます。

SQL 句の詳細については、「 [sql](../../data/odbc/sql.md)」を参照してください。 レコードの並べ替えの詳細については、「レコード[セット: レコードの並べ替え (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset:: Move

レコードセット内の現在のレコードポインターを前方または後方に移動します。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>パラメーター

*nRows*<br/>
前方または後方に移動する行の数。 正の値は、レコードセットの末尾に向かって前方に移動します。 負の値は、先頭に向かって後方に移動します。

*wFetchType*<br/>
`Move` がフェッチする行セットを決定します。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

*NRows*に値0を渡すと、`Move` によって現在のレコードが更新されます。`Move` により、現在の `AddNew` または `Edit` モードが終了し、`AddNew` または `Edit` が呼び出される前に現在のレコードの値が復元されます。

> [!NOTE]
>  レコードセット内を移動するときに、削除されたレコードをスキップすることはできません。 詳細については、「 [CRecordset:: IsDeleted](#isdeleted) 」を参照してください。 `skipDeletedRecords` オプションを設定して `CRecordset` を開くと、 *nRows*パラメーターが0の場合は `Move` アサートされます。 この動作により、同じデータを使用して他のクライアントアプリケーションによって削除された行を更新できなくなります。 `skipDeletedRecords`の説明については、「 [Open](#open) 」の*dwoption*パラメーターを参照してください。

`Move` は、レコードセットを行セット別に移動します。 *NRows*と*wFetchType*の値に基づいて、`Move` 適切な行セットがフェッチされ、その行セットの最初のレコードが現在のレコードになります。 バルク行フェッチを実装していない場合、行セットのサイズは常に1になります。 行セットをフェッチするときに、`Move` は、 [CheckRowsetError](#checkrowseterror)メンバー関数を直接呼び出して、フェッチによって発生したエラーを処理します。

渡される値によっては、`Move` は他の `CRecordset` メンバー関数と等価です。 特に、 *wFetchType*の値は、より直観的で、多くの場合、現在のレコードを移動するために推奨される方法であるメンバー関数を示すことができます。

次の表に、 *wFetchType*に指定できる値、 *wFetchType*と*nRows*に基づいてフェッチ `Move` れる行セット、および*wFetchType*に対応する同等のメンバー関数を示します。

|wFetchType|フェッチされる行セット|同等のメンバー関数|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (既定値)|現在の行セットの最初の行から*nRows*行を開始する行セット。||
|SQL_FETCH_NEXT|次の行セット。*nRows*は無視されます。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|前の行セット。*nRows*は無視されます。|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|レコードセット内の最初の行セット。*nRows*は無視されます。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|レコードセット内の最後の完全な行セットです。*nRows*は無視されます。|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|*NRows* > 0 の場合、行セットの先頭から*nRows*行が開始されます。 *NRows* < 0 の場合、行セットの末尾から*nRows*行が開始されます。 *NRows* = 0 の場合、ファイルの先頭 (BOF) 条件が返されます。|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|*NRows*に対応するブックマーク値を持つ行から始まる行セット。|[SetBookmark](#setbookmark)|

> [!NOTE]
>  前方参照専用のレコードセットの場合、`Move` は*wFetchType*に対して SQL_FETCH_NEXT の値を指定した場合にのみ有効です。

> [!CAUTION]
>  レコードセットにレコードがない場合、`Move` を呼び出すと例外がスローされます。 レコードセットにレコードがあるかどうかを確認するには、 [IsBOF](#isbof)と[IsEOF](#iseof)を呼び出します。

> [!NOTE]
>  レコードセットの先頭または末尾を超えてスクロールした場合 (`IsBOF` または `IsEOF` が0以外の値を返した場合)、`Move` 関数を呼び出すと、`CDBException`がスローされる可能性があります。 たとえば、`IsEOF` が0以外の値を返し、`IsBOF` ではない場合、`MoveNext` は例外をスローしますが、`MovePrev` はスローしません。

> [!NOTE]
>  現在のレコードが更新または追加されている間に `Move` を呼び出した場合、更新は警告なしに失われます。

レコードセットナビゲーションの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。 関連情報については、Windows SDK の ODBC API 関数 `SQLExtendedFetch` を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset:: MoveFirst

最初の行セットの最初のレコードを現在のレコードにします。

```
void MoveFirst();
```

### <a name="remarks"></a>Remarks

バルク行フェッチが実装されているかどうかにかかわらず、これは常にレコードセットの最初のレコードになります。

レコードセットを開いた直後に `MoveFirst` を呼び出す必要はありません。 その時点で、最初のレコード (存在する場合) が自動的に現在のレコードになります。

> [!NOTE]
>  このメンバー関数は、順方向専用レコードセットでは無効です。

> [!NOTE]
>  レコードセット内を移動するときに、削除されたレコードをスキップすることはできません。 詳細については、 [IsDeleted](#isdeleted)メンバー関数を参照してください。

> [!CAUTION]
>  レコードセットにレコードがない場合は、`Move` 関数のいずれかを呼び出すと例外がスローされます。 レコードセットにレコードがあるかどうかを確認するには、`IsBOF` を呼び出し、`IsEOF`します。

> [!NOTE]
>  現在のレコードを更新または追加しているときに `Move` 関数のいずれかを呼び出すと、警告なしに更新が失われます。

レコードセットナビゲーションの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

  「 [IsBOF](#isbof)」の例を参照してください。

##  <a name="movelast"></a>CRecordset:: MoveLast

最後の行セットの最初のレコードを現在のレコードにします。

```
void MoveLast();
```

### <a name="remarks"></a>Remarks

バルク行フェッチを実装していない場合、レコードセットの行セットサイズは1であるため、`MoveLast` は単にレコードセットの最後のレコードに移動します。

> [!NOTE]
>  このメンバー関数は、順方向専用レコードセットでは無効です。

> [!NOTE]
>  レコードセット内を移動するときに、削除されたレコードをスキップすることはできません。 詳細については、 [IsDeleted](#isdeleted)メンバー関数を参照してください。

> [!CAUTION]
>  レコードセットにレコードがない場合は、`Move` 関数のいずれかを呼び出すと例外がスローされます。 レコードセットにレコードがあるかどうかを確認するには、`IsBOF` を呼び出し、`IsEOF`します。

> [!NOTE]
>  現在のレコードを更新または追加しているときに `Move` 関数のいずれかを呼び出すと、警告なしに更新が失われます。

レコードセットナビゲーションの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

  「 [IsBOF](#isbof)」の例を参照してください。

##  <a name="movenext"></a>CRecordset:: MoveNext

次の行セットの最初のレコードを現在のレコードにします。

```
void MoveNext();
```

### <a name="remarks"></a>Remarks

バルク行フェッチを実装していない場合、レコードセットの行セットサイズは1であるため、`MoveNext` は単に次のレコードに移動します。

> [!NOTE]
>  レコードセット内を移動するときに、削除されたレコードをスキップすることはできません。 詳細については、 [IsDeleted](#isdeleted)メンバー関数を参照してください。

> [!CAUTION]
>  レコードセットにレコードがない場合は、`Move` 関数のいずれかを呼び出すと例外がスローされます。 レコードセットにレコードがあるかどうかを確認するには、`IsBOF` を呼び出し、`IsEOF`します。

> [!NOTE]
>  また、`MoveNext`を呼び出す前に `IsEOF` を呼び出すことをお勧めします。 たとえば、レコードセットの末尾を越えてスクロールした場合、`IsEOF` は0以外の値を返します。後続の `MoveNext` の呼び出しでは、例外がスローされます。

> [!NOTE]
>  現在のレコードを更新または追加しているときに `Move` 関数のいずれかを呼び出すと、警告なしに更新が失われます。

レコードセットナビゲーションの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

  「 [IsBOF](#isbof)」の例を参照してください。

##  <a name="moveprev"></a>CRecordset:: MovePrev

前の行セットの最初のレコードを現在のレコードにします。

```
void MovePrev();
```

### <a name="remarks"></a>Remarks

バルク行フェッチを実装していない場合、レコードセットの行セットサイズは1であるため、`MovePrev` は単に前のレコードに移動します。

> [!NOTE]
>  このメンバー関数は、順方向専用レコードセットでは無効です。

> [!NOTE]
>  レコードセット内を移動するときに、削除されたレコードをスキップすることはできません。 詳細については、 [IsDeleted](#isdeleted)メンバー関数を参照してください。

> [!CAUTION]
>  レコードセットにレコードがない場合は、`Move` 関数のいずれかを呼び出すと例外がスローされます。 レコードセットにレコードがあるかどうかを確認するには、`IsBOF` を呼び出し、`IsEOF`します。

> [!NOTE]
>  また、`MovePrev`を呼び出す前に `IsBOF` を呼び出すことをお勧めします。 たとえば、レコードセットの先頭から前方にスクロールした場合、`IsBOF` は0以外の値を返します。後続の `MovePrev` の呼び出しでは、例外がスローされます。

> [!NOTE]
>  現在のレコードを更新または追加しているときに `Move` 関数のいずれかを呼び出すと、警告なしに更新が失われます。

レコードセットナビゲーションの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

### <a name="example"></a>例

  「 [IsBOF](#isbof)」の例を参照してください。

##  <a name="onsetoptions"></a>CRecordset:: OnSetOptions

指定された ODBC ステートメントのオプション (選択時に使用される) を設定するために呼び出されます。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>パラメーター

*hstmt*<br/>
オプションを設定する ODBC ステートメントの HSTMT です。

### <a name="remarks"></a>Remarks

`OnSetOptions` を呼び出して、指定した ODBC ステートメントのオプション (選択時に使用) を設定します。 フレームワークは、このメンバー関数を呼び出して、レコードセットの初期オプションを設定します。 `OnSetOptions` は、スクロール可能なカーソルおよびカーソルの同時実行に対するデータソースのサポートを決定し、それに応じてレコードセットのオプションを設定します。 (`OnSetOptions` は選択操作に使用されるのに対し、`OnSetUpdateOptions` は更新操作に使用されます)。

ドライバーまたはデータソースに固有のオプションを設定するには、`OnSetOptions` をオーバーライドします。 たとえば、データソースで排他アクセスのためのオープンがサポートされている場合、その機能を利用するために `OnSetOptions` をオーバーライドすることがあります。

カーソルの詳細については、「 [ODBC](../../data/odbc/odbc-basics.md)」を参照してください。

##  <a name="onsetupdateoptions"></a>CRecordset:: OnSetUpdateOptions

指定された ODBC ステートメントに対してオプション (update で使用) を設定するために呼び出されます。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>パラメーター

*hstmt*<br/>
オプションを設定する ODBC ステートメントの HSTMT です。

### <a name="remarks"></a>Remarks

`OnSetUpdateOptions` を呼び出して、指定した ODBC ステートメントのオプション (update で使用) を設定します。 このメンバー関数は、レコードセット内のレコードを更新するための HSTMT を作成した後に、フレームワークによって呼び出されます。 (`OnSetOptions` は選択操作に使用されるのに対し、`OnSetUpdateOptions` は更新操作に使用されます)。`OnSetUpdateOptions` は、スクロール可能なカーソルおよびカーソルの同時実行に対するデータソースのサポートを決定し、それに応じてレコードセットのオプションを設定します。

このステートメントを使用してデータベースにアクセスする前に、ODBC ステートメントのオプションを設定するには、`OnSetUpdateOptions` をオーバーライドします。

カーソルの詳細については、「 [ODBC](../../data/odbc/odbc-basics.md)」を参照してください。

##  <a name="open"></a>CRecordset:: Open

テーブルを取得するか、レコードセットが表すクエリを実行して、レコードセットを開きます。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>パラメーター

*Noて Type*<br/>
既定値の AFX_DB_USE_DEFAULT_TYPE をそのまま使用するか、`enum OpenType`の次のいずれかの値を使用します。

- 双方向スクロールを使用してレコードセットを `CRecordset::dynaset` します。 レコードのメンバーシップおよび順序は、レコードセットを開いたときに決定されますが、他のユーザーによるデータ値の変更は、フェッチ操作後に表示されます。 ダイナセットは、キーセット ドリブン レコードセットとも呼ばれます。

- 双方向スクロールを使用して静的レコードセットを `CRecordset::snapshot` します。 レコードのメンバーシップと順序は、レコードセットを開いたときに決定されます。データ値は、レコードをフェッチしたときに決定されます。 他のユーザーが行った変更は、レコードセットを閉じてから再度開くまで表示されません。

- 双方向スクロールを使用してレコードセットを `CRecordset::dynamic` します。 他のユーザーが行ったメンバーシップ、順序、およびデータ値の変更は、フェッチ操作後に表示されます。 多くの ODBC ドライバーでは、この型のレコードセットはサポートされていません。

- 前方スクロールのみを含む読み取り専用のレコードセットを `CRecordset::forwardOnly` します。

   `CRecordset`の場合、既定値は `CRecordset::snapshot`です。 既定値の機構により、Visual C++ ウィザードで既定値の異なる ODBC `CRecordset` と DAO `CDaoRecordset` 両方を操作できます。

これらのレコードセットの種類の詳細については、「[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)」を参照してください。 関連情報については、Windows SDK の「ブロックカーソルとスクロール可能なカーソルの使用」を参照してください。

> [!CAUTION]
>  要求した型がサポートされていない場合、例外がスローされます。

*lpszSQL*<br/>
次のいずれかを含む文字列ポインター:

- NULL ポインター。

- テーブルの名前。

- SQL **SELECT**ステートメント (必要に応じて、sql **WHERE**句または**ORDER by**句を使用します)。

- 定義済みクエリ (ストアドプロシージャ) の名前を指定する**CALL**ステートメント。 中かっこと**CALL**キーワードの間に空白を挿入しないように注意してください。

この文字列の詳細については、「[解説](#remarks)」の表と ClassWizard のロールの説明を参照してください。

> [!NOTE]
>  結果セットの列の順序は、 [DoFieldExchange](#dofieldexchange)関数または[DoBulkFieldExchange](#dobulkfieldexchange)関数のオーバーライドで、Rfx 関数または Bulk rfx 関数呼び出しの順序と一致している必要があります。

*dwOptions*<br/>
以下に示す値の組み合わせを指定できるビットマスク。 これらの値の一部は同時に指定できません。 既定値は**none**です。

- `CRecordset::none` オプションは設定しません。 このパラメーター値は、他のすべての値と同時に指定できません。 既定では、レコードセットは、 [Edit](#edit)または[Delete](#delete)を使用して更新し、 [AddNew](#addnew)を使用して新しいレコードを追加することができます。 更新可能性は、指定した*Noて type*オプションだけでなく、データソースによっても異なります。 バルク追加の最適化は使用できません。 バルク行フェッチは実装されません。 削除されたレコードはレコードセットの移動中にスキップされません。 ブックマークは使用できません。 自動ダーティ フィールド チェックが実装されます。

- `CRecordset::appendOnly` では、レコードセットに対して `Edit` または `Delete` を許可しません。 `AddNew` のみ実行できます。 このオプションは `CRecordset::readOnly` と同時に指定できません。

- `CRecordset::readOnly` レコードセットを読み取り専用として開きます。 このオプションは `CRecordset::appendOnly` と同時に指定できません。

- 準備された SQL ステートメントを使用して、一度に多数のレコードを追加する `CRecordset::optimizeBulkAdd` ます。 ODBC API 関数 `SQLSetPos` を使用してレコードセットを更新していない場合にのみ適用されます。 最新の更新で、ダーティとマークされるフィールドが決まります。 このオプションは `CRecordset::useMultiRowFetch` と同時に指定できません。

- バルク行フェッチを実装して、1回のフェッチ操作で複数の行を取得できるように `CRecordset::useMultiRowFetch` します。 これは、パフォーマンスを向上するために設計された拡張機能です。ただし、バルク レコード フィールド エクスチェンジは ClassWizard ではサポートされていません。 このオプションは `CRecordset::optimizeBulkAdd` と同時に指定できません。 `CRecordset::useMultiRowFetch`を指定すると、オプション `CRecordset::noDirtyFieldCheck` が自動的にオンになります (ダブルバッファリングは使用できません)。順方向専用のレコードセットでは、オプション `CRecordset::useExtendedFetch` が自動的に有効になります。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

- レコードセット内を移動するときに、削除されたすべてのレコードをスキップ `CRecordset::skipDeletedRecords` ます。 これにより、特定の相対フェッチでパフォーマンスが低下します。 このオプションは前方スクロール専用レコードセットでは無効です。 *NRows*パラメーターを0に設定し、`CRecordset::skipDeletedRecords` オプションを設定して[Move](#move)を呼び出すと、`Move` によってアサートされます。 `CRecordset::skipDeletedRecords` は*ドライバーパッキング*に似ていることに注意してください。これは、削除された行がレコードセットから削除されることを意味します。 ただし、ドライバーによってレコードがパックされる場合、ユーザー自身が削除するレコードだけがスキップされます。レコードセットを開いている間に他のユーザーによって削除されたレコードはスキップされません。 `CRecordset::skipDeletedRecords` は、他のユーザーが削除した行をスキップします。

- サポートされている場合、`CRecordset::useBookmarks` はレコードセットでブックマークを使用できます。 ブックマークを使用すると、データの取得速度は低下しますが、データ移動のパフォーマンスが向上します。 前方スクロール専用レコードセットでは無効です。 詳細については、「[レコードセット: ブックマークと絶対位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。

- 自動ダーティフィールドチェック (ダブルバッファリング) をオフに `CRecordset::noDirtyFieldCheck` ます。 これにより、パフォーマンスは向上しますが、`SetFieldDirty` メンバー関数と `SetFieldNull` メンバー関数を呼び出して手動でフィールドをダーティとしてマークする必要があります。`CRecordset` クラスのダブル バッファリングは、`CDaoRecordset` クラスのダブル バッファリングに似ています。 ただし、`CRecordset` では、個別のフィールドに対してダブル バッファリングを有効にできません。すべてのフィールドに対して有効にするか、またはすべてのフィールドに対して無効にします。 `CRecordset::useMultiRowFetch`オプションを指定した場合、`CRecordset::noDirtyFieldCheck` は自動的にオンになります。ただし、`SetFieldDirty` と `SetFieldNull` は、バルク行フェッチを実装するレコードセットでは使用できません。

- `CRecordset::executeDirect` は、準備された SQL ステートメントを使用しません。 パフォーマンスを向上させるために、`Requery` メンバー関数が呼び出されないようにする場合は、このオプションを指定します。

- `SQLFetch`ではなく `SQLExtendedFetch` を実装 `CRecordset::useExtendedFetch` ます。 これは、前方スクロール専用レコードセットに対してバルク行フェッチを実装するために設計されています。 前方参照専用レコードセットに対して `CRecordset::useMultiRowFetch` オプションを指定すると、`CRecordset::useExtendedFetch` が自動的に有効になります。

- `CRecordset::userAllocMultiRowBuffers` ユーザーは、データのストレージバッファーを割り当てます。 独自の格納バッファーを割り当てる場合は、このオプションと一緒に `CRecordset::useMultiRowFetch` を使用します。使用しない場合、必要な格納バッファーが自動的に割り当てられます。 詳細については、「レコード[セット: レコードを一括フェッチする (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。 `CRecordset::useMultiRowFetch` を指定せずに `CRecordset::userAllocMultiRowBuffers` を指定すると、アサーションが失敗することに注意してください。

### <a name="return-value"></a>戻り値

`CRecordset` オブジェクトが正常に開かれた場合は0以外の場合は。[CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (呼び出された場合) が0を返す場合は0。

### <a name="remarks"></a>Remarks

レコードセットによって定義されたクエリを実行するには、このメンバー関数を呼び出す必要があります。 `Open`を呼び出す前に、レコードセットオブジェクトを作成する必要があります。

このレコードセットのデータソースへの接続は、`Open`を呼び出す前にレコードセットを作成する方法によって異なります。 データソースに接続されていないレコードセットコンストラクターに[CDatabase](../../mfc/reference/cdatabase-class.md)オブジェクトを渡した場合、このメンバー関数は[GetDefaultConnect](#getdefaultconnect)を使用してデータベースオブジェクトを開こうとします。 レコードセットコンストラクターに NULL を渡すと、コンストラクターによって `CDatabase` オブジェクトが構築され、`Open` によってデータベースオブジェクトが接続されます。 これらのさまざまな状況下でレコードセットと接続を閉じる方法の詳細については、「 [Close](#close)」を参照してください。

> [!NOTE]
>  `CRecordset` オブジェクトを使用したデータ ソースへのアクセスは常に共有されます。 `CDaoRecordset` クラスとは異なり、`CRecordset` オブジェクトを使用して排他アクセスでデータ ソースを開くことはできません。

`Open`を呼び出すと、クエリ (通常は SQL **SELECT**ステートメント) によって、次の表に示す条件に基づいてレコードが選択されます。

|lpszSQL パラメーターの値|レコードの選択基準|例|
|------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL` の返す文字列。||
|SQL テーブル名|`DoFieldExchange` または `DoBulkFieldExchange` のテーブル リストのすべての列。|`"Customer"`|
|定義済みクエリ (ストアド プロシージャ) の名前|返すためにクエリが定義された列。|`"{call OverDueAccts}"`|
|テーブルリスト**から**列リストを**選択し**ます|指定したテーブルの指定した列。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  SQL 文字列に余分な空白を挿入しないでください。 たとえば、中かっこと**CALL**キーワードの間に空白を挿入すると、MFC は SQL 文字列をテーブル名として誤って解釈し、 **SELECT**ステートメントに組み込みます。これにより、例外がスローされます。 同様に、定義済みのクエリで出力パラメーターを使用する場合は、中かっこと ' ' 記号の間に空白を挿入しないでください。 最後に、 **CALL**ステートメントの中かっこの前、または**Select**ステートメントの**select**キーワードの前に空白を挿入しないようにする必要があります。

通常の手順では、NULL を `Open`に渡します。この場合、`Open` は[GetDefaultSQL](#getdefaultsql)を呼び出します。 派生 `CRecordset` クラスを使用している場合は、ClassWizard で指定したテーブル名が `GetDefaultSQL` に与えられます。 代わりに、その他の情報を `lpszSQL` パラメーターに指定できます。

どのような場合でも、`Open` は、クエリの最終的な SQL 文字列を構築します (文字列には、渡された `lpszSQL` 文字列に SQL **WHERE**句と**ORDER BY**句が追加されている場合があります)。その後、クエリを実行します。 `Open`を呼び出した後に[GetSQL](#getsql)を呼び出すことによって、構築された文字列を調べることができます。 レコードセットが SQL ステートメントを作成してレコードを選択する方法の詳細については、「[レコードセット: レコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)」を参照してください。

レコードセット クラスのフィールド データ メンバーは、選択したデータの列に結び付けられています。 いくつかのレコードが返された場合、最初のレコードが現在のレコードになります。

フィルターや並べ替えなどのレコードセットのオプションを設定する場合は、レコードセットオブジェクトを作成した後、`Open`を呼び出す前に、これらのオプションを指定します。 レコードセットが既に開いている状態でレコードセット内のレコードを更新する場合は、 [Requery](#requery)を呼び出します。

その他の例を含む詳細については、「[レコードセット (odbc)](../../data/odbc/recordset-odbc.md)」、「[レコードセット: レコード選択のしくみ (odbc)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)」、および「[レコードセット: レコードセットの作成と終了 (odbc)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)」を参照してください。

### <a name="example"></a>例

次のコード例は、さまざまな形式の `Open` 呼び出しを示しています。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset:: RefreshRowset

現在の行セット内の行のデータと状態を更新します。

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>パラメーター

*wRow*<br/>
現在の行セット内の行の1から始まる位置。 この値の範囲は、0から行セットのサイズまでです。

*wLockType*<br/>
更新後に行をロックする方法を示す値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

*Wrow*に値0を渡すと、行セット内のすべての行が更新されます。

`RefreshRowset`を使用するには、 [Open](#open)メンバー関数で `CRecordset::useMulitRowFetch` オプションを指定することによって、バルク行フェッチを実装している必要があります。

`RefreshRowset` は、ODBC API 関数 `SQLSetPos`を呼び出します。 *Wlocktype*パラメーターは、`SQLSetPos` が実行された後の行のロック状態を指定します。 次の表では、 *Wlocktype*に使用できる値について説明します。

|wLockType|説明|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (既定値)|ドライバーまたはデータソースは、行が `RefreshRowset` が呼び出される前と同じロックまたはロック解除された状態であることを保証します。|
|SQL_LOCK_EXCLUSIVE|ドライバーまたはデータソースは、行を排他的にロックします。 一部のデータソースでは、この種類のロックがサポートされていません。|
|SQL_LOCK_UNLOCK|ドライバーまたはデータソースによって行のロックが解除されます。 一部のデータソースでは、この種類のロックがサポートされていません。|

`SQLSetPos`の詳細については、Windows SDK を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="requery"></a>CRecordset:: Requery

レコードセットを再構築 (更新) します。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>戻り値

レコードセットが正常に再構築された場合は0以外の場合は。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

いくつかのレコードが返された場合、最初のレコードが現在のレコードになります。

ユーザーまたは他のユーザーがデータソースに対して行った追加や削除をレコードセットに反映させるには、`Requery`を呼び出してレコードセットを再構築する必要があります。 レコードセットがダイナセットである場合は、自分または他のユーザーが既存のレコードに対して行った更新が自動的に反映されます (ただし、追加することはできません)。 レコードセットがスナップショットの場合は、`Requery` を呼び出して、他のユーザーによる編集と、追加や削除を反映する必要があります。

ダイナセットまたはスナップショットについては、新しいフィルターや並べ替え、または新しいパラメーター値を使用してレコードセットを再構築するときに、いつでも `Requery` を呼び出します。 `Requery`を呼び出す前に `m_strFilter` に新しい値を割り当てて `m_strSort` 新しいフィルターまたは並べ替えプロパティを設定します。 `Requery`を呼び出す前に、パラメーターデータメンバーに新しい値を割り当てることによって、新しいパラメーターを設定します。 フィルター文字列と並べ替え文字列が変更されていない場合は、クエリを再利用できます。これにより、パフォーマンスが向上します。

レコードセットを再構築しようとして失敗した場合、レコードセットは閉じられます。 `Requery`を呼び出す前に、`CanRestart` メンバー関数を呼び出してレコードセットを再度実行できるかどうかを確認できます。 `CanRestart` では、`Requery` が成功するとは限りません。

> [!CAUTION]
>  [Open](#open)を呼び出した後にのみ `Requery` を呼び出します。

### <a name="example"></a>例

この例では、レコードセットを再構築して別の並べ替え順序を適用します。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition

指定されたレコード番号に対応するレコードにレコードセットを配置します。

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>パラメーター

*nRows*<br/>
レコードセット内の現在のレコードの、1から始まる序数の位置。

### <a name="remarks"></a>Remarks

`SetAbsolutePosition` は、この序数位置に基づいて現在のレコードポインターを移動します。

> [!NOTE]
>  このメンバー関数は、順方向専用レコードセットでは無効です。

ODBC レコードセットの場合、絶対位置の設定1はレコードセット内の最初のレコードを表します。0の設定は、ファイルの先頭 (BOF) の位置を示します。

負の値を `SetAbsolutePosition`に渡すこともできます。 この場合、レコードセットの位置はレコードセットの末尾から評価されます。 たとえば、`SetAbsolutePosition( -1 )` は、現在のレコードポインターをレコードセット内の最後のレコードに移動します。

> [!NOTE]
>  絶対位置は、サロゲートレコード番号として使用するためのものではありません。 ブックマークは、前のレコードが削除されたときにレコードの位置が変更されるため、指定した位置に保持して返すことをお勧めします。 また、レコードセットが再作成された場合、特定のレコードの絶対位置が同じであることを保証することはできません。これは、レコードセット内の個々のレコードの順序が、SQL ステートメントで Order BY を使用して作成されている場合を除きます。句。

レコードセットナビゲーションとブックマークの詳細については、「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md) 」および「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)」を参照してください。

##  <a name="setbookmark"></a>CRecordset:: SetBookmark

指定されたブックマークを含むレコードにレコードセットを配置します。

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>パラメーター

*varBookmark*<br/>
特定のレコードのブックマーク値を格納している[CDBVariant](../../mfc/reference/cdbvariant-class.md)オブジェクトへの参照。

### <a name="remarks"></a>Remarks

レコードセットでブックマークがサポートされているかどうかを判断するには、 [Canbookmark](#canbookmark)を呼び出します。 サポートされている場合にブックマークを使用できるようにするには、 [Open](#open)メンバー関数の*dwOptions*パラメーターで `CRecordset::useBookmarks` オプションを設定する必要があります。

> [!NOTE]
>  ブックマークがサポートされていないか使用できない場合は、`SetBookmark` を呼び出すと、例外がスローされます。 ブックマークは、順方向専用のレコードセットではサポートされていません。

最初に現在のレコードのブックマークを取得するには、 [GetBookmark](#getbookmark)を呼び出します。これにより、ブックマーク値が `CDBVariant` オブジェクトに保存されます。 その後、保存されているブックマーク値を使用して `SetBookmark` を呼び出すことで、そのレコードに戻ることができます。

> [!NOTE]
>  特定のレコードセット操作の後、`SetBookmark`を呼び出す前に、ブックマークの永続化を確認する必要があります。 たとえば、`GetBookmark` でブックマークを取得し、`Requery`を呼び出すと、ブックマークが無効になることがあります。 `SetBookmark`を安全に呼び出すことができるかどうかを確認するには、 [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)を呼び出します。

ブックマークとレコードセットナビゲーションの詳細については、「[レコードセット: ブックマークと絶対位置 (odbc)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 」および「[レコードセット: スクロール (odbc)](../../data/odbc/recordset-scrolling-odbc.md)」を参照してください。

##  <a name="setfielddirty"></a>CRecordset:: SetFieldDirty

レコードセットのフィールドデータメンバーを変更済みとして、または変更せずにフラグを付けます。

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
レコードセットのフィールドデータメンバーのアドレス、または NULL を格納します。 NULL の場合、レコードセット内のすべてのフィールドデータメンバーにフラグが設定されます。 (C++ Null はデータベース用語では null と同じではなく、"値がない" ことを意味します)。

*bDirty*<br/>
フィールドデータメンバーに "ダーティ" としてフラグを設定する場合は TRUE (変更された場合)。 それ以外の場合は、フィールドデータメンバーに "clean" (変更なし) のフラグを設定する場合は FALSE。

### <a name="remarks"></a>Remarks

フィールドを変更せずにマークすると、フィールドが更新されず、SQL トラフィックが少なくなります。

> [!NOTE]
>  このメンバー関数は、バルク行フェッチを使用しているレコードセットには適用されません。 バルク行フェッチを実装している場合、`SetFieldDirty` によってアサーションが失敗します。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

フレームワークは、変更されたフィールドのデータメンバーを、レコードフィールドエクスチェンジ (RFX) メカニズムによってデータソースのレコードに書き込まれるようにマークします。 フィールドの値を変更すると、通常はダーティフィールドが自動的にダーティに設定されるため、`SetFieldDirty` を自分で呼び出す必要はほとんどありませんが、フィールドデータの値に関係なく、明示的に列が更新または挿入されるようにすることが必要になる場合があります。レプリカ.

> [!CAUTION]
>  このメンバー関数は、 [Edit](#edit)または[AddNew](#addnew)を呼び出した後にのみ呼び出してください。

関数の最初の引数に NULL を使用すると、関数が `param` フィールドではなく `outputColumn` フィールドにのみ適用されます。 たとえば、

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` フィールドのみを NULL に設定します。`param` のフィールドは影響を受けません。

`param` のフィールドを操作するには、次のように、作業する個々の `param` の実際のアドレスを指定する必要があります。

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

つまり、`outputColumn` フィールドの場合と同様に、すべての `param` フィールドを NULL に設定することはできません。

##  <a name="setfieldnull"></a>CRecordset:: SetFieldNull

レコードセットのフィールドデータメンバーに Null としてフラグを付けます (特に値を含まない)。または、Null 以外の値としてフラグを指定します。

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
レコードセットのフィールドデータメンバーのアドレス、または NULL を格納します。 NULL の場合、レコードセット内のすべてのフィールドデータメンバーにフラグが設定されます。 (C++ Null はデータベース用語では null と同じではなく、"値がない" ことを意味します)。

*bNull*<br/>
フィールドデータメンバーに値がないことを示すフラグが設定されている場合は0以外 (Null)。 それ以外の場合は、フィールドデータメンバーに Null 以外のフラグが設定されている場合は0になります。

### <a name="remarks"></a>Remarks

レコードセットに新しいレコードを追加すると、すべてのフィールドデータメンバーは最初に Null 値に設定され、"ダーティ" (変更) としてフラグが設定されます。 データソースからレコードを取得する場合、その列には既に値があるか、または Null になります。

> [!NOTE]
>  バルク行フェッチを使用しているレコードセットでは、このメンバー関数を呼び出さないでください。 バルク行フェッチを実装した場合、`SetFieldNull` を呼び出すと、アサーションが失敗します。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

現在のレコードのフィールドに値を設定しないように指定する場合は、 *Bnull*を TRUE に設定して `SetFieldNull` を呼び出し、null としてフラグを設定します。 フィールドが以前は Null とマークされていて、値を指定する必要がある場合は、単に新しい値を設定します。 `SetFieldNull`で Null フラグを削除する必要はありません。 フィールドを Null にできるかどうかを判断するには、`IsFieldNullable`を呼び出します。

> [!CAUTION]
>  このメンバー関数は、 [Edit](#edit)または[AddNew](#addnew)を呼び出した後にのみ呼び出してください。

関数の最初の引数に NULL を使用すると、関数が `param` フィールドではなく `outputColumn` フィールドにのみ適用されます。 たとえば、

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

`outputColumn` フィールドのみを NULL に設定します。`param` のフィールドは影響を受けません。

`param` のフィールドを操作するには、次のように、作業する個々の `param` の実際のアドレスを指定する必要があります。

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

つまり、`outputColumn` フィールドの場合と同様に、すべての `param` フィールドを NULL に設定することはできません。

> [!NOTE]
>  パラメーターを Null に設定すると、レコードセットが開かれる前に `SetFieldNull` を呼び出すと、アサーションが発生します。 この場合は、 [Setparamnull](#setparamnull)を呼び出します。

`SetFieldNull` は[DoFieldExchange](#dofieldexchange)を介して実装されます。

##  <a name="setlockingmode"></a>CRecordset:: Setロックモード

ロックモードを "オプティミスティック" ロック (既定値) または "ペシミスティック" ロックに設定します。 更新のためにレコードをロックする方法を指定します。

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>パラメーター

*Evaluationmode*<br/>
`enum LockMode`の次のいずれかの値を格納します。

- オプティミスティックロック `optimistic`、`Update`の呼び出し中にのみ更新されるレコードをロックします。

- `pessimistic` ペシミスティックロックは、`Edit` が呼び出されるとすぐにレコードをロックし、`Update` の呼び出しが完了するか新しいレコードに移動するまでロックを保持します。

### <a name="remarks"></a>Remarks

レコードセットが更新に使用する2つのレコードロックの方法を指定する必要がある場合は、このメンバー関数を呼び出します。 既定では、レコードセットのロックモードは `optimistic`です。 これは、より慎重な `pessimistic` ロック戦略に変更できます。 レコードセットオブジェクトを構築して開いた後、`Edit`を呼び出す前に、`SetLockingMode` を呼び出します。

##  <a name="setparamnull"></a>CRecordset:: SetParamNull

パラメーターに Null (具体的には値がない) または非 Null としてフラグを付けます。

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
パラメーターの 0 から始まるインデックス。

*bNull*<br/>
TRUE (既定値) の場合、パラメーターは Null としてフラグが設定されます。 それ以外の場合、パラメーターには Null 以外のフラグが設定されます。

### <a name="remarks"></a>Remarks

[SetFieldNull](#setfieldnull)とは異なり、レコードセットを開く前に `SetParamNull` を呼び出すことができます。

`SetParamNull` は、通常、定義済みのクエリ (ストアドプロシージャ) と共に使用されます。

##  <a name="setrowsetcursorposition"></a>CRecordset:: SetRowsetCursorPosition

現在の行セット内の行にカーソルを移動します。

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>パラメーター

*wRow*<br/>
現在の行セット内の行の1から始まる位置。 この値の範囲は、1から行セットのサイズまでです。

*wLockType*<br/>
更新後に行をロックする方法を示す値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

バルク行フェッチを実装する場合、レコードは行セットによって取得され、フェッチされた行セットの最初のレコードが現在のレコードになります。 行セット内の別のレコードを現在のレコードにするには、`SetRowsetCursorPosition`を呼び出します。 たとえば、`SetRowsetCursorPosition` を[GetFieldValue](#getfieldvalue)メンバー関数と組み合わせて、レコードセットの任意のレコードからデータを動的に取得することができます。

`SetRowsetCursorPosition`を使用するには、 [Open](#open)メンバー関数で*dwOptions*パラメーターの `CRecordset::useMultiRowFetch` オプションを指定することによって、バルク行フェッチを実装している必要があります。

`SetRowsetCursorPosition` は、ODBC API 関数 `SQLSetPos`を呼び出します。 *Wlocktype*パラメーターは、`SQLSetPos` が実行された後の行のロック状態を指定します。 次の表では、 *Wlocktype*に使用できる値について説明します。

|wLockType|説明|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (既定値)|ドライバーまたはデータソースは、行が `SetRowsetCursorPosition` が呼び出される前と同じロックまたはロック解除された状態であることを保証します。|
|SQL_LOCK_EXCLUSIVE|ドライバーまたはデータソースは、行を排他的にロックします。 一部のデータソースでは、この種類のロックがサポートされていません。|
|SQL_LOCK_UNLOCK|ドライバーまたはデータソースによって行のロックが解除されます。 一部のデータソースでは、この種類のロックがサポートされていません。|

`SQLSetPos`の詳細については、Windows SDK を参照してください。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="setrowsetsize"></a>CRecordset:: SetRowsetSize

フェッチ中に取得するレコードの数を指定します。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>パラメーター

*dwNewRowsetSize*<br/>
特定のフェッチ中に取得する行の数。

### <a name="remarks"></a>Remarks

この仮想メンバー関数は、バルク行フェッチを使用しているときに、1つのフェッチ中に取得する行数を指定します。 バルク行フェッチを実装するには、 [Open](#open)メンバー関数の*dwOptions*パラメーターで `CRecordset::useMultiRowFetch` オプションを設定する必要があります。

> [!NOTE]
>  バルク行フェッチを実装せずに `SetRowsetSize` を呼び出すと、アサーションが失敗します。

`Open` を呼び出す前に `SetRowsetSize` を呼び出して、レコードセットの行セットのサイズを初期設定します。 バルク行フェッチを実装する場合の既定の行セットサイズは25です。

> [!NOTE]
>  `SetRowsetSize`を呼び出すときは注意が必要です。 `Open`の dwOptions パラメーターの `CRecordset::userAllocMultiRowBuffers` オプションで指定されているように、データのストレージを手動で割り当てる場合は、`SetRowsetSize`を呼び出した後、カーソルを実行する前に、これらのストレージバッファーを再割り当てする必要があるかどうかを確認する必要があります。ナビゲーション操作。

行セットサイズの現在の設定を取得するには、 [GetRowsetSize](#getrowsetsize)を呼び出します。

バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

##  <a name="update"></a>CRecordset:: Update

新しいデータまたは編集されたデータをデータソースに保存することにより、`AddNew` または `Edit` 操作を完了します。

```
virtual BOOL Update();
```

### <a name="return-value"></a>戻り値

1つのレコードが正常に更新された場合は0以外。それ以外の場合は、列が変更されていない場合は0です。 レコードが更新されなかった場合、または複数のレコードが更新された場合は、例外がスローされます。 また、データソースのその他のエラーに対しても例外がスローされます。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [AddNew](#addnew)または[Edit](#edit)メンバー関数の呼び出しの後に呼び出します。 この呼び出しは、`AddNew` または `Edit` 操作を完了するために必要です。

> [!NOTE]
>  バルク行フェッチを実装している場合は、`Update`を呼び出すことはできません。 これにより、アサーションは失敗します。 クラス `CRecordset` は、データの一括行を更新するためのメカニズムを提供していませんが、ODBC API 関数 `SQLSetPos`を使用して独自の関数を記述することができます。 バルク行フェッチの詳細については、「 [レコードセット: バルク行フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

`AddNew` と `Edit` はどちらも、データソースに保存するために追加または編集されたデータを格納する編集バッファーを準備します。 `Update` によってデータが保存されます。 変更済みとしてマークまたは検出されたフィールドのみが更新されます。

データソースでトランザクションがサポートされている場合は、トランザクションの `Update` 呼び出し (およびそれに対応する `AddNew` または `Edit` 呼び出し) を行うことができます。 トランザクションの詳細については、「[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)」を参照してください。

> [!CAUTION]
>  最初に `AddNew` または `Edit`を呼び出さずに `Update` を呼び出すと、`Update` は `CDBException`をスローします。 `AddNew` または `Edit`を呼び出す場合は、`Move` 操作を呼び出す前、またはレコードセットまたはデータソース接続を閉じる前に `Update` を呼び出す必要があります。 そうしないと、変更内容が通知なしに失われます。

`Update` 障害の処理の詳細については、「レコード[セット: レコード更新のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)」を参照してください。

### <a name="example"></a>例

「[トランザクション: レコードセットでのトランザクションの実行 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView クラス](../../mfc/reference/crecordview-class.md)
