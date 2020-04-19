---
title: CDaoTableDef クラス
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151221"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef クラス

ベース テーブル、またはアタッチ テーブルの格納された定義を表現します。

## <a name="syntax"></a>構文

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|`CDaoTableDef` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|データベースを新しいテーブルを追加します。|
|[CDaoTableDef::CanUpdate](#canupdate)|テーブルを更新する場合は 0 以外を返します (フィールドやテーブルのプロパティの定義を変更することができます)。|
|[CDaoTableDef::Close](#close)|オープンのテーブル定義を閉じます。|
|[CDaoTableDef::Create](#create)|使用して、データベースに追加できるテーブルを作成します。 [Append](#append)します。|
|[CDaoTableDef::CreateField](#createfield)|テーブルのフィールドを作成するには、呼び出されます。|
|[CDaoTableDef::CreateIndex](#createindex)|テーブルのインデックスを作成するには、呼び出されます。|
|[CDaoTableDef::DeleteField](#deletefield)|テーブルからフィールドを削除するには、呼び出されます。|
|[CDaoTableDef::DeleteIndex](#deleteindex)|テーブルからインデックスを削除するには、呼び出されます。|
|[CDaoTableDef::GetAttributes](#getattributes)|1 つまたは複数の特性を示す値を返します、`CDaoTableDef`オブジェクト。|
|[CDaoTableDef::GetConnect](#getconnect)|テーブルのソースに関する情報を示す値を返します。|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|基になるベース テーブルの日付と時刻を返します、`CDaoTableDef`オブジェクトが作成されました。|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|ベース テーブルのデザインに加えられた最新の変更の日時を返します。|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|テーブル内のフィールドの数を表す値を返します。|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|テーブルの特定の種類のフィールドの詳細についての情報を返します。|
|[CDaoTableDef::GetIndexCount](#getindexcount)|テーブルのインデックスの数を返します。|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|特定の種類のテーブルのインデックスに関する情報を返します。|
|[CDaoTableDef::GetName](#getname)|ユーザー定義テーブルの名前を返します。|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|テーブルのレコードの数を返します。|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|ソース データベースに接続されているテーブルの名前を指定する値を返します。|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|変更されたか、テーブルに追加するフィールドのデータを検証する値を返します。|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|フィールド オブジェクトの値が指定した検証規則を満たしていない場合、アプリケーションで表示されるメッセージのテキストを指定する値を返します。|
|[CDaoTableDef::IsOpen](#isopen)|テーブルの場合、0 以外の値を返しますが開きます。|
|[CDaoTableDef::Open](#open)|開き、データベースに格納されている既存のテーブル定義のテーブル定義のコレクションです。|
|[CDaoTableDef::RefreshLink](#refreshlink)|接続されたテーブルの接続情報を更新します。|
|[CDaoTableDef::SetAttributes](#setattributes)|1 つまたは複数の特性を示す値を設定、`CDaoTableDef`オブジェクト。|
|[CDaoTableDef::SetConnect](#setconnect)|テーブルのソースに関する情報を提供する値を設定します。|
|[CDaoTableDef::SetName](#setname)|テーブルの名前を設定します。|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|ソース データベースに接続されたテーブルの名前を指定する値を設定します。|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|変更されたか、テーブルに追加するフィールドのデータを検証する値を設定します。|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|フィールド オブジェクトの値が指定した検証規則を満たしていない場合、アプリケーションで表示されるメッセージのテキストを指定する値を設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|テーブル定義のオブジェクトを基になる DAO インターフェイスへのポインター。|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|このテーブルのソース データベースです。|

## <a name="remarks"></a>Remarks

DAO データベースの各オブジェクトは、保存されているすべての DAO テーブル定義のオブジェクトを含むテーブル定義と呼ばれる、コレクションを保持します。

使用してテーブル定義を操作する、`CDaoTableDef`オブジェクト。 たとえば、次のように操作できます。

- データベース内の任意のローカル、接続されている、または外部テーブルのフィールドおよびインデックスの構造を調べます。

- 呼び出す、`SetConnect`と`SetSourceTableName`使用して接続されているテーブルは、メンバー関数、`RefreshLink`メンバー関数への接続を更新するには、テーブルが接続されています。

- 呼び出す、`CanUpdate`かどうかは、テーブル内のフィールド定義を編集することができますを調べます。

- 取得または設定を使用して検証条件、`GetValidationRule`と`SetValidationRule`、および`GetValidationText`と`SetValidationText`メンバー関数。

- 使用して、`Open`テーブル タイプ、ダイナセット部、またはスナップショットの種類を作成するメンバー関数`CDaoRecordset`オブジェクト。

    > [!NOTE]
    >  DAO データベース クラスは、ベースの開いているデータベースの接続 (ODBC) で MFC データベース クラスとは異なります。 DAO データベース クラスの名前には、"CDao"プレフィックスが付いています。 DAO クラス; で ODBC データ ソースのアクセスをできます。DAO クラスは、一般には、Microsoft Jet データベース エンジンに固有であるため、優れた機能の機能を提供します。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>既存のテーブルを操作するか、新しいテーブルを作成するテーブル定義のオブジェクトを使用するには

1. すべての場合、最初に構築、`CDaoTableDef`へのポインターを提供する、オブジェクト、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)テーブルが所属するオブジェクトします。

1. 目的に応じて、次を実行します。

   - 既存のテーブルの名前を使用する呼び出し定義オブジェクトの[オープン](#open)保存されているテーブルの名前を指定して、メンバー関数。

   - 新しいテーブルを作成するには、定義オブジェクトを呼び出す[作成](#create)テーブルの名前を指定して、メンバー関数。 呼び出す[CreateField](#createfield)と[CreateIndex](#createindex)フィールドおよびインデックスをテーブルに追加します。

   - 呼び出す[Append](#append)データベースのテーブル定義のコレクションに追加して、テーブルを保存します。 `Create` テーブル定義では、開いている状態を呼び出した後は`Create`呼び出さないでください`Open`します。

        > [!TIP]
        >  保存されているテーブルを作成する最も簡単な方法では、それらを作成し、Microsoft Access を使用して、データベースに保存します。 開くでき、MFC コード内で使用できます。

テーブル定義のオブジェクトを開くか作成を使用する作成して開く、`CDaoRecordset`でテーブル定義の名前を指定する、オブジェクト、`dbOpenTable`値、*できるかどうか*パラメーター。

テーブル定義のオブジェクトを使用して作成する、`CDaoRecordset`オブジェクトを通常を作成または、前述のようにテーブル定義を開きし、レコード セット オブジェクトを作成するには、呼び出すときに、テーブル定義のオブジェクトにポインターを渡すこと[cdaorecordset::open](../../mfc/reference/cdaorecordset-class.md#open)します。 渡すテーブル定義は、開いている状態でなければなりません。 詳細については、クラスを参照してください。 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)します。

テーブル定義オブジェクトの使用が完了したらを呼び出すその[閉じる](../../mfc/reference/cdaorecordset-class.md#close)メンバー関数です。 は、テーブル定義のオブジェクトを破棄します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

呼び出した後に、このメンバー関数を呼び出す[作成](#create)データベースにテーブル定義を保存する新しいテーブル定義オブジェクトを作成します。

```
virtual void Append();
```

### <a name="remarks"></a>Remarks

関数では、データベースのテーブル定義のコレクションにオブジェクトを追加します。 されませんが、追加することでそれを定義する際に一時オブジェクトとして、テーブル定義を使用できますが、保存を使用する場合を呼び出す必要があります`Append`します。

> [!NOTE]
>  (Null または空の文字列を含む)、名前のないテーブルの定義を追加しようとすると、MFC は、例外をスローします。

関連情報については、「DAO ヘルプの「メソッドの追加」」を参照してください。

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

確認するには、このメンバー関数を呼び出すかどうか基になるテーブルの定義、`CDaoTableDef`オブジェクトを変更することができます。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>戻り値

テーブルの構造 (スキーマ) を変更できる場合は 0 以外 (追加またはフィールドおよびインデックスの削除)、それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

既定では、基になるテーブルを新しく作成された、`CDaoTableDef`オブジェクトを更新するには、基になる、関連付けられているテーブルと、`CDaoTableDef`オブジェクトを更新することはできません。 A`CDaoTableDef`結果のレコード セットは更新可能でない場合でも、オブジェクトが更新可能なする可能性があります。

関連情報については、「DAO ヘルプの「更新可能なプロパティ」」を参照してください。

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

`CDaoTableDef` オブジェクトを構築します。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>パラメーター

*pDatabase*<br/>
ポインターを[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

オブジェクトを構築後に呼び出す必要がある、[作成](#create)または[オープン](#open)メンバー関数。 呼び出す必要がある場合、オブジェクトが完了したら、その[閉じる](#close)メンバー関数し、破棄、`CDaoTableDef`オブジェクト。

##  <a name="close"></a>  CDaoTableDef::Close

閉じるし、テーブル定義のオブジェクトを解放するには、このメンバー関数を呼び出します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

通常は後で呼び出す`Close`で割り当てられた場合は、テーブル定義のオブジェクトを削除する**新しい**します。

呼び出すことができます[オープン](#open)呼び出した後でもう一度`Close`します。 これにより、テーブル定義のオブジェクトを再利用できます。

関連情報については、「Close メソッド」DAO ヘルプのトピックを参照してください。

##  <a name="create"></a>  CDaoTableDef::Create

保存されている新しいテーブルを作成するには、このメンバー関数を呼び出します。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
テーブルの名前を含む文字列へのポインター。

*lAttributes*<br/>
テーブル定義のオブジェクトによって表されるテーブルの特性に対応する値。 ビットごとの OR を使用して、次の定数のいずれかを結合できます。

|定数|説明|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet データベース エンジンを使用するデータベースの場合は、排他的に開かれて、接続されているテーブルを示します。|
|`dbAttachSavePWD`|Microsoft Jet データベース エンジンを使用してデータベースの場合は、ユーザー ID と接続されているテーブルのパスワードが保存接続情報を持つことを示します。|
|`dbSystemObject`|テーブルが、Microsoft Jet データベース エンジンによって提供されるシステム テーブルであることを示します。|
|`dbHiddenObject`|Microsoft Jet データベース エンジンによって提供される非表示テーブルを示します。|

*lpszSrcTable*<br/>
ソース テーブル名を含む文字列へのポインター。 既定では、この値は NULL として初期化されます。

*lpszConnect*<br/>
既定の接続文字列を含む文字列へのポインター。 既定では、この値は NULL として初期化されます。

### <a name="remarks"></a>Remarks

テーブル定義をという名前が、一度呼び出すことができますし、 [Append](#append)をデータベースのテーブル定義のコレクションにテーブル定義を保存します。 呼び出した後`Append`、テーブル定義は、開いている状態、および作成に使用することができます、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクト。

関連情報については、DAO のヘルプで「CreateTableDef メソッド」を参照してください。

##  <a name="createfield"></a>  CDaoTableDef::CreateField

テーブルにフィールドを追加するには、このメンバー関数を呼び出します。

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
このフィールドの名前を指定する文字列式へのポインター。

*nType*<br/>
フィールドのデータ型を示す値。 設定には、これらの値のいずれかを指定できます。

|型|サイズ (バイト)|説明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 バイト|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|通貨 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|フローティング|
|`dbDouble`|8|二重線|
|`dbDate`|8|日付/時刻 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|テキスト ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|長いバイナリ (OLE オブジェクト)、 [CLongBinary](../../mfc/reference/clongbinary-class.md)または[CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|メモ ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
テキストを含むフィールドのバイト単位の最大サイズまたはテキストまたは数値の値を含むフィールドの固定サイズを示す値。 *LSize*テキスト フィールドを除くすべてのパラメーターは無視されます。

*lAttributes*<br/>
フィールドの特性に対応する値は、ビットごとの OR を使用して結合できます。

|定数|説明|
|--------------|-----------------|
|`dbFixedField`|フィールド サイズが (数値フィールドの既定値) を修正しました。|
|`dbVariableField`|フィールド サイズは、変数 (テキスト フィールドのみ) です。|
|`dbAutoIncrField`|新しいレコードのフィールドの値は、変更できない一意の long 整数を自動的にインクリメントされます。 Microsoft Jet データベースのテーブルに対してのみサポートされます。|
|`dbUpdatableField`|フィールドの値を変更できます。|
|`dbDescending`|降順で並べ替えられます (Z、A または 100-0) 順序 (インデックス オブジェクトのフィールド コレクション内のフィールド オブジェクトにのみ適用されます)。 この定数を省略した場合に昇順に並べ替えられます (A ~ Z、0 - 100) 順序 (既定値)。|

*fieldinfo*<br/>
参照を[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。

### <a name="remarks"></a>Remarks

A `DAOField` (OLE) オブジェクトを作成し、フィールド コレクションに追加、 `DAOTableDef` (OLE) オブジェクト。 オブジェクトのプロパティを確認するための用途以外使用することも`CDaoFieldInfo`テーブル定義に新しいフィールドを作成するための入力パラメーターを作成します。 最初のバージョン`CreateField`は簡単に使用すると、さらに細かく制御する場合は、2 番目のバージョンを使用することができますが、 `CreateField`、受け取り、`CDaoFieldInfo`パラメーター。

バージョンを使用する場合`CreateField`を受け取る、`CDaoFieldInfo`パラメーター、慎重に設定する必要ありますの次のメンバーの各、`CDaoFieldInfo`構造体。

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

残りのメンバー`CDaoFieldInfo`に設定する必要があります**0**、FALSE、またはメンバーの適切な空の文字列または`CDaoException`発生する可能性があります。

関連情報については、DAO のヘルプで「CreateField メソッド」を参照してください。

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

テーブルにインデックスを追加するには、この関数を呼び出します。

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>パラメーター

*indexinfo*<br/>
参照を[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)構造体。

### <a name="remarks"></a>Remarks

インデックスは、データベースのテーブルと重複するレコードが受け入れられるかどうかからアクセスされるレコードの順序を指定します。 インデックスでは、データに効率的にアクセスも提供します。

テーブルにインデックスを作成する必要はありませんが、インデックスなしのテーブルで特定のレコードへのアクセスまたはレコード セットを作成することができます、長い時間がかかります。 その一方で、多くのインデックスを作成する減速更新、追加、のすべてのインデックスが自動的に更新されると、削除操作。 作成するインデックスを決定する際に、これらの要因を検討してください。

次のメンバー、`CDaoIndexInfo`構造体を設定する必要があります。

- `m_strName` 名前を指定する必要があります。

- `m_pFieldInfos` 配列を指す必要があります`CDaoIndexFieldInfo`構造体。

- `m_nFields` 配列内のフィールドの数を指定する必要があります`CDaoFieldInfo`構造体。

残りのメンバーは無視される場合は FALSE に設定します。 さらに、`m_lDistinctCount`メンバーは、インデックスの作成時に無視されます。

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

フィールドを削除し、アクセスできないようにするには、このメンバー関数を呼び出します。

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
既存のフィールドの名前を指定する文字列式へのポインター。

*nIndex*<br/>
インデックスで検索する場合、テーブルの 0 から始まるフィールド コレクション内のフィールドのインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、新しいオブジェクトをデータベースに追加されていない場合や[CanUpdate](#canupdate) 0 以外の値を返します。

関連情報については、DAO のヘルプで「メソッドの削除」を参照してください。

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

基になるテーブルにインデックスを削除するには、このメンバー関数を呼び出します。

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
既存のインデックスの名前を指定する文字列式へのポインター。

*nIndex*<br/>
インデックスで検索する場合のデータベースの 0 から始まる TableDefs コレクション内のインデックス オブジェクトの配列インデックス。

### <a name="remarks"></a>Remarks

このメンバー関数を使用するには、データベースに追加されていない新しいオブジェクトの場合、または[CanUpdate](#canupdate) 0 以外の値を返します。

関連情報については、DAO のヘルプで「メソッドの削除」を参照してください。

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

`CDaoTableDef`オブジェクト、戻り値で表されるテーブルの特性を指定します、`CDaoTableDef`オブジェクトし、これらの定数の合計を指定できます。

```
long GetAttributes();
```

### <a name="return-value"></a>戻り値

1 つまたは複数の特性を示す値を返します、`CDaoTableDef`オブジェクト。

### <a name="remarks"></a>Remarks

|定数|説明|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet データベース エンジンを使用するデータベースの場合は、排他的に開かれて、接続されているテーブルを示します。|
|`dbAttachSavePWD`|Microsoft Jet データベース エンジンを使用してデータベースの場合は、ユーザー ID と接続されているテーブルのパスワードが保存接続情報を持つことを示します。|
|`dbSystemObject`|テーブルが、Microsoft Jet データベース エンジンによって提供されるシステム テーブルであることを示します。|
|`dbHiddenObject`|Microsoft Jet データベース エンジンによって提供される非表示テーブルを示します。|
|`dbAttachedTable`|テーブルが Paradox データベースなどの非 ODBC データベースからの接続されているテーブルであることを示します。|
|`dbAttachedODBC`|テーブルが Microsoft SQL Server など、ODBC データベースからの接続されているテーブルであることを示します。|

システム テーブルは、さまざまな内部情報が含まれる Microsoft Jet データベース エンジンによって作成されるテーブルです。

非表示の表は、一時的な使用、Microsoft Jet データベース エンジンによって作成されたテーブルです。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

データ ソースの接続文字列を取得するには、このメンバー関数を呼び出します。

```
CString GetConnect();
```

### <a name="return-value"></a>戻り値

A`CString`テーブルのパスとデータベースの種類を含むオブジェクト。

### <a name="remarks"></a>Remarks

`CDaoTableDef`アタッチ テーブルを表すオブジェクトを`CString`オブジェクトは、1 つまたは 2 つの部分 (データベースの型指定子およびデータベースへのパス) で構成されています。

次の表に示すように、パス データベース ファイルを含むディレクトリの完全パスを指定し、前に、識別子が必要"データベース ="。 (Microsoft Jet および Microsoft Excel で次のようにデータベース) となる場合、データベースのパスの引数に特定のファイル名が含まれます。

テーブルに[CDaoTableDef::SetConnect](#setconnect)可能なデータベースの種類とその対応するデータベースの指定子とパスを示しています。

Microsoft Jet データベースのベース テーブルの指定子は空の文字列 ("")。

ODBC ドライバーがテーブルにアクセスするログイン ダイアログ ボックスの最初の時刻を表示しますパスワードが必要なが指定されていない場合、もう一度接続を閉じて再度開く場合。 接続されているテーブルがある場合、`dbAttachSavePWD`属性、ログイン プロンプトは表示されません、テーブルが再度開かれたとき。

関連情報については、DAO のヘルプ「プロパティの接続」を参照してください。

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

テーブルの基になる日付と時刻を判断するには、この関数を呼び出し、`CDaoTableDef`オブジェクトが作成されました。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>戻り値

基になるテーブルの作成の日時を含む値を`CDaoTableDef`オブジェクト。

### <a name="remarks"></a>Remarks

日付と時刻の設定は、ベース テーブルが作成または最後に更新されたコンピューターから派生します。 マルチ ユーザー環境では、ユーザーは、; 不一致を避けるため、ファイル サーバーから直接これらの設定を取得する必要があります。すべてのクライアントが、"standard"のタイム ソースを使用する必要があります: 1 台のサーバーからでしょう。

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

テーブルの基になる日付と時刻を判断するには、この関数を呼び出し、`CDaoTableDef`オブジェクトが最後に更新されました。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>戻り値

基になるテーブルの日付と時刻を格納する値、`CDaoTableDef`オブジェクトが最後に更新されました。

### <a name="remarks"></a>Remarks

日付と時刻の設定は、ベース テーブルが作成または最後に更新されたコンピューターから派生します。 マルチ ユーザー環境では、ユーザーは、; 不一致を避けるため、ファイル サーバーから直接これらの設定を取得する必要があります。すべてのクライアントが、"standard"のタイム ソースを使用する必要があります: 1 台のサーバーからでしょう。

関連情報については、DAO のヘルプ トピックの"DateCreated、LastUpdated プロパティ"を参照してください。

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

テーブルで定義されているフィールドの数を取得するには、このメンバー関数を呼び出します。

```
short GetFieldCount();
```

### <a name="return-value"></a>戻り値

テーブル内のフィールドの数。

### <a name="remarks"></a>Remarks

その値が 0 の場合はありませんオブジェクトのコレクションです。

関連情報については、「Count プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

さまざまな種類のテーブル定義で定義されているフィールドに関する情報を取得するには、このメンバー関数を呼び出します。

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
インデックスで検索する場合、テーブルの 0 から始まるフィールド コレクション内のフィールド オブジェクトのインデックス。

*fieldinfo*<br/>
参照を[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。

*dwInfoOptions*<br/>
取得するフィールドに関する情報を指定するオプション。 使用可能なオプションを返す関数が何とここは。

- `AFX_DAO_PRIMARY_INFO` (既定値)名前、種類、サイズ、属性。 最速のパフォーマンスには、このオプションを使用します。

- `AFX_DAO_SECONDARY_INFO` プライマリの情報と。必要に応じて、序数の位置、長さ 0 は、順序、外部名、ソース フィールド、ソース テーブルの照合を許可します。

- `AFX_DAO_ALL_INFO` プライマリとセカンダリの情報と。検証規則、入力テキストの場合は、既定値

*lpszName*<br/>
名前で検索する場合、フィールド オブジェクトの名前へのポインター。 名前は、フィールドの一意名で、最大 64 文字の文字列です。

### <a name="remarks"></a>Remarks

関数の 1 つのバージョンでは、インデックスを使用してフィールドを検索することができます。 その他のバージョンでは、フィールド名で検索できます。

返される情報については、次を参照してください。、 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体。 この構造体メンバーの説明に上記の情報の項目に対応するは*dwInfoOptions*します。 1 つのレベルの情報を要求するときに、そのレベルもの情報を取得します。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

テーブルのインデックスの数を取得するには、このメンバー関数を呼び出します。

```
short GetIndexCount();
```

### <a name="return-value"></a>戻り値

テーブルのインデックスの数。

### <a name="remarks"></a>Remarks

その値が 0 の場合はありませんインデックスのコレクションです。

関連情報については、「Count プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

さまざまなテーブル定義で定義されているインデックスに関する情報を取得するには、このメンバー関数を呼び出します。

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
コレクション内の位置で検索する場合、テーブルの 0 から始まるインデックス コレクション内のインデックス オブジェクトの数値インデックス。

*indexinfo*<br/>
参照を[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)構造体。

*dwInfoOptions*<br/>
取得するインデックスに関する情報を指定するオプション。 使用可能なオプションを返す関数が何とここは。

- `AFX_DAO_PRIMARY_INFO` 名前、フィールドについては、フィールドです。 最速のパフォーマンスには、このオプションを使用します。

- `AFX_DAO_SECONDARY_INFO` プライマリの情報と。クラスター化すると、null 値、必須で、外部を無視する、一意のプライマリ

- `AFX_DAO_ALL_INFO` プライマリとセカンダリの情報と。Distinct Count

*lpszName*<br/>
名前で検索する場合、インデックス オブジェクトの名前へのポインター。

### <a name="remarks"></a>Remarks

関数の 1 つのバージョンでは、コレクション内の位置でインデックスを検索することができます。 その他のバージョンでは、名前、インデックスを検索することができます。

返される情報については、次を参照してください。、 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)構造体。 この構造体メンバーの説明に上記の情報の項目に対応するは*dwInfoOptions*します。 1 つのレベルの情報を要求するときに、そのレベルもの情報を取得します。

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getname"></a>  CDaoTableDef::GetName

ユーザー定義の基になるテーブルの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetName();
```

### <a name="return-value"></a>戻り値

ユーザー定義テーブルの名前。

### <a name="remarks"></a>Remarks

この名前は文字で始まるし、最大 64 文字まで含めることができます。 数字を含めることができ、アンダー スコア文字しますが、区切り記号やスペースを含めることはできません。

関連情報については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

レコードの数を調べるには、このメンバー関数を呼び出す、`CDaoTableDef`オブジェクト。

```
long GetRecordCount();
```

### <a name="return-value"></a>戻り値

テーブル定義のオブジェクトにアクセスするレコードの数。

### <a name="remarks"></a>Remarks

呼び出す`GetRecordCount`テーブル型に対する`CDaoTableDef`オブジェクトがテーブル内のレコードのおおよその数を反映し、テーブルのレコードの追加し、削除、すぐに影響を受けますが。 呼び出すまで、トランザクションがレコードの数の一部として表示されますがロールバック[CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)します。 A`CDaoTableDef`レコードのないオブジェクトが 0 のレコード数プロパティの設定。 接続されているテーブルまたは ODBC のデータベースを扱うとき`GetRecordCount`常に-1 を返します。

関連情報については、「RecordCount プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

ソース データベースに接続されているテーブルの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>戻り値

A`CString`ネイティブ データ テーブルの場合は、接続されたテーブル、または空の文字列のソース名を指定するオブジェクト。

### <a name="remarks"></a>Remarks

接続されたテーブルは、Microsoft Jet データベースへのリンクされた別のデータベースのテーブルです。 接続されているテーブルのデータは、他のアプリケーションで操作できる、外部データベースに残ります。

関連情報については、「SourceTableName プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

テーブル定義の検証規則を取得するには、このメンバー関数を呼び出します。

```
CString GetValidationRule();
```

### <a name="return-value"></a>戻り値

A`CString`を変更またはテーブルに追加すると、フィールドのデータを検証するオブジェクト。

### <a name="remarks"></a>Remarks

検証規則は、更新操作に関連して使用されます。 テーブル定義に検証規則が含まれている場合、そのテーブル定義の更新プログラムは、データが変更される前に事前に定義された条件に一致する必要があります。 変更が一致しない場合、条件の値を含む例外[GetValidationText](#getvalidationtext)がスローされます。 `CDaoTableDef`オブジェクトをこの`CString`は、接続されているテーブルと、ベース テーブルの読み取り/書き込みの読み取り専用です。

関連情報については、"Validationrule"DAO ヘルプのトピックを参照してください。

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

ユーザー入力の検証規則に一致しないデータを表示する文字列を取得するには、この関数を呼び出します。

```
CString GetValidationText();
```

### <a name="return-value"></a>戻り値

A`CString`検証規則に一致しないデータが入力すると、ユーザーに表示されるテキストを指定するオブジェクト。

### <a name="remarks"></a>Remarks

`CDaoTableDef`オブジェクトをこの`CString`は、接続されているテーブルと、ベース テーブルの読み取り/書き込みの読み取り専用です。

関連情報については、「プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

確認するには、このメンバー関数を呼び出すかどうか、`CDaoTableDef`オブジェクトが現在開いています。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

0 以外の値、`CDaoTableDef`オブジェクトが開いている場合は 0 それ以外の場合。

### <a name="remarks"></a>Remarks

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

ポインターが含まれています、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)このテーブルのオブジェクト。

### <a name="remarks"></a>Remarks

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

基に DAO テーブル定義オブジェクトの OLE インターフェイスへのポインターが含まれています、`CDaoTableDef`オブジェクト。

### <a name="remarks"></a>Remarks

DAO インターフェイスに直接アクセスする必要がある場合は、このポインターを使用します。

##  <a name="open"></a>  CDaoTableDef::Open

テーブル定義を開くには、このメンバー関数は以前、データベースに保存した呼び出しはのテーブル定義のコレクションです。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
テーブル名を指定する文字列へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

接続されたテーブルの接続情報を更新するには、このメンバー関数を呼び出します。

```
void RefreshLink();
```

### <a name="remarks"></a>Remarks

呼び出すことによって接続されたテーブルの接続情報を変更する[SetConnect](#setconnect) 、対応する`CDaoTableDef`オブジェクトを使用して、`RefreshLink`メンバー関数は、情報を更新します。 呼び出すと`RefreshLink`、接続されているテーブルのプロパティは変更されません。

強制的に変更された接続情報を有効、すべての開いている[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)このテーブルの定義に基づくオブジェクトを閉じる必要があります。

関連情報については、DAO のヘルプで「RefreshLink メソッド」を参照してください。

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

1 つまたは複数の特性を示す値を設定、`CDaoTableDef`オブジェクト。

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>パラメーター

*lAttributes*<br/>
表されるテーブルの特性、`CDaoTableDef`オブジェクトし、これらの定数の合計を指定できます。

|定数|説明|
|--------------|-----------------|
|`dbAttachExclusive`|Microsoft Jet データベース エンジンを使用するデータベースの場合は、排他的に開かれて、接続されているテーブルを示します。|
|`dbAttachSavePWD`|Microsoft Jet データベース エンジンを使用してデータベースの場合は、ユーザー ID と接続されているテーブルのパスワードが保存接続情報を持つことを示します。|
|`dbSystemObject`|テーブルが、Microsoft Jet データベース エンジンによって提供されるシステム テーブルであることを示します。|
|`dbHiddenObject`|Microsoft Jet データベース エンジンによって提供される非表示テーブルを示します。|

### <a name="remarks"></a>Remarks

複数の属性を設定するときに、ビットごとの OR 演算子を使用して適切な定数を組み合わせることができます。 設定`dbAttachExclusive`非添付のテーブルで例外が生成されます。 結合、次の値も、例外が発生します。

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

関連情報については、「属性のプロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

`CDaoTableDef`文字列オブジェクト、接続されたテーブルを表すオブジェクトを 1 つまたは 2 つの部分 (データベースの型指定子およびデータベースへのパス) で構成されます。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>パラメーター

*lpszConnect*<br/>
ODBC または ISAM のインストール可能なドライバーに渡す追加のパラメーターを指定する文字列式へのポインター。

### <a name="remarks"></a>Remarks

次の表に示すように、パス データベース ファイルを含むディレクトリの完全パスを指定し、前に、識別子が必要"データベース ="。 (Microsoft Jet および Microsoft Excel で次のようにデータベース) となる場合、データベースのパスの引数に特定のファイル名が含まれます。

> [!NOTE]
>  フォームのパス ステートメントに等号 (=) の前後に空白を含めない"データベース = ドライブ:\\\path"。 これは、スローされる例外が発生し、接続の失敗になります。

次の表は、可能なデータベースの種類とその対応するデータベースの指定子とパスを示します。

|データベースの種類|指定子|パス|
|-------------------|---------------|----------|
|Jet データベース エンジンを使用してデータベース|"[ `database`];"|" `drive`:\\\ *path*\\\ *filename*.MDB"|
|dBASE III|"dBASE III;"|" `drive`:\\\ *パス*"|
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *パス*"|
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *パス*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *パス*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *パス*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *パス*"|
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *パス*\\\ *filename*します。XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *パス*\\\ *filename*します。XLS"|
|Excel 5.0 または Excel 95|"Excel 5.0;"|" `drive`:\\\ *パス*\\\ *filename*します。XLS"|
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *パス*\ *filename*します。XLS"|
|HTML のインポート|「HTML のインポート。」|" `drive`:\\\ *パス*\ *filename*"|
|HTML のエクスポート|「HTML エクスポート;」|" `drive`:\\\ *パス*"|
|テキスト|「テキスト」|"drive:\\\path"|
|ODBC|"ODBC;DATABASE = `database`;UID =*ユーザー*;PWD =*パスワード*;DSN = *%datasourcename;* LOGINTIMEOUT =*秒;*"(すべてのサーバーの完全な接続文字列は限りませんではほんの一例です。 パラメーター間のスペースに非常に重要ですが、します。)|なし|
|Exchange|"Exchange;<br /><br /> MAPILEVEL= *folderpath*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFILE= *profile*;]<br /><br /> [PWD= *password*;]<br /><br /> [DATABASE= `database`;]"|*"drive*:\\\ *path*\\\ *filename*.MDB"|

> [!NOTE]
>  DAO 3.5 の時点では、市販がサポートされていません。

二重の円記号を使用する必要があります (\\\\) 接続文字列にします。 使用して既存の接続のプロパティを変更したかどうかは`SetConnect`、後で呼び出す必要がある[RefreshLink](#refreshlink)します。 使用して接続プロパティを初期化する場合`SetConnect`、呼び出しではない必要がある`RefreshLink`、テーブル定義を追加するように選択する必要があります、最初にします。

ODBC ドライバーがテーブルにアクセスするログイン ダイアログ ボックスの最初の時刻を表示しますパスワードが必要なが指定されていない場合、もう一度接続を閉じて再度開く場合。

接続文字列を設定することができます、`CDaoTableDef`オブジェクト ソースの引数を提供することで、`Create`メンバー関数。 型、パス、ユーザー ID、パスワード、またはデータベースの ODBC データ ソースを確認する設定を確認することができます。 詳細については、特定のドライバーのマニュアルを参照してください。

関連情報については、DAO のヘルプ「プロパティの接続」を参照してください。

##  <a name="setname"></a>  CDaoTableDef::SetName

ユーザー定義テーブルの名前を設定するには、このメンバー関数を呼び出します。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
テーブルの名前を指定する文字列式へのポインター。

### <a name="remarks"></a>Remarks

名前は文字で始める必要があり、最大 64 文字まで含めることができます。 数字を含めることができ、アンダー スコア文字しますが、区切り記号やスペースを含めることはできません。

関連情報については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

接続されたテーブルの名前またはベース テーブルの名前を指定するには、このメンバー関数を呼び出す、`CDaoTableDef`オブジェクトが基づくデータの元のソース内に存在します。

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>パラメーター

*lpszSrcTableName*<br/>
外部データベースのテーブル名を指定する文字列式へのポインター。 ベース テーブルではの設定は、空の文字列 ("")。

### <a name="remarks"></a>Remarks

呼び出す必要がありますし、 [RefreshLink](#refreshlink)します。 このプロパティの設定では、ベース テーブルと読み取り/書き込みの接続されたテーブルまたはコレクションに追加されていないオブジェクトの空です。

関連情報については、「SourceTableName プロパティ」DAO ヘルプのトピックを参照してください。

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

テーブル定義の検証規則を設定するには、このメンバー関数を呼び出します。

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>パラメーター

*lpszValidationRule*<br/>
操作を評価する文字列式へのポインター。

### <a name="remarks"></a>Remarks

検証規則は、更新操作に関連して使用されます。 テーブル定義に検証規則が含まれている場合、そのテーブル定義の更新プログラムは、データが変更される前に事前に定義された条件に一致する必要があります。 変更が一致しない場合、条件のテキストを含む例外[GetValidationText](#getvalidationtext)が表示されます。

検証は、Microsoft Jet データベース エンジンを使用するデータベースのみサポートされます。 式は、ユーザー定義関数、集計関数のドメイン、SQL 集計関数、またはクエリを参照できません。 検証規則を`CDaoTableDef`オブジェクトは、そのオブジェクトの複数のフィールドを参照できます。

たとえば、という名前のフィールド*hire_date*と*termination_date*、検証規則があります。

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

関連情報については、"Validationrule"DAO ヘルプのトピックを参照してください。

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

検証規則の例外のテキストを設定するには、このメンバー関数を呼び出す、 `CDaoTableDef` Microsoft Jet データベース エンジンでサポートされている、基になるベース テーブルを持つオブジェクト。

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>パラメーター

*lpszValidationText*<br/>
データを入力した場合に表示されるテキストを指定する文字列式へのポインターが無効です。

### <a name="remarks"></a>Remarks

接続されたテーブルの検証のテキストを設定することはできません。

関連情報については、「プロパティ」DAO ヘルプのトピックを参照してください。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset クラス](../../mfc/reference/cdaorecordset-class.md)
