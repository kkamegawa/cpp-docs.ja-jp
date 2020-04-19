---
title: CDatabase クラス
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253715"
---
# <a name="cdatabase-class"></a>CDatabase クラス

データ ソースへの接続を表します。これを通じてデータ ソース上で操作を行うことができます。

## <a name="syntax"></a>構文

```
class CDatabase : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|`CDatabase` オブジェクトを構築します。 呼び出すことにより、オブジェクトを初期化する必要があります`OpenEx`または`Open`します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|「トランザクション」を開始-一連の呼び出し元に戻すことの`AddNew`、 `Edit`、`Delete`と`Update`クラスのメンバー関数`CRecordset`-に接続されたデータ ソース。 データ ソースのトランザクションをサポートする必要があります`BeginTrans`にまったく影響します。|
|[CDatabase::BindParameters](#bindparameters)|呼び出しの前にパラメーターをバインドすることができます`CDatabase::ExecuteSQL`します。|
|[CDatabase::Cancel](#cancel)|非同期操作または 2 番目のスレッドからのプロセスをキャンセルします。|
|[CDatabase::CanTransact](#cantransact)|データ ソースは、トランザクションをサポートしている場合、0 以外の値を返します。|
|[CDatabase::CanUpdate](#canupdate)|場合は 0 以外の値を返します、`CDatabase`オブジェクトが更新可能な (いない読み取り専用)。|
|[CDatabase::Close](#close)|データ ソース接続を閉じます。|
|[CDatabase::CommitTrans](#committrans)|によって開始されたトランザクションが完了すると`BeginTrans`します。 トランザクション内のデータ ソースを変更するコマンドが実行されます。|
|[CDatabase::ExecuteSQL](#executesql)|SQL ステートメントを実行します。 データ レコードは返されません。|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|レコード セット オブジェクトで使用されるブックマークを永続化操作を識別します。|
|[CDatabase::GetConnect](#getconnect)|接続に使用する ODBC 接続文字列を返します、`CDatabase`オブジェクトをデータ ソースにします。|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|開いているレコード セット オブジェクトでのトランザクションのコミットの効果を識別します。|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|開いているレコード セット オブジェクトのトランザクションのロールバックの効果を識別します。|
|[CDatabase::GetDatabaseName](#getdatabasename)|現在使用中のデータベースの名前を返します。|
|[CDatabase::IsOpen](#isopen)|場合は 0 以外の値を返します、`CDatabase`オブジェクトが現在データ ソースに接続されています。|
|[CDatabase::OnSetOptions](#onsetoptions)|標準的な接続オプションを設定するためにフレームワークによって呼び出されます。 既定の実装では、クエリのタイムアウト値を設定します。 事前にこれらのオプションを確立するには呼び出すことによって`SetQueryTimeout`します。|
|[CDatabase::Open](#open)|(ODBC ドライバー) を通じてデータ ソースへの接続を確立します。|
|[CDatabase::OpenEx](#openex)|(ODBC ドライバー) を通じてデータ ソースへの接続を確立します。|
|[CDatabase::Rollback](#rollback)|現在のトランザクションで加えられた変更を反転させます。 定義されている以前の状態、データ ソースを返します、`BeginTrans`呼び出し、そのままです。|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|その後、データ ソースの接続試行がタイムアウトになります秒数を設定します。|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|データベースの後の秒数のクエリ操作のセットがタイムアウトになります。後続のすべてのレコード セットの影響を与える`Open`、 `AddNew`、 `Edit`、および`Delete`呼び出し。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|データ ソースへの open Database Connectivity (ODBC) 接続ハンドルです。 型*HDBC*します。|

## <a name="remarks"></a>Remarks

データ ソースは、いくつかのデータベース管理システム (DBMS) によってホストされているデータの特定のインスタンスです。 例としては、Microsoft SQL Server、Microsoft Access、Borland dBASE、xBASE です。 1 つまたは複数を持てる`CDatabase`アプリケーションで一度にアクティブなオブジェクト。

> [!NOTE]
>  Open Database Connectivity (ODBC) クラスではなく、データ アクセス オブジェクト (DAO) クラスを使用している場合は、クラスを使用して[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)代わりにします。 詳細については、この記事を参照してください。[概要。データベース プログラミング](../../data/data-access-programming-mfc-atl.md)します。

使用する`CDatabase`、構築、`CDatabase`オブジェクトと呼び出しの`OpenEx`メンバー関数。 これは、接続を開きます。 構築する際に`CRecordset`、接続されているデータ ソースに対する操作のためのオブジェクトへのポインターをレコード セットのコンス トラクターに渡す、`CDatabase`オブジェクト。 接続を使用してが完了したら、呼び出し、`Close`メンバー関数し、破棄、`CDatabase`オブジェクト。 `Close` 閉じられていないすべてのレコード セットを閉じます。

詳細については`CDatabase`、記事を参照して[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)と[概要。データベース プログラミング](../../data/data-access-programming-mfc-atl.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdb.h

##  <a name="begintrans"></a>  CDatabase::BeginTrans

接続されたデータ ソースでトランザクションを開始するには、このメンバー関数を呼び出します。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>戻り値

呼び出しが成功し、変更がのみ手動でコミットされる場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

トランザクションでは、1 つまたは複数の呼び出しの`AddNew`、 `Edit`、 `Delete`、および`Update`のメンバー関数は、`CRecordset`オブジェクト。 トランザクションを開始する前に、`CDatabase`オブジェクトする必要があります既にに接続されているデータ ソースを呼び出してその`OpenEx`または`Open`メンバー関数。 トランザクションを終了するには、呼び出し[CommitTrans](#committrans)データ ソースへのすべての変更を受け入れる (およびそれらを実行) を呼び出したり[ロールバック](#rollback)全体のトランザクションを中止します。 呼び出す`BeginTrans`した後、トランザクションに関連するすべてのレコード セットを開くし、として、実際の更新操作。

> [!CAUTION]
>  ODBC ドライバーによって呼び出す前にレコード セットを開く`BeginTrans`を呼び出すときに問題が発生する可能性があります`Rollback`します。 使用する特定のドライバーを確認する必要があります。 たとえば、Microsoft ODBC デスクトップ Driver パック 3.0 に含まれる Microsoft Access ドライバーを使用する場合、開いているカーソルのある任意のデータベースのトランザクションを開始する必要がありますいない Jet データベース エンジンの要件の考慮する必要があります。 MFC データベース クラスで、開いているカーソルは開いていることを意味`CRecordset`オブジェクト。 詳細については、次を参照してください。[テクニカル ノート 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)します。

`BeginTrans` 要求された同時実行とデータ ソースの機能に応じて、サーバー上のデータ レコードをロックも可能性があります。 データのロックについては、記事を参照してください。[レコード セット。レコードのロック (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)します。

ユーザー定義のトランザクションについては、この記事で[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

`BeginTrans` 確立する一連のトランザクションをロールバックできる状態 (反転)。 ロールバックの新しい状態を確立するために、現在のトランザクションをコミットし、呼び出す`BeginTrans`もう一度です。

> [!CAUTION]
>  呼び出す`BeginTrans`呼び出さずにもう一度`CommitTrans`または`Rollback`エラーが発生します。

呼び出す、 [CanTransact](#cantransact)ドライバーが特定のデータベースのトランザクションをサポートしているかどうかを調べます。 呼び出す必要もあります[GetCursorCommitBehavior](#getcursorcommitbehavior)と[GetCursorRollbackBehavior](#getcursorrollbackbehavior)カーソルによる保存のサポートを確認します。

トランザクションの詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

### <a name="example"></a>例

  記事をご覧ください[トランザクション。レコード セット (ODBC) からのトランザクション実行](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)します。

##  <a name="bindparameters"></a>  CDatabase::BindParameters

オーバーライド`BindParameters`呼び出す前にパラメーターをバインドする必要がある場合[:executesql](#executesql)します。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>パラメーター

*hstmt*<br/>
パラメーターをバインドする、ODBC ステートメント ハンドル。

### <a name="remarks"></a>Remarks

このアプローチは、結果を必要としない場合に便利です、ストアド プロシージャから設定します。

オーバーライドの中で呼び出す`SQLBindParameters`および関連する ODBC 関数にパラメーターをバインドします。 MFC への呼び出しの前に、オーバーライドを呼び出す`ExecuteSQL`します。 呼び出す必要はありません`SQLPrepare`;`ExecuteSQL`呼び出し`SQLExecDirect`し、破棄、 *hstmt*、これは一度だけ使用します。

##  <a name="cancel"></a>  CDatabase::Cancel

実行中の非同期操作または 2 つ目のスレッドからのプロセスのいずれかにキャンセルするデータ ソースを要求するには、このメンバー関数を呼び出します。

```
void Cancel();
```

### <a name="remarks"></a>Remarks

MFC ODBC クラスは、非同期処理を不要になった使用に注意してください。非同期操作を実行する ODBC API 関数を直接に呼び出す必要があります[SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)します。 詳細については、次を参照してください。[非同期実行](/sql/odbc/reference/develop-app/asynchronous-execution)します。

##  <a name="cantransact"></a>  CDatabase::CanTransact

データベースがトランザクションをできるかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>戻り値

0 以外の値を使用してこのレコード セット`CDatabase`オブジェクトは、トランザクションを許可する。 それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

トランザクションの詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

##  <a name="canupdate"></a>  CDatabase::CanUpdate

確認するには、このメンバー関数を呼び出すかどうか、`CDatabase`オブジェクトを更新します。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>戻り値

0 以外の値、`CDatabase`更新プログラムを許可するオブジェクト。 それ以外の場合は 0、いずれかがあるかを示すで渡されます TRUE *bReadOnly*開いたときに、`CDatabase`オブジェクトまたはデータがソース自体は読み取り専用です。 データ ソースは、ODBC API 関数への呼び出しは読み取り専用`SQLGetInfo`SQL_DATASOURCE_READ_ONLY は"y"を返します。

### <a name="remarks"></a>Remarks

すべてのドライバーでは、更新をサポートします。

##  <a name="cdatabase"></a>  CDatabase::CDatabase

`CDatabase` オブジェクトを構築します。

```
CDatabase();
```

### <a name="remarks"></a>Remarks

オブジェクトを構築後に呼び出す必要があるその`OpenEx`または`Open`メンバー関数を指定したデータ ソースへの接続を確立します。

埋め込むできると便利な場合があります、`CDatabase`ドキュメント クラス内のオブジェクト。

### <a name="example"></a>例

この例を使用して`CDatabase`で、 `CDocument`-クラスを派生します。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>  CDatabase::Close

データ ソースから切断する場合は、このメンバー関数を呼び出します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

関連付けられているすべてのレコード セットを閉じる必要があります、`CDatabase`オブジェクトのこのメンバー関数を呼び出す前にします。 `Close`を破棄しません、`CDatabase`オブジェクト、同じデータ ソースまたは別のデータ ソースへの新しい接続を開くことで、オブジェクトを再利用できます。

保留中のすべて`AddNew`または`Edit`データベースを使用してレコード セットのステートメントが取り消されると、および保留中のトランザクションがすべてロールバックされます。 すべてのレコード セットに依存する、`CDatabase`オブジェクトが定義されていない状態のままにします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>  CDatabase::CommitTrans

トランザクションを完了すると、このメンバー関数を呼び出します。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>戻り値

更新プログラムが正常にコミットされた場合は 0 以外それ以外の場合 0 を返します。 場合`CommitTrans`失敗した場合、データ ソースの状態が定義されています。 その状態を確認するデータを確認する必要があります。

### <a name="remarks"></a>Remarks

トランザクションでは、一連の呼び出しの`AddNew`、 `Edit`、 `Delete`、および`Update`のメンバー関数は、`CRecordset`オブジェクトへの呼び出しで開始された、 [BeginTrans](#begintrans)メンバー関数。 `CommitTrans` トランザクションをコミットします。 既定では、更新プログラムすぐにコミットされます。呼び出す`BeginTrans`まで遅延する更新プログラムのコミットメントにより`CommitTrans`が呼び出されます。

呼び出すまで`CommitTrans`、トランザクションを終了するには、呼び出すことができます、[ロールバック](#rollback)メンバー関数は、トランザクションを中止し、データ ソースを元の状態のままにします。 新しいトランザクションを開始するには、呼び出す`BeginTrans`もう一度です。

トランザクションの詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

### <a name="example"></a>例

  記事をご覧ください[トランザクション。レコード セット (ODBC) からのトランザクション実行](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)します。

##  <a name="executesql"></a>  CDatabase::ExecuteSQL

SQL コマンドを直接実行する必要がある場合は、このメンバー関数を呼び出します。

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>パラメーター

*lpszSQL*<br/>
実行する有効な SQL コマンドを含む null で終わる文字列へのポインター。 渡すことができます、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)します。

### <a name="remarks"></a>Remarks

Null で終わる文字列として、コマンドを作成します。 `ExecuteSQL` データ レコードは返されません。 レコードを操作する場合は、代わりに、レコード セット オブジェクトを使用します。

ほとんどのデータ ソースのコマンドは、データを選択すると、新しいレコードの挿入、レコードを削除、およびレコードの編集のコマンドをサポートしているレコード セット オブジェクトを介して発行されます。 ただし、ODBC の機能は、クラスで直接サポート、データベース、時点で直接 SQL 呼び出しを実行する必要がありますので`ExecuteSQL`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>  CDatabase::GetBookmarkPersistence

特定の操作の後で、レコードセット オブジェクトでのブックマークの永続性を判別するには、このメンバー関数を呼び出します。

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>戻り値

レコードセット オブジェクトでブックマークが保持されている操作を識別するビットマスク。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

たとえば、`CRecordset::GetBookmark` を呼び出してから `CRecordset::Requery` を呼び出した場合、`GetBookmark` から取得されたブックマークは有効ではなくなっている場合があります。 `GetBookmarkPersistence` を呼び出してから `CRecordset::SetBookmark` を呼び出す必要があります。

`GetBookmarkPersistence` の戻り値として組み合わせることができるビットマスク値の一覧を次の表に示します。

|ビットマスク値|ブックマークの永続性|
|-------------------|--------------------------|
|SQL_BP_CLOSE|ブックマークが後に有効な`Requery`操作。|
|SQL_BP_DELETE|行のブックマークが後に有効では、`Delete`行に対して操作します。|
|SQL_BP_DROP|ブックマークが後に有効な`Close`操作。|
|SQL_BP_SCROLL|いずれかの後、ブックマークは有効な`Move`操作。 これは、`CRecordset::CanBookmark` によって返されるのと同様に、レコードセットでブックマークがサポートされているかどうかだけを示します。|
|SQL_BP_TRANSACTION|トランザクションがコミットまたはロールバックされた後、ブックマークは有効です。|
|SQL_BP_UPDATE|行のブックマークが後に有効では、`Update`行に対して操作します。|
|SQL_BP_OTHER_HSTMT|1 つのレコードセット オブジェクトに関連付けられたブックマークは、別のレコードセットで有効です。|

この戻り値の詳細については、ODBC API 関数を参照してください。 `SQLGetInfo` Windows SDK に含まれています。 ブックマークの詳細については、記事を参照してください。[レコード セット。ブックマークと絶対位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)します。

##  <a name="getconnect"></a>  CDatabase::GetConnect

このメンバー関数を呼び出すことで、`OpenEx` オブジェクトをデータ ソースに接続した `Open` または `CDatabase` の呼び出し時に使用された接続文字列を取得します。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>戻り値

A **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md)場合は、接続文字列を含む`OpenEx`または`Open`がされているという以外、それ以外の場合、空の文字列。

### <a name="remarks"></a>Remarks

参照してください[cdatabase::open](#open)の接続文字列を作成する方法を説明します。

##  <a name="getcursorcommitbehavior"></a>  CDatabase::GetCursorCommitBehavior

確認するには、このメンバー関数を呼び出す方法、 [CommitTrans](#committrans)操作に開いているレコード セット オブジェクトのカーソルに影響を与えます。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>戻り値

開いているレコード セット オブジェクトでのトランザクションの効果を示す値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

次の表は、可能な戻り値の`GetCursorCommitBehavior`と開いているレコード セットへの対応する影響。

|戻り値|CRecordset オブジェクトへの影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|呼び出す`CRecordset::Requery`トランザクションのコミット直後します。|
|SQL_CB_DELETE|呼び出す`CRecordset::Close`トランザクションのコミット直後します。|
|SQL_CB_PRESERVE|通常どおり続行`CRecordset`操作。|

この戻り値の詳細については、ODBC API 関数を参照してください。 `SQLGetInfo` Windows SDK に含まれています。 トランザクションの詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

##  <a name="getcursorrollbackbehavior"></a>  CDatabase::GetCursorRollbackBehavior

確認するには、このメンバー関数を呼び出す方法、[ロールバック](#rollback)操作に開いているレコード セット オブジェクトのカーソルに影響を与えます。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>戻り値

開いているレコード セット オブジェクトでのトランザクションの効果を示す値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

次の表は、可能な戻り値の`GetCursorRollbackBehavior`と開いているレコード セットへの対応する影響。

|戻り値|CRecordset オブジェクトへの影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|呼び出す`CRecordset::Requery`直後、トランザクションをロールバックします。|
|SQL_CB_DELETE|呼び出す`CRecordset::Close`直後、トランザクションをロールバックします。|
|SQL_CB_PRESERVE|通常どおり続行`CRecordset`操作。|

この戻り値の詳細については、ODBC API 関数を参照してください。 `SQLGetInfo` Windows SDK に含まれています。 トランザクションの詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName

(データ ソースは、「データベース」と呼ばれる名前付きオブジェクトを定義します) を指定した、現在接続されているデータベースの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)成功、それ以外の場合は、データベース名を含む、空`CString`します。

### <a name="remarks"></a>Remarks

指定されたデータ ソース名 (DSN) と同じです。 これはない、`OpenEx`または`Open`呼び出します。 どのような`GetDatabaseName`返しますは ODBC によって異なります。 一般に、データベースは、テーブルのコレクションです。 このエンティティの名前が`GetDatabaseName`それを返します。

たとえば、見出しにこの名前を表示することができます。 ODBC から名前を取得中にエラーが発生した場合`GetDatabaseName`空白を返します`CString`します。

##  <a name="isopen"></a>  CDatabase::IsOpen

確認するには、このメンバー関数を呼び出すかどうか、`CDatabase`オブジェクトが現在データ ソースに接続されています。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

0 以外の値、`CDatabase`オブジェクトが現在接続されている場合は 0。

##  <a name="m_hdbc"></a>  CDatabase::m_hdbc

ODBC データ ソース接続へのパブリックのハンドルが含まれています:「接続ハンドル」

### <a name="remarks"></a>Remarks

通常、する必要はありませんこのメンバー変数に直接アクセスします。 呼び出すときにフレームワークがハンドルを割り当てる代わりに、`OpenEx`または`Open`します。 フレームワークを呼び出すときに、ハンドルを割り当て解除、**削除**演算子に対して、`CDatabase`オブジェクト。 なお、`Close`メンバー関数は、ハンドルを解放できません。

状況によっては、ただし、する必要があります、ハンドルを直接使用します。 たとえば、クラスではなく、直接、ODBC API 関数を呼び出す必要があります`CDatabase`、接続ハンドルをパラメーターとして渡す必要があります。 次のコード例を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions

SQL ステートメントを直接実行するときに、フレームワークがこのメンバー関数を呼び出し、`ExecuteSQL`メンバー関数。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>パラメーター

*hstmt*<br/>
オプションが設定される ODBC ステートメント ハンドル。

### <a name="remarks"></a>Remarks

`CRecordset::OnSetOptions` このメンバー関数も呼び出します。

`OnSetOptions` ログイン タイムアウトの値を設定します。 前の呼び出しが発生した場合、`SetQueryTimeout`とメンバー関数、 `OnSetOptions` ; 現在の値を反映してそれ以外の場合、既定値を設定します。

> [!NOTE]
>  4.2、`OnSetOptions`もか snychronous または非同期処理モードを設定します。 MFC 4.2 以降では、すべての操作は、同期します。 非同期操作を実行する ODBC API 関数の直接呼び出しを行う必要があります`SQLSetPos`します。

オーバーライドする必要はありません`OnSetOptions`タイムアウト値を変更します。 代わりに、クエリのタイムアウト値をカスタマイズするには、呼び出す`SetQueryTimeout`はレコード セットを作成する前に`OnSetOptions`新しい値が使用されます。 値セットは、すべてのレコード セットまたは SQL の直接呼び出しで後続の操作に適用されます。

オーバーライド`OnSetOptions`追加オプションを設定する場合。 オーバーライドは基本クラスを呼び出す必要があります`OnSetOptions`前に、または ODBC API 関数を呼び出した後`SQLSetStmtOption`します。 フレームワークの既定の実装で示されているメソッドに従ってください`OnSetOptions`します。

##  <a name="open"></a>  CDatabase::Open

新しく構築された初期化するためにこのメンバー関数を呼び出す`CDatabase`オブジェクト。

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszDSN*<br/>
データ ソースの名前を指定します: ODBC 管理者プログラムを介した ODBC で名前が登録されています。 DSN の値がで指定されている場合*lpszConnect* (フォームに"DSN =\<データ ソース >") でもう一度指定してはなりませんが*lpszDSN*。 この場合、 *lpszDSN*は NULL になります。 それ以外の場合、ユーザーがデータ ソースを選択できるデータ ソース ダイアログ ボックスをユーザーに表示する場合は、NULL を渡すことができます。 詳細については、「解説」を参照してください。

*bExclusive*<br/>
クラス ライブラリのこのバージョンでサポートされていません。 現時点では、このパラメーターが TRUE の場合、アサーションは失敗します。 共有 (排他的ではありません)、データ ソースが常に開かれます。

*bReadOnly*<br/>
読み取り専用にして、データ ソースへの更新を禁止するために接続する場合は TRUE。 依存するすべてのレコード セットは、この属性を継承します。 既定値は FALSE です。

*lpszConnect*<br/>
接続文字列を指定します。 接続文字列は、データ ソース名、データ ソース、ユーザー認証の文字列 (パスワード、データ ソースでは、1 つが必要な場合)、およびその他の情報に有効なユーザー ID を含めることも、情報を連結します。 接続文字列全体を文字列"ODBC;"によってプレフィックス指定する必要があります。(大文字または小文字)。 "ODBC;"文字列を使用して、ODBC データ ソースに接続があることを示すこれは、クラス ライブラリの今後のバージョンは非 ODBC データ ソースをサポート可能性がある場合の上位互換性を確保します。

*bUseCursorLib*<br/>
ODBC カーソル ライブラリの DLL を読み込む場合は TRUE。 カーソル ライブラリでは、基になる、ODBC ドライバー (ドライバーには、それらがサポートしている) 場合に、ダイナセットの使用を有効に防ぐための機能の一部をマスクします。 カーソル ライブラリが読み込まれている場合にサポートされている専用のカーソルには、静的なスナップショットと順方向専用カーソルです。 既定値は TRUE です。 直接 recordset オブジェクトを作成する予定のかどうか`CRecordset`せず、そこから派生する、カーソル ライブラリをしないに読み込む必要があります。

### <a name="return-value"></a>戻り値

以外の場合は、接続が正常に行われました。それ以外の場合、ユーザーが選択した場合は 0 では、詳細な接続情報を要求するダイアログ ボックスが表示された場合をキャンセルします。 その他のすべてのケースでは、フレームワークは、例外をスローします。

### <a name="remarks"></a>Remarks

これを使用するにはレコード セット オブジェクトを構築する前に、データベース オブジェクトを初期化する必要があります。

> [!NOTE]
>  呼び出す、 [OpenEx](#openex)メンバー関数は、データ ソースに接続し、データベース オブジェクトを初期化することをお勧めします。

場合では、パラメーター、`Open`呼び出しには、接続を作成するのに十分な情報が含まれていない、ODBC ドライバーは、ユーザーから必要な情報を取得するダイアログ ボックスを開きます。 呼び出すと`Open`、接続文字列、 *lpszConnect*、プライベートに格納されている、`CDatabase`オブジェクトし、は、呼び出すことによって利用可能な[GetConnect](#getconnect)メンバー関数。

呼び出す前に、独自のダイアログ ボックスを開く場合は、`Open`パスワードなど、ユーザーから情報を取得するに渡す接続文字列にし、その情報を追加`Open`します。 または、アプリケーション呼び出しの時間を節約できます再利用できるように、次を指定した接続文字列にする場合があります`Open`上、`CDatabase`オブジェクト。

複数レベルのログイン認証の接続文字列を使用することもできます (それぞれ、別の`CDatabase`オブジェクト) またはその他のデータ ソースに固有の情報を伝達するためにします。 接続文字列の詳細については、Windows SDK の第 5 章を参照してください。

これは、方法は、たとえば、DBMS ホストが使用できない場合は、接続の試行がタイムアウトする可能性があります。 接続の試行が失敗した場合、`Open`スロー、`CDBException`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>  CDatabase::OpenEx

新しく構築された初期化するためにこのメンバー関数を呼び出す`CDatabase`オブジェクト。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>パラメーター

*lpszConnectString*<br/>
ODBC 接続文字列を指定します。 これには、データ ソース名のユーザー ID とパスワードなどの他の省略可能な情報も含まれます。 たとえば、"DSN SQLServer_Source; を =UID = SA;PWD = abc123"可能な接続文字列です。 NULL を渡す場合*lpszConnectString*、データ ソースのダイアログ ボックスでは、データ ソースの選択が求められます。

*dwOptions*<br/>
次の値の組み合わせを指定するビットマスクです。 既定値は 0、書き込みアクセス権と共有するには、ODBC カーソル ライブラリの DLL は読み込まれず、接続を作成するのに十分な情報がない場合にのみ、ODBC の接続 ダイアログ ボックスが表示されますとして、データベースが開かれることを意味します。

- `CDatabase::openExclusive` クラス ライブラリのこのバージョンでサポートされていません。 共有 (排他的ではありません)、データ ソースが常に開かれます。 現時点では、このオプションを指定する場合に、アサーションが失敗します。

- `CDatabase::openReadOnly` 読み取り専用データ ソースを開きます。

- `CDatabase::useCursorLib` ODBC カーソル ライブラリ DLL を読み込みます。 カーソル ライブラリでは、基になる、ODBC ドライバー (ドライバーには、それらがサポートしている) 場合に、ダイナセットの使用を有効に防ぐための機能の一部をマスクします。 カーソル ライブラリが読み込まれている場合にサポートされている専用のカーソルには、静的なスナップショットと順方向専用カーソルです。 直接 recordset オブジェクトを作成する予定のかどうか`CRecordset`せず、そこから派生する、カーソル ライブラリをしないに読み込む必要があります。

- `CDatabase::noOdbcDialog` 十分な接続情報を指定するかどうかに関係なく、ODBC の接続 ダイアログ ボックスは表示されません。

- `CDatabase::forceOdbcDialog` ODBC の接続 ダイアログ ボックスが常に表示します。

### <a name="return-value"></a>戻り値

以外の場合は、接続が正常に行われました。それ以外の場合、ユーザーが選択した場合は 0 では、詳細な接続情報を要求するダイアログ ボックスが表示された場合をキャンセルします。 その他のすべてのケースでは、フレームワークは、例外をスローします。

### <a name="remarks"></a>Remarks

これを使用するにはレコード セット オブジェクトを構築する前に、データベース オブジェクトを初期化する必要があります。

場合、 *lpszConnectString*パラメーター、`OpenEx`呼び出しに接続するために十分な情報が含まれていない、されませんが与えられていれば、ODBC ドライバーは、ユーザーから必要な情報を取得するダイアログ ボックスを表示設定`CDatabase::noOdbcDialog`または`CDatabase::forceOdbcDialog`で、 *dwOptions*パラメーター。 呼び出すと`OpenEx`、接続文字列、 *lpszConnectString*、プライベートに格納されている、`CDatabase`オブジェクトし、は、呼び出すことによって利用可能な[GetConnect](#getconnect)メンバー関数。

呼び出す前に、独自のダイアログ ボックスを開く場合は、`OpenEx`パスワードなど、ユーザーから情報を取得しに渡す接続文字列にその情報を追加する`OpenEx`します。 または、アプリケーション呼び出しの時間を節約できます再利用できるように、次を指定した接続文字列にする場合があります`OpenEx`上、`CDatabase`オブジェクト。

複数レベルのログイン認証の接続文字列を使用することもできます (それぞれ、別の`CDatabase`オブジェクト) またはその他のデータ ソースに固有の情報を伝達するためにします。 接続文字列の詳細についてで第 6 章を参照してください、 *ODBC プログラマ リファレンス*します。

これは、方法は、たとえば、DBMS ホストが使用できない場合は、接続の試行がタイムアウトする可能性があります。 接続の試行が失敗した場合、`OpenEx`スロー、`CDBException`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>  CDatabase::Rollback

トランザクション中に行われた変更を反転するには、このメンバー関数を呼び出します。

```
BOOL Rollback();
```

### <a name="return-value"></a>戻り値

0 以外の場合、トランザクションが正常に取り消された; 場合それ以外の場合 0 を返します。 場合、`Rollback`呼び出しに失敗した、データ ソースとトランザクションの状態が定義されていません。 場合`Rollback`0 を返しますの状態を決定するデータ ソースを確認する必要があります。

### <a name="remarks"></a>Remarks

すべて`CRecordset` `AddNew`、 `Edit`、 `Delete`、および`Update`実行された最後の呼び出し[BeginTrans](#begintrans)呼び出しの時点に存在していた状態にロールバックされます。

呼び出しの後に`Rollback`トランザクションが終了し、呼び出す必要があります、`BeginTrans`別のトランザクション用にもう一度です。 呼び出される前に対象だったレコード`BeginTrans`レコードになり、現在もう一度後`Rollback`します。

ロールバック後、ロールバック前に、の現在のレコードを最新の状態します。 レコード セットとロールバックした後、データ ソースの状態に関する詳細については、記事を参照してください。[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

### <a name="example"></a>例

  記事をご覧ください[トランザクション。レコード セット (ODBC) からのトランザクション実行](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)します。

##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout

このメンバー関数を呼び出すなどを呼び出す前に`OpenEx`または`Open`-ソース接続がタイムアウトを既定のデータの前に許容される秒数をオーバーライドします。

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>パラメーター

*dwSeconds*<br/>
接続試行する前に許可する秒数がタイムアウトになりました。

### <a name="remarks"></a>Remarks

接続の試行ではたとえば、DBMS が利用できない場合は、タイムアウトになる可能性があります。 呼び出す`SetLoginTimeout`、初期化されていないの構築後`CDatabase`オブジェクトしますが、呼び出す前に`OpenEx`または`Open`します。

ログイン タイムアウトの既定値は、15 秒です。 すべてのデータ ソースでは、ログイン タイムアウト値を指定する機能をサポートします。 データ ソースがタイムアウトをサポートしていない場合は、例外は発生しませんが、トレース出力を取得します。 値が 0 の場合"infinite"。

##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout

接続されているデータ ソースのタイムアウトで後続の操作の前に、秒の既定の数を上書きするには、このメンバー関数を呼び出します。

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>パラメーター

*dwSeconds*<br/>
クエリ試行する前に許可する秒数がタイムアウトになりました。

### <a name="remarks"></a>Remarks

操作は、ネットワーク アクセスの問題や、過剰なクエリ処理時間のためタイムアウト可能性があります。 呼び出す`SetQueryTimeout`またはレコード セットの前に、レコード セットを開く前に`AddNew`、`Update`または`Delete`メンバー関数をクエリのタイムアウト値を変更する場合。 この設定は、後続のすべての適用`Open`、 `AddNew`、 `Update`、および`Delete`これに関連付けられているすべてのレコード セットへの呼び出し`CDatabase`オブジェクト。 開いた後、レコード セットのクエリ タイムアウト値を変更しても、レコード セットの値は変わりません。 たとえば、後続`Move`操作では、新しい値を使用しないでください。

クエリ タイムアウトの既定値は、15 秒です。 すべてのデータ ソースでは、クエリのタイムアウト値を設定する機能をサポートします。 クエリのタイムアウト値は 0 を設定した場合のタイムアウトは行われません。データ ソースとの通信が応答を停止します。 この動作は、開発時に役立ちます。 データ ソースがタイムアウトをサポートしていない場合は、例外は発生しませんが、トレース出力を取得します。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)
