---
title: CDaoQueryDef クラス
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399747"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef クラス

クエリ定義、つまり "querydef" を表し、通常はデータベースに保存されています。

## <a name="syntax"></a>構文

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|`CDaoQueryDef` オブジェクトを構築します。 次に呼び出す`Open`または`Create`ニーズに応じて、します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDaoQueryDef::Append](#append)|データベースのクエリ定義のコレクションとして保存されたクエリには、クエリ定義を追加します。|
|[CDaoQueryDef::CanUpdate](#canupdate)|クエリは、データベースを更新できる場合、0 以外の値を返します。|
|[CDaoQueryDef::Close](#close)|クエリ定義のオブジェクトを閉じます。 これが完了したら、C++ オブジェクトを破棄します。|
|[CDaoQueryDef::Create](#create)|基になる DAO クエリ定義のオブジェクトを作成します。 クエリ定義を使用して、一時的なクエリ、または呼び出しとして`Append`データベースに保存します。|
|[CDaoQueryDef::Execute](#execute)|クエリ定義のオブジェクトによって定義されたクエリを実行します。|
|[CDaoQueryDef::GetConnect](#getconnect)|クエリ定義に関連付けられている接続文字列を返します。 接続文字列は、データ ソースを識別します。 (SQL のパススルー クエリのみ。 それ以外の場合、空の文字列です。)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|保存されたクエリが作成された日付を返します。|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|保存されたクエリの最終更新日を返します。|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|クエリ定義で定義されているフィールドの数を返します。|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|クエリで定義されている指定されたフィールドに関する情報を返します。|
|[CDaoQueryDef::GetName](#getname)|クエリ定義の名前を返します。|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|ODBC (ODBC クエリ) に対して使用するタイムアウト値を返すクエリを実行するとします。 これは、クエリの操作が完了するためにどのくらいの期間決定します。|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|クエリに定義されているパラメーターの数を返します。|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|クエリには、指定されたパラメーターに関する情報を返します。|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|クエリに指定されたパラメーターの値を返します。|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|アクション クエリによって影響を受けたレコードの数を返します。|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|クエリのクエリ定義で定義されているレコードを返す場合は 0 以外を返します。|
|[CDaoQueryDef::GetSQL](#getsql)|クエリ定義で定義されたクエリを指定する SQL 文字列を返します。|
|[CDaoQueryDef::GetType](#gettype)|クエリの種類を返します。 削除、更新、追加、テーブルを作成および具合です。|
|[CDaoQueryDef::IsOpen](#isopen)|クエリ定義が開いていて、実行できる場合は、0 以外の値を返します。|
|[CDaoQueryDef::Open](#open)|データベースのクエリ定義のコレクションに格納されている既存のクエリ定義を開きます。|
|[CDaoQueryDef::SetConnect](#setconnect)|ODBC データ ソースに対してパススルー クエリの接続文字列を設定します。|
|[CDaoQueryDef::SetName](#setname)|クエリ定義の作成時に使用されている名を置き換えて、保存されたクエリの名前を設定します。|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|ODBC (ODBC クエリ) に対して使用するタイムアウト値の設定、クエリを実行するとします。|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|クエリに指定されたパラメーターの値を設定します。|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|クエリ定義がレコードを返すかどうかを指定します。 この属性を TRUE に設定は、SQL パススルー クエリに対して有効ではのみです。|
|[CDaoQueryDef::SetSQL](#setsql)|クエリ定義で定義されたクエリを指定する SQL 文字列を設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|基になる DAO クエリ定義のオブジェクトの OLE インターフェイスへのポインター。|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|ポインター、`CDaoDatabase`クエリ定義が関連付けられているオブジェクト。 かどうか、クエリ定義をデータベースに保存可能性があります。|

## <a name="remarks"></a>Remarks

クエリ定義は、クエリ、および「作成日」や「ODBC タイムアウトします」など、そのプロパティを記述した SQL ステートメントを含むデータ アクセス オブジェクト 保存せずに、一時的なクエリ定義のオブジェクトを作成することもできますが、便利な- と非常に効率的-よくを保存するには、データベース内のクエリを再利用します。 A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクトは、その保存したクエリ定義が含まれています QueryDefs コレクションと呼ばれる、コレクションを保持します。

> [!NOTE]
>  DAO データベース クラスは、ベースの開いているデータベースの接続 (ODBC) で MFC データベース クラスとは異なります。 DAO データベース クラスの名前には、"CDao"プレフィックスが付いています。 DAO クラスで ODBC データ ソースのアクセスできます。 一般に、DAO に基づいて MFC クラスは ODBC; に基づいて MFC クラスよりもより高機能ですDAO ベースのクラスは、独自のデータベース エンジンを使用して、ODBC ドライバーを含む、データにアクセスできます。 DAO ベースのクラスには、DAO を直接呼び出すことがなく、クラスを使用してテーブルの追加などのデータ定義言語 (DDL) 操作もサポートします。

## <a name="usage"></a>使用法

クエリ定義のオブジェクトのいずれも使用または新たに作成する保存済みのクエリを使用するクエリまたは一時的なクエリを保存します。

1. すべての場合、最初に構築、`CDaoQueryDef`へのポインターを提供する、オブジェクト、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)クエリが属しているオブジェクトします。

1. 目的に応じて、次を実行します。

   - 保存済みのクエリを使用するには、クエリ定義オブジェクトを呼び出す[オープン](#open)保存されたクエリの名前を指定して、メンバー関数。

   - 新しい保存されたクエリを作成するには、クエリ定義オブジェクトを呼び出す[作成](#create)メンバー関数は、クエリの名前を指定します。 呼び出して[Append](#append)データベースのクエリ定義のコレクションに追加して、クエリを保存します。 `Create` クエリ定義では、開いている状態を呼び出した後は`Create`呼び出さないでください`Open`します。

   - 一時的なクエリ定義を作成するには`Create`します。 クエリ名に空の文字列を渡します。 `Append` を呼び出さないでください。

クエリ定義オブジェクトの使用が完了したらを呼び出すその[閉じる](#close)メンバー関数です。 は、クエリ定義のオブジェクトを破棄します。

> [!TIP]
>  保存されたクエリを作成する最も簡単な方法では、それらを作成し、Microsoft Access を使用して、データベースに保存します。 開くでき、MFC コード内で使用できます。

## <a name="purposes"></a>目的

次の目的のいずれかのクエリ定義のオブジェクトを使用できます。

- 作成する、`CDaoRecordset`オブジェクト

- オブジェクトの呼び出しに`Execute`アクション クエリまたは SQL パススルー クエリを直接実行するメンバー関数

Select、アクション、クロス集計、削除、更新プログラムを含めて、クエリの任意の型のクエリ定義のオブジェクトを使用し、追加、テーブルの作成、データ定義、SQL パススルー、共用体、一括クエリできます。 クエリの種類については、指定した SQL ステートメントの内容によって決まります。 クエリの種類については、次を参照してください。、`Execute`と[GetType](#gettype)メンバー関数。 レコード セットは行を返すのよく使用されるクエリは、通常を使用して、**を選択しています.** キーワード。 `Execute` 一括操作の最もよく使用されます。 詳細については、次を参照してください。 [Execute](#execute)と[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)します。

## <a name="querydefs-and-recordsets"></a>クエリ定義とレコード セット

クエリ定義のオブジェクトを使用して作成する、`CDaoRecordset`オブジェクトを通常、作成または前述のように、クエリ定義を開きます。 呼び出すときに、クエリ定義のオブジェクトにポインターを渡すこと、レコード セット オブジェクトを構築し、 [cdaorecordset::open](../../mfc/reference/cdaorecordset-class.md#open)します。 渡すクエリ定義は、開いている状態でなければなりません。 詳細については、クラスを参照してください。 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)します。

クエリ定義を使用して、開いている状態である場合を除き、レコード セット (最も一般的なクエリ定義の使用) を作成することはできません。 いずれかを呼び出すことによって、クエリ定義を開いている状態に`Open`または`Create`します。

## <a name="external-databases"></a>外部データベース

クエリ定義のオブジェクトは、外部データベース エンジンのネイティブの SQL 構文を使用することをお勧めします。 たとえば、(Microsoft SQL Server で使用) と Transact SQL クエリを作成でき、クエリ定義のオブジェクトに格納できます。 Microsoft Jet データベース エンジンに基づいていない SQL クエリを使用する必要がある場合は、外部データ ソースを指す接続文字列を指定する必要があります。 有効な接続文字列を使用したクエリはデータベース エンジンをバイパスし、処理用の外部のデータベース サーバーに直接クエリを渡します。

> [!TIP]
>  ODBC テーブルの操作の推奨される方法は、Microsoft Jet に添付すること (します。MDB) データベース。

関連情報については、「QueryDef オブジェクト」、「QueryDefs コレクション」および DAO SDK の「CdbDatabase オブジェクト」のトピックを参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

##  <a name="append"></a>  CDaoQueryDef::Append

呼び出した後に、このメンバー関数を呼び出す[作成](#create)新しいクエリ オブジェクトを作成します。

```
virtual void Append();
```

### <a name="remarks"></a>Remarks

`Append` データベースのクエリ定義のコレクションにオブジェクトを追加することによって、データベースのクエリ定義を保存します。 それを付加せず、一時オブジェクトとしてクエリ定義を使用できますが、呼び出す必要がある場合は、これを保存する`Append`します。

MFC が型の例外をスローする場合は、一時的なクエリ定義のオブジェクトを追加しようとすると、 [CDaoException](../../mfc/reference/cdaoexception-class.md)します。

##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate

クエリ定義を変更できるかどうかを判断するには、このメンバー関数を呼び出すなどの名前または SQL 文字列を変更するなど。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>戻り値

クエリ定義を変更する権限がある場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

場合は、クエリ定義を変更できます。

- 読み取り専用で開かれているデータベースに基づきません。

- データベースに対する更新アクセス許可があります。

   これは、セキュリティ機能を実装するかどうかによって異なります。 MFC ではセキュリティのサポートはされていません必要があります、自分で実装を直接に DAO を呼び出すか、Microsoft Access を使用しています。 「アクセス許可のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef

`CDaoQueryDef` オブジェクトを構築します。

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>パラメーター

*pDatabase*<br/>
開いているへのポインター [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

オブジェクトは、データベースのクエリ定義のコレクション、コレクションに格納される新しいクエリまたは格納しないようにの一時的なクエリに格納されている既存のクエリ定義を表すことができます。 次の手順は、クエリ定義の種類によって異なります。

- オブジェクトは、既存のクエリ定義を表している場合は、オブジェクトを呼び出す[オープン](#open)メンバー関数を初期化します。

- オブジェクトを保存する新しいクエリ定義を表している場合は、オブジェクトを呼び出す[作成](#create)メンバー関数。 これにより、オブジェクトがデータベースのクエリ定義のコレクションに追加します。 呼び出して`CDaoQueryDef`メンバー関数、オブジェクトの属性を設定します。 最後に、呼び出す[Append](#append)します。

- オブジェクトは、一時的なクエリ定義 (データベースに保存しない) を表している場合は、呼び出す`Create`クエリの名前の空の文字列を渡します。 呼び出した後`Create`、直接その属性を設定して、クエリ定義を初期化します。 `Append` を呼び出さないでください。

クエリ定義の属性を設定するには、使用することができます、 [SetName](#setname)、 [SetSQL](#setsql)、 [SetConnect](#setconnect)、[に](#setodbctimeout)、および[SetReturnsRecords](#setreturnsrecords)メンバー関数。

呼び出すクエリ定義のオブジェクトが完了したら、その[閉じる](#close)メンバー関数。 クエリ定義へのポインターがある場合は、使用、**削除**C++ オブジェクトを破棄する演算子。

##  <a name="close"></a>  CDaoQueryDef::Close

クエリ定義のオブジェクトの使用が終わったときに、このメンバー関数を呼び出します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

基になる DAO オブジェクトを解放クエリ定義を終了しますが、保存された DAO クエリ定義オブジェクトまたは C++ 破棄しません`CDaoQueryDef`オブジェクト。 同じです。 これはいない[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)、DAO (ない場合は一時的なクエリ定義) で、データベースのクエリ定義のコレクションから、クエリ定義を削除します。

##  <a name="create"></a>  CDaoQueryDef::Create

新しい保存されたクエリまたは新しい一時的なクエリを作成するには、このメンバー関数を呼び出します。

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
データベースに保存されたクエリの一意の名前。 詳細については、文字列は、DAO のヘルプで「CreateQueryDef メソッド」を参照してください。 既定値、空の文字列を使用する場合は、一時的なクエリ定義が作成されます。 このようなクエリは、クエリ定義のコレクションには保存されません。

*lpszSQL*<br/>
クエリを定義する SQL 文字列です。 後で呼び出す必要がある場合は、既定値は NULL に同意した[SetSQL](#setsql)文字列を設定します。 それまでは、クエリは定義されません。 ただしはレコード セットを開くに未定義のクエリを使用することができます。詳細については、「解説」を参照してください。 QueryDefs コレクションにクエリ定義を追加する前に、SQL ステートメントを定義する必要があります。

### <a name="remarks"></a>Remarks

内の名前を渡す場合*lpszName*を呼び出して[Append](#append)データベースのクエリ定義のコレクションにクエリ定義を保存します。 それ以外の場合、オブジェクトは一時的なクエリ定義では保存されません。 いずれかの場合も、クエリ定義は、開いている状態では、作成に使用できる、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトまたはクエリ定義の[Execute](#execute)メンバー関数。

SQL ステートメントを指定しない場合*lpszSQL*を使用してクエリを実行することはできません`Execute`が、これを使用するにはレコード セットを作成します。 その場合は、MFC は、レコード セットの既定の SQL ステートメントを使用します。

##  <a name="execute"></a>  CDaoQueryDef::Execute

クエリ定義のオブジェクトによって定義されたクエリを実行するには、このメンバー関数を呼び出します。

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>パラメーター

*nOptions*<br/>
クエリの特性を決定する整数。 関連情報については、DAO ヘルプの「メソッドの実行」トピックを参照してください。 ビットごとの OR 演算子を使用することができます ( **&#124;**) この引数は、次の定数を結合します。

- `dbDenyWrite` 他のユーザーに書き込みアクセス許可を拒否します。

- `dbInconsistent` 更新プログラムの一貫性がありません。

- `dbConsistent` 一貫性のある更新します。

- `dbSQLPassThrough` SQL パススルーします。 処理のために、ODBC データベースに渡される SQL ステートメントをによりします。

- `dbFailOnError` 既定値です。 ロールバック エラーが発生した場合の更新プログラムと、エラー レポートをユーザーにします。

- `dbSeeChanges` 別のユーザーが編集してデータを変更する場合は、実行時エラーを生成します。

> [!NOTE]
>  用語の説明「一貫性のない」と「一貫性」DAO ヘルプの「メソッドの実行」トピックを参照してください。

### <a name="remarks"></a>Remarks

この方法で実行するために使用されるクエリ定義オブジェクトを次のクエリの型の 1 つのみ表現できます。

- アクションのクエリ

- SQL パススルー クエリ

`Execute` select クエリなど、レコードを返すクエリに対しては機能しません。 `Execute` など使用一括操作のクエリでは、よく**UPDATE**、**挿入**、または**SELECT INTO**、またはデータ定義言語 (DDL) 操作。

> [!TIP]
>  ODBC データ ソースを操作することをお勧めの Microsoft Jet にテーブルをアタッチする (します。MDB) データベース。 詳細については、"にアクセスする外部のデータベースと DAO"DAO ヘルプのトピックを参照してください。

呼び出す、 [GetRecordsAffected](#getrecordsaffected)最新によって影響を受けたレコードの数を決定するクエリ定義オブジェクトのメンバー関数`Execute`呼び出します。 たとえば、`GetRecordsAffected`削除、更新、またはアクションのクエリを実行するときに挿入されるレコードの数に関する情報を返します。 返されるカウントが cascade を更新または削除時に、関連テーブルの変更が有効では反映されません。

両方を含めた場合`dbInconsistent`と`dbConsistent`、結果は、既定で含める場合はどちらも、または`dbInconsistent`します。

`Execute` レコード セットは返されません。 使用して`Execute`レコードを選択するクエリに MFC の種類の例外をスローすると、 [CDaoException](../../mfc/reference/cdaoexception-class.md)します。

##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect

クエリ定義のデータ ソースに関連付けられた接続文字列を取得するには、このメンバー関数を呼び出します。

```
CString GetConnect();
```

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)クエリ定義の接続文字列を格納しています。

### <a name="remarks"></a>Remarks

この関数は、ODBC データ ソースと特定の ISAM ドライバーでのみ使用されます。 Microsoft Jet では使用されません (します。MDB) データベース。この場合、`GetConnect`空の文字列を返します。 詳細については、次を参照してください。 [SetConnect](#setconnect)します。

> [!TIP]
>  ODBC テーブルを使用することをお勧めが接続先にするには、します。MDB データベースです。 詳細については、"にアクセスする外部のデータベースと DAO"DAO ヘルプのトピックを参照してください。

接続文字列については、DAO のヘルプ「プロパティの接続」を参照してください。

##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated

クエリ定義のオブジェクトが作成された日付を取得するには、このメンバー関数を呼び出します。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>戻り値

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)クエリ定義が作成された日時を含むオブジェクト。

### <a name="remarks"></a>Remarks

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated

最終更新時刻、日付のクエリ定義のオブジェクトを取得するには、このメンバー関数の呼び出し、そのプロパティのいずれかが変更されたとき、その名前、SQL 文字列、または接続文字列など。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>戻り値

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)クエリ定義が最後に更新された日時を含むオブジェクト。

### <a name="remarks"></a>Remarks

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount

クエリのフィールドの数を取得するには、このメンバー関数を呼び出します。

```
short GetFieldCount();
```

### <a name="return-value"></a>戻り値

クエリで定義されているフィールドの数。

### <a name="remarks"></a>Remarks

`GetFieldCount` クエリ定義のすべてのフィールドをループに役立ちます。 そのために、使用`GetFieldCount`と共に[GetFieldInfo](#getfieldinfo)します。

##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo

さまざまな種類のクエリ定義で定義されているフィールドに関する情報を取得するには、このメンバー関数を呼び出します。

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスで検索する場合、クエリ定義のフィールド コレクションで目的のフィールドの 0 から始まるインデックス。

*fieldinfo*<br/>
参照を`CDaoFieldInfo`オブジェクトを要求された情報を返します。

*dwInfoOptions*<br/>
取得するフィールドに関する情報を指定するオプション。 使用可能なオプションを返す関数が何とここは。

- AFX_DAO_PRIMARY_INFO (既定値) の名前、種類、サイズ、属性

- プラス AFX_DAO_SECONDARY_INFO プライマリ情報:必要に応じて、序数の位置 0 の長さ、ソース フィールド、外部名、ソース テーブル、照合順序を許可します。

- AFX_DAO_ALL_INFO プライマリとセカンダリの情報に加えて:既定値、入力テキスト、検証規則

*lpszName*<br/>
名前で検索の目的のフィールドの名前を含む文字列。 使用することができます、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)します。

### <a name="remarks"></a>Remarks

返される情報の説明については*fieldinfo*を参照してください、 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。 この構造体は、わかりやすい情報に対応するメンバー *dwInfoOptions*上。 1 つのレベルの情報を要求すると、その情報も同様のレベルを取得します。

##  <a name="getname"></a>  CDaoQueryDef::GetName

クエリ定義によって表されるクエリの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetName();
```

### <a name="return-value"></a>戻り値

クエリ名を返します。

### <a name="remarks"></a>Remarks

クエリ定義名は一意のユーザー定義の名前です。 クエリ定義名の詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout

ODBC データ ソースへのクエリがタイムアウトするまで、現在の制限時間を取得するには、このメンバー関数を呼び出します。

```
short GetODBCTimeout();
```

### <a name="return-value"></a>戻り値

タイムアウトをクエリするまでの秒数。

### <a name="remarks"></a>Remarks

この制限時間については、DAO ヘルプの「補足プロパティ」を参照してください。

> [!TIP]
>  ODBC テーブルの操作の推奨される方法は、Microsoft Jet に添付すること (します。MDB) データベース。 詳細については、"にアクセスする外部のデータベースと DAO"DAO ヘルプのトピックを参照してください。

##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount

保存されたクエリのパラメーターの数を取得するには、このメンバー関数を呼び出します。

```
short GetParameterCount();
```

### <a name="return-value"></a>戻り値

クエリで定義されたパラメーターの数。

### <a name="remarks"></a>Remarks

`GetParameterCount` クエリ定義のすべてのパラメーターをループに役立ちます。 そのために、使用`GetParameterCount`と共に[GetParameterInfo](#getparameterinfo)します。

関連情報については、「パラメーター オブジェクト」、「Parameters コレクション」および"パラメーターの宣言 (SQL)"DAO ヘルプのトピックを参照してください。

##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo

クエリ定義で定義されているパラメーターに関する情報を取得するには、このメンバー関数を呼び出します。

```
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスで検索する場合、クエリ定義のパラメーター コレクションで目的のパラメーターの 0 から始まるインデックス。

*パラメーター情報*<br/>
参照を[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)オブジェクトを要求された情報を返します。

*dwInfoOptions*<br/>
取得するパラメーターに関する情報を指定するオプション。 利用可能なオプションは、原因は何を返す関数と共にとおりです。

- AFX_DAO_PRIMARY_INFO (既定値) の名前、型

*lpszName*<br/>
名前で検索の目的のパラメーターの名前を含む文字列。 使用することができます、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)します。

### <a name="remarks"></a>Remarks

返される情報の説明については*paraminfo*を参照してください、 [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)構造体。 この構造体は、わかりやすい情報に対応するメンバー *dwInfoOptions*上。

関連情報については、"パラメーターの宣言 (SQL)"DAO ヘルプのトピックを参照してください。

##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue

クエリ定義のパラメーターのコレクションに格納されている指定されたパラメーターの現在の値を取得するには、このメンバー関数を呼び出します。

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
パラメーターの名前で検索値の名前。

*nIndex*<br/>
インデックスで検索する場合、クエリ定義のパラメーター コレクション内のパラメーターの 0 から始まるインデックス。 呼び出すには、この値を取得できます[GetParameterCount](#getparametercount)と[GetParameterInfo](#getparameterinfo)します。

### <a name="return-value"></a>戻り値

クラスのオブジェクト[COleVariant](../../mfc/reference/colevariant-class.md)パラメーターの値を格納しています。

### <a name="remarks"></a>Remarks

パラメーター名、またはコレクションの序数位置を使用してアクセスできます。

関連情報については、"パラメーターの宣言 (SQL)"DAO ヘルプのトピックを参照してください。

##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected

最後の呼び出しの影響を受けたレコードの数を判断するには、このメンバー関数を呼び出す[Execute](#execute)します。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>戻り値

影響を受けたレコードの数。

### <a name="remarks"></a>Remarks

返されるカウントが cascade を更新または削除時に、関連テーブルの変更が有効では反映されません。

関連情報については、「RecordsAffected プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords

クエリ定義をレコードを返すクエリに基づいているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>戻り値

レコードを返すクエリ定義がクエリに基づいている場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、SQL パススルー クエリに対してのみ使用されます。 SQL クエリの詳細については、次を参照してください。、 [Execute](#execute)メンバー関数。 SQL パススルー クエリと操作の詳細については、次を参照してください。、 [SetReturnsRecords](#setreturnsrecords)メンバー関数。

関連情報については、「レコード表示プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getsql"></a>  CDaoQueryDef::GetSQL

クエリ定義の基になるクエリを定義する SQL ステートメントを取得するには、このメンバー関数を呼び出します。

```
CString GetSQL();
```

### <a name="return-value"></a>戻り値

クエリ定義の基になるクエリを定義する SQL ステートメント。

### <a name="remarks"></a>Remarks

キーワードや、テーブル名の文字列をおそらく解析されます。

関連情報については、"SQL Property"、"比較の Microsoft Jet データベース エンジン SQL と ANSI SQL"、および「クエリを実行する、データベースを SQL でコード」DAO ヘルプのトピックを参照してください。

##  <a name="gettype"></a>  CDaoQueryDef::GetType

クエリ定義のクエリの種類を判断するには、このメンバー関数を呼び出します。

```
short GetType();
```

### <a name="return-value"></a>戻り値

クエリ定義で定義されたクエリの型。 値は、「解説」を参照してください。

### <a name="remarks"></a>Remarks

クエリの種類はどのような文字列に指定したクエリ定義の SQL クエリを作成するか、既存のクエリ定義のによって設定されます[SetSQL](#setsql)メンバー関数。 この関数によって返されるクエリの種類には、次の値のいずれかを指定できます。

- `dbQSelect` 選択します

- `dbQAction` 動作

- `dbQCrosstab` クロス集計

- `dbQDelete` Delete

- `dbQUpdate` 更新プログラム

- `dbQAppend` 追加

- `dbQMakeTable` テーブルな作成

- `dbQDDL` データ定義

- `dbQSQLPassThrough` パススルー

- `dbQSetOperation` 共用体

- `dbQSPTBulk` 併用`dbQSQLPassThrough`クエリ レコードは返されませんを指定します。

> [!NOTE]
>  SQL パススルー クエリを作成するに設定しないでください、`dbSQLPassThrough`定数。 これは自動的に設定、Microsoft Jet データベース エンジンによってクエリ定義のオブジェクトを作成し、接続文字列を設定します。

SQL 文字列については、次を参照してください。 [GetSQL](#getsql)します。 クエリの種類については、次を参照してください。 [Execute](#execute)します。

##  <a name="isopen"></a>  CDaoQueryDef::IsOpen

確認するには、このメンバー関数を呼び出すかどうか、`CDaoQueryDef`オブジェクトが現在開いています。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

0 以外の値、`CDaoQueryDef`オブジェクトが現在開いている場合は 0 それ以外の場合。

### <a name="remarks"></a>Remarks

クエリ定義は、呼び出しに使用する前に、開いている状態である必要があります[Execute](#execute)を作成したり、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクト。 か、開いている状態の呼び出しにクエリ定義を格納する[作成](#create)(新しいクエリを定義) のまたは[開く](#open)(の既存のクエリ定義)。

##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase

ポインターが含まれています、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)クエリ定義のオブジェクトに関連付けられたオブジェクト。

### <a name="remarks"></a>Remarks

データベースに直接アクセスする必要がある場合は、このポインターを使用して — たとえば、他のクエリ定義またはレコード セットへのポインターを取得するデータベースのコレクションでオブジェクトします。

##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef

基になる DAO クエリ定義のオブジェクトの OLE インターフェイスへのポインターが含まれています。

### <a name="remarks"></a>Remarks

このポインターは、完全性とその他のクラスとの整合性に対して提供されます。 ただし、MFC には、DAO のクエリ定義ではなく完全にカプセル化するためが必要になる可能性があることはできません。 使用する場合は注意: この操作はわかっている場合を除き、ポインターの値を変更して具体的には、します。

##  <a name="open"></a>  CDaoQueryDef::Open

データベースのクエリ定義のコレクションに保存したクエリ定義を開くには、このメンバー関数を呼び出します。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
開く、保存されたクエリ定義の名前を含む文字列。 使用することができます、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)します。

### <a name="remarks"></a>Remarks

呼び出すことができます、クエリ定義が開いたら、その[Execute](#execute)メンバー関数または作成するクエリを使用して、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクト。

##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect

クエリ定義オブジェクトの接続文字列を設定するには、このメンバー関数を呼び出します。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>パラメーター

*lpszConnect*<br/>
関連付けられている接続文字列を含む文字列[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

接続文字列は、ODBC および必要に応じて、特定の ISAM ドライバーに追加情報を渡す使用されます。 Microsoft Jet 用は使用されません (します。MDB) データベース。

> [!TIP]
>  ODBC テーブルを使用することをお勧めが接続先にするには、します。MDB データベースです。

ODBC データ ソースへの SQL パススルー クエリを表すクエリを実行する前に設定された接続文字列で`SetConnect`を呼び出すと[SetReturnsRecords](#setreturnsrecords)クエリがレコードを返すかどうかを指定します。

詳細については、接続文字列の構造との接続文字列コンポーネントの例については、DAO のヘルプ「プロパティの接続」を参照してください。

##  <a name="setname"></a>  CDaoQueryDef::SetName

一時的でないクエリ定義の名前を変更する場合は、このメンバー関数を呼び出します。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
関連付けられている nontemporary クエリの新しい名前を含む文字列[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

クエリ定義名は、ユーザー定義の一意の名前です。 呼び出すことができます`SetName`クエリを定義する前に、オブジェクトがクエリ定義のコレクションに追加されます。

##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout

ODBC データ ソースへのクエリがタイムアウトするまでに時間制限を設定するには、このメンバー関数を呼び出します。

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>パラメーター

*nODBCTimeout*<br/>
タイムアウトをクエリするまでの秒数。

### <a name="remarks"></a>Remarks

このメンバー関数では、「タイムアウト」接続されているデータ ソースに対する後続の処理までの秒数の既定をオーバーライドできます。 操作は、ネットワーク アクセスの問題や、過剰なクエリ処理時間のためタイムアウト可能性があります。 呼び出す`SetODBCTimeout`クエリ タイムアウト値を変更する場合は、このクエリの定義を持つクエリを実行する前にします。 (ODBC 接続を再利用とタイムアウト値は、同じ接続上のすべてのクライアントに対して同じ) です。

クエリ タイムアウトの既定値は、60 秒です。

##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue

実行時に、クエリ定義でパラメーターの値を設定するには、このメンバー関数を呼び出します。

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
値を設定するパラメーターの名前。

*varValue*<br/>
値を設定します。「解説」を参照してください。

*nIndex*<br/>
クエリ定義のパラメーター コレクション内のパラメーターの序数位置。 呼び出すには、この値を取得できます[GetParameterCount](#getparametercount)と[GetParameterInfo](#getparameterinfo)します。

### <a name="remarks"></a>Remarks

パラメーターは、クエリ定義の SQL 文字列の一部として確立するが既に必要があります。 パラメーター名、またはコレクションの序数位置を使用してアクセスできます。

として設定する値を指定する`COleVariant`オブジェクト。 目的の値と型の設定については、`COleVariant`オブジェクト、クラスを参照してください。 [COleVariant](../../mfc/reference/colevariant-class.md)します。

##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords

外部データベースに SQL パススルー クエリの設定のプロセスの一環として、このメンバー関数を呼び出します。

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>パラメーター

*bReturnsRecords*<br/>
外部データベースにクエリがレコードを返す場合に TRUE を渡すそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このような場合は、クエリ定義を作成し、他を使用してそのプロパティを設定`CDaoQueryDef`メンバー関数。 外部データベースについては、次を参照してください。 [SetConnect](#setconnect)します。

##  <a name="setsql"></a>  CDaoQueryDef::SetSQL

クエリを実行する SQL ステートメントを設定するには、このメンバー関数を呼び出します。

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>パラメーター

*lpszSQL*<br/>
実行に適した完全な SQL ステートメントを含む文字列。 この文字列の構文は、DBMS に依存する、クエリの対象とします。 Microsoft Jet データベース エンジンで使用される構文の詳細については、「作成 SQL ステートメントでコード」DAO ヘルプのトピックを参照してください。

### <a name="remarks"></a>Remarks

一般的な使用`SetSQL`パススルーの SQL クエリで使用するためのクエリ定義オブジェクトを設定します。 (対象となる DBMS 上の SQL パススルー クエリの構文、DBMS のマニュアルを参照してください)。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset クラス](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef クラス](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException クラス](../../mfc/reference/cdaoexception-class.md)
