---
title: CDaoDatabase クラス
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 4c594b1ddfc1464417506557bb8743c4979be677
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304283"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase クラス

データアクセスオブジェクト (DAO) を使用した Access データベースへの接続を表します。 DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CDaoDatabase:: CDaoDatabase](#cdaodatabase)|`CDaoDatabase` オブジェクトを構築します。 オブジェクトをデータベースに接続するには、`Open` を呼び出します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CDaoDatabase:: CanTransact](#cantransact)|データベースでトランザクションがサポートされている場合は、0以外の値を返します。|
|[CDaoDatabase:: CanUpdate](#canupdate)|`CDaoDatabase` オブジェクトが更新可能な場合 (読み取り専用ではない場合) は0以外の値を返します。|
|[CDaoDatabase::Close](#close)|データベース接続を閉じます。|
|[CDaoDatabase::Create](#create)|基になる DAO データベースオブジェクトを作成し、`CDaoDatabase` オブジェクトを初期化します。|
|[CDaoDatabase:: creater](#createrelation)|データベース内のテーブル間の新しいリレーションシップを定義します。|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|データベースのクエリ定義コレクションに保存されているクエリ定義オブジェクトを削除します。|
|[CDaoDatabase::D eleteRelation](#deleterelation)|データベース内のテーブル間の既存のリレーションシップを削除します。|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|データベース内のテーブルの定義を削除します。 これにより、実際のテーブルとそのすべてのデータが削除されます。|
|[CDaoDatabase::Execute](#execute)|アクションクエリを実行します。 結果を返すクエリに対して `Execute` を呼び出すと、例外がスローされます。|
|[CDaoDatabase::GetConnect](#getconnect)|`CDaoDatabase` オブジェクトをデータベースに接続するために使用される接続文字列を返します。 ODBC に使用されます。|
|[CDaoDatabase:: GetName](#getname)|現在使用されているデータベースの名前を返します。|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|データベースに対して定義されたクエリの数を返します。|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|データベースで定義されている、指定されたクエリに関する情報を返します。|
|[CDaoDatabase:: GetQueryTimeout 解説](#getquerytimeout)|データベースクエリ操作がタイムアウトするまでの秒数を返します。`Execute` の呼び出しなど、ODBC データソースに対する以降のすべてのオープン、追加、新規、更新、および編集操作などの操作に影響します。|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|前回の更新、編集、または追加操作によって影響を受けたレコードの数、または `Execute`の呼び出しによって影響を受けたレコードの数を返します。|
|[CDaoDatabase:: GetRelationCount](#getrelationcount)|データベース内のテーブル間に定義されているリレーションシップの数を返します。|
|[CDaoDatabase:: GetRelationInfo](#getrelationinfo)|データベース内のテーブル間に定義されている、指定されたリレーションシップに関する情報を返します。|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|データベースで定義されているテーブルの数を返します。|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|データベース内の指定されたテーブルに関する情報を返します。|
|[CDaoDatabase:: GetVersion](#getversion)|データベースに関連付けられているデータベースエンジンのバージョンを返します。|
|[CDaoDatabase::IsOpen](#isopen)|`CDaoDatabase` オブジェクトが現在データベースに接続されている場合は、0以外の値を返します。|
|[CDaoDatabase::Open](#open)|データベースへの接続を確立します。|
|[CDaoDatabase:: SetQueryTimeout 解説](#setquerytimeout)|データベースクエリ操作 (ODBC データソースのみ) がタイムアウトするまでの秒数を設定します。以降のすべての open、add new、update、および delete 操作に影響します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[CDaoDatabase:: m_pDAODatabase](#m_pdaodatabase)|基になる DAO データベースオブジェクトへのポインター。|
|[CDaoDatabase:: m_pWorkspace](#m_pworkspace)|データベースを格納し、そのトランザクション領域を定義する[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)オブジェクトへのポインター。|

## <a name="remarks"></a>コメント

サポートされているデータベース形式の詳細については、「 [GetName](../../mfc/reference/cdaoworkspace-class.md#getname)メンバー関数」を参照してください。 `CDaoDatabase`CDaoWorkspace[ オブジェクトによって表される特定の "ワークスペース" で一度に1つ以上の](../../mfc/reference/cdaoworkspace-class.md)オブジェクトをアクティブにすることができます。 ワークスペースは、Databases コレクションと呼ばれる、開いているデータベースオブジェクトのコレクションを保持します。

## <a name="usage"></a>使用法

レコードセットオブジェクトを作成するときに、データベースオブジェクトを暗黙的に作成することができます。 ただし、データベースオブジェクトを明示的に作成することもできます。 既存のデータベースを `CDaoDatabase`で明示的に使用するには、次のいずれかの操作を行います。

- `CDaoDatabase`オブジェクトを構築し、開いている [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) オブジェクトへのポインターを渡します。

- または、ワークスペースを指定せずに `CDaoDatabase` オブジェクトを構築します (MFC は一時ワークスペースオブジェクトを作成します)。

新しい Microsoft Jet を作成するには (.MDB) データベースを作成し、`CDaoDatabase` オブジェクトを構築して、その[Create](#create) member 関数を呼び出します。 `Create`後に `Open` を呼び出さ*ない*でください。

既存のデータベースを開くには、`CDaoDatabase` オブジェクトを構築し、その[open](#open)メンバー関数を呼び出します。

これらの手法のいずれかによって、DAO データベースオブジェクトがワークスペースの Databases コレクションに追加され、データへの接続が開かれます。 次に、接続されたデータベースで動作するように、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)、または[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)オブジェクトを作成し、これらのオブジェクトのコンストラクターに `CDaoDatabase` オブジェクトへのポインターを渡します。 接続の使用が終了したら、 [Close](#close)メンバー関数を呼び出し、`CDaoDatabase` オブジェクトを破棄します。 以前に閉じていないレコードセットは、`Close` によって閉じられます。

## <a name="transactions"></a>トランザクション

データベーストランザクション処理は、ワークスペースレベルで提供されます。 `CDaoWorkspace`クラスの[BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)、 [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)、および[Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)メンバー関数を参照してください。

## <a name="odbc-connections"></a>ODBC 接続

ODBC データソースを操作する場合は、外部テーブルを Microsoft Jet にアタッチすることをお勧めします (「」をお勧めします。MDB) データベース。

## <a name="collections"></a>コレクション

各データベースには、テーブルセット、querydef、recordset、および relation オブジェクトの独自のコレクションが保持されています。 クラス `CDaoDatabase` は、これらのオブジェクトを操作するためのメンバー関数を提供します。

> [!NOTE]
>  オブジェクトは、MFC データベースオブジェクトではなく、DAO に格納されます。 MFC には、テーブルオブジェクト、クエリ、およびレコードセットオブジェクトのクラスが用意されていますが、リレーションシップオブジェクトのクラスはありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

##  <a name="cantransact"></a>CDaoDatabase:: CanTransact

データベースでトランザクションが許可されているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanTransact();
```

### <a name="return-value"></a>戻り値

データベースがトランザクションをサポートしている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

トランザクションは、データベースのワークスペースで管理されます。

##  <a name="canupdate"></a>CDaoDatabase:: CanUpdate

`CDaoDatabase` オブジェクトで更新が許可されているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>戻り値

`CDaoDatabase` オブジェクトが更新を許可する場合は0以外の。それ以外の場合は0。 `CDaoDatabase` オブジェクトを開いたときに*bReadOnly*で TRUE が渡されたか、またはデータベース自体が読み取り専用であることを示します。 「 [Open](#open) member 関数」を参照してください。

### <a name="remarks"></a>コメント

データベースの更新可能性の詳細については、DAO ヘルプの「更新可能なプロパティ」を参照してください。

##  <a name="cdaodatabase"></a>CDaoDatabase:: CDaoDatabase

`CDaoDatabase` オブジェクトを構築します。

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>パラメーター

*pWorkspace*<br/>
新しいデータベースオブジェクトを格納する `CDaoWorkspace` オブジェクトへのポインター。 既定値の NULL をそのまま使用すると、既定の DAO ワークスペースを使用する一時 `CDaoWorkspace` オブジェクトがコンストラクターによって作成されます。 [M_pWorkspace](#m_pworkspace)データメンバーを使用して、ワークスペースオブジェクトへのポインターを取得できます。

### <a name="remarks"></a>コメント

新しい Microsoft Jet () を作成する場合は、オブジェクトを構築した後。MDB) データベースを呼び出し、オブジェクトの[Create](#create) member 関数を呼び出します。 既存のデータベースを開いている場合は、そのオブジェクトの[Open](#open)メンバー関数を呼び出します。

オブジェクトを終了したら、 [Close](#close)メンバー関数を呼び出してから、`CDaoDatabase` オブジェクトを破棄する必要があります。

`CDaoDatabase` オブジェクトをドキュメントクラスに埋め込むと便利な場合があります。

> [!NOTE]
>  既存の `CDaoDatabase` オブジェクトへのポインターを渡さずに、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトを開くと、`CDaoDatabase` オブジェクトも暗黙的に作成されます。 このデータベースオブジェクトは、レコードセットオブジェクトを閉じたときに閉じられます。

##  <a name="close"></a>  CDaoDatabase::Close

このメンバー関数を呼び出して、データベースに関連付けられている、開いているすべてのレコードセット、テーブルテーブル、およびクエリ定義を閉じます。

```
virtual void Close();
```

### <a name="remarks"></a>コメント

このメンバー関数を呼び出す前に、これらのオブジェクトを自分で閉じることをお勧めします。 `CDaoDatabase` オブジェクトを閉じると、関連付けられている[ワークスペース](../../mfc/reference/cdaoworkspace-class.md)の Databases コレクションからオブジェクトが削除されます。 `Close` によって `CDaoDatabase` オブジェクトが破棄されないため、同じデータベースまたは別のデータベースを開いてオブジェクトを再利用できます。

> [!CAUTION]
>  データベースを閉じる前に、[更新](../../mfc/reference/cdaorecordset-class.md#update)メンバー関数 (保留中の編集がある場合) と、開いているすべてのレコードセットオブジェクトの `Close` メンバー関数を呼び出します。 処理を終了したときに、そのスタック上の[オブジェクトまたは](../../mfc/reference/cdaorecordset-class.md)`CDaoDatabase` オブジェクトを宣言すると、データベースが閉じられ、保存されていない変更は失われ、保留中のすべてのトランザクションがロールバックされ、データに対する保留中の編集はすべて失われます。

> [!CAUTION]
>  レコードセットオブジェクトが開いている間にデータベースオブジェクトを閉じようとした場合、またはその特定のワークスペースに属するデータベースオブジェクトが開いているときにワークスペースオブジェクトを閉じようとした場合、それらのレコードセットオブジェクトは閉じられ、保留中の更新または編集はすべて削除されます。ロールバックされます。 ワークスペースオブジェクトを閉じようとしているときに、そのオブジェクトに属するデータベースオブジェクトが開いている場合、操作はその特定のワークスペースオブジェクトに属するすべてのデータベースオブジェクトを閉じます。その結果、閉じられていないレコードセットオブジェクトが閉じられる可能性があります。 データベースオブジェクトを閉じない場合、MFC はデバッグビルドでアサーションエラーを報告します。

データベースオブジェクトが関数のスコープ外で定義されていて、その関数を閉じずに終了した場合、明示的に閉じるか、または定義されているモジュールがスコープ外になるまで、データベースオブジェクトは開いたままになります。

##  <a name="create"></a>  CDaoDatabase::Create

新しい Microsoft Jet を作成するには (.MDB) データベースを作成した後、`CDaoDatabase` オブジェクトを構築した後、このメンバー関数を呼び出します。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
作成するデータベースファイルの名前を表す文字列式です。 "C:\\\MYDB." のように、完全なパスとファイル名を指定できます。MDB "。 名前を指定する必要があります。 ファイル名拡張子を指定しない場合は、「」と入力します。MDB が追加されます。 ネットワークで汎用名前付け規則 (UNC) がサポートされている場合は、ネットワークパスを指定することもできます。たとえば、"\\\\\\、MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB" などです。 Microsoft Jet のみ (.MDB) データベースファイルは、このメンバー関数を使用して作成できます。 ("\\" はC++エスケープ文字であるため、文字列リテラルには二重の円記号が必要です)。

*lpszLocale*<br/>
データベースを作成するための照合順序を指定するために使用される文字列式です。 既定値は `dbLangGeneral` です。 指定できる値は次のとおりです。

- `dbLangGeneral` 英語、ドイツ語、フランス語、ポルトガル語、イタリア語、および現代のスペイン語

- `dbLangArabic` アラビア語

- `dbLangCyrillic` ロシア語

- `dbLangCzech` チェコ語

- `dbLangDutch` オランダ語

- `dbLangGreek` ギリシャ語

- `dbLangHebrew` ヘブライ語

- `dbLangHungarian` ハンガリー語

- `dbLangIcelandic` アイスランド語

- 北欧言語 `dbLangNordic` (Microsoft Jet データベースエンジンバージョン1.0 のみ)

- `dbLangNorwdan` ノルウェー語とデンマーク語

- `dbLangPolish` ポーランド語

- `dbLangSpanish` 従来のスペイン語

- `dbLangSwedfin` スウェーデン語およびフィンランド語

- `dbLangTurkish` トルコ語

*dwOptions*<br/>
1つ以上のオプションを示す整数。 指定できる値は次のとおりです。

- 暗号化されたデータベースを作成 `dbEncrypt` ます。

- Microsoft Jet データベースバージョン1.0 を使用してデータベースを作成 `dbVersion10` ます。

- Microsoft Jet データベースバージョン1.1 を使用してデータベースを作成 `dbVersion11` ます。

- Microsoft Jet データベースバージョン2.0 を使用してデータベースを作成 `dbVersion20` ます。

- Microsoft Jet データベースバージョン3.0 を使用してデータベースを作成 `dbVersion30` ます。

暗号化定数を省略すると、暗号化されていないデータベースが作成されます。 指定できるバージョン定数は1つだけです。 バージョン定数を省略すると、Microsoft Jet データベースバージョン3.0 を使用するデータベースが作成されます。

> [!CAUTION]
>  データベースが暗号化されていない場合は、ユーザーまたはパスワードのセキュリティを実装している場合でも、データベースを構成するバイナリディスクファイルを直接読み取ることができます。

### <a name="remarks"></a>コメント

`Create` によって、データベースファイルと基になる DAO データベースオブジェクトC++が作成され、オブジェクトが初期化されます。 オブジェクトは、関連付けられているワークスペースの Databases コレクションに追加されます。 データベースオブジェクトが開いている状態です。`Create`後に `Open*` を呼び出さないでください。

> [!NOTE]
>  `Create`では、Microsoft Jet () のみを作成できます。MDB) データベース。 ISAM データベースまたは ODBC データベースを作成することはできません。

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

このメンバー関数を呼び出して、データベース内のプライマリテーブル内の1つ以上のフィールドと、外部テーブル (データベース内の別のテーブル) の1つ以上のフィールドとの間の関係を確立します。

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
リレーションシップオブジェクトの一意の名前です。 名前は文字で始める必要があり、最大40文字まで含めることができます。 数字とアンダースコア文字を含めることはできますが、句読点やスペースは使用できません。

*lpszTable*<br/>
リレーションシップのプライマリテーブルの名前。 テーブルが存在しない場合、MFC は[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローします。

*lpszForeignTable*<br/>
リレーションシップ内の外部テーブルの名前。 テーブルが存在しない場合、MFC は `CDaoException`型の例外をスローします。

*lAttributes*<br/>
リレーションシップの種類に関する情報を格納している long 値。 この値を使用して、参照整合性を適用できます。 ビットごとの OR 演算子 ( **&#124;** ) を使用すると、次のいずれかの値を組み合わせることができます (組み合わせが理にかなっている場合)。

- `dbRelationUnique` リレーションシップは一対一です。

- `dbRelationDontEnforce` リレーションシップは適用されません (参照整合性はありません)。

- `dbRelationInherited` リレーションシップは、2つのアタッチされたテーブルを含む最新複数データベースに存在します。

- `dbRelationUpdateCascade` の更新は連鎖します (カスケードの詳細については、「解説」を参照してください)。

- `dbRelationDeleteCascade` 削除は連鎖します。

*lpszField*<br/>
プライマリテーブル内のフィールドの名前を含む null で終わる文字列へのポインター ( *Lpsztable*によって指定)。

*lpszForeignField*<br/>
*LpszForeignTable*によって名前が付けられた、外部テーブルのフィールドの名前を格納している null で終わる文字列へのポインター。

*relinfo*<br/>
作成するリレーションシップに関する情報を格納する[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)オブジェクトへの参照。

### <a name="remarks"></a>コメント

リレーションシップには、外部データベースのクエリまたはアタッチされたテーブルを含めることはできません。

リレーションシップに2つのテーブルのそれぞれに1つのフィールドが含まれている場合は、関数の最初のバージョンを使用します。 リレーションシップに複数のフィールドが含まれる場合は、2番目のバージョンを使用します。 リレーションシップのフィールドの最大数は14です。

この操作は、基になる DAO 関係オブジェクトを作成しますが、mfc のリレーションシップオブジェクトのカプセル化は `CDaoDatabase`クラスに含まれているので、これは MFC 実装の詳細です。 MFC は、リレーションのクラスを提供しません。

リレーションシップオブジェクトの属性を設定して cascade 操作をアクティブにすると、関連する主キーテーブルが変更されたときに、データベースエンジンによって、他の1つ以上のテーブルのレコードが自動的に更新または削除されます。

たとえば、Customers テーブルと Orders テーブルの間に連鎖削除リレーションシップを設定したとします。 Customers テーブルからレコードを削除すると、その顧客に関連する Orders テーブルのレコードも削除されます。 さらに、Orders テーブルと他のテーブル間の連鎖削除リレーションシップを確立すると、Customers テーブルからレコードを削除すると、それらのテーブルのレコードが自動的に削除されます。

関連情報については、DAO ヘルプの「Createrメソッド」を参照してください。

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

このメンバー関数を呼び出して、`CDaoDatabase` オブジェクトのクエリ定義コレクションから、指定されたクエリ定義 (保存されたクエリ) を削除します。

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
削除する保存済みのクエリの名前を指定します。

### <a name="remarks"></a>コメント

その後、そのクエリはデータベースで定義されなくなります。

クエリ定義オブジェクトの作成の詳細については、「クラス[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)」を参照してください。 `CDaoQueryDef` オブジェクトを構築するときに、querydef オブジェクトが特定の `CDaoDatabase` オブジェクトに関連付けられ、データベースオブジェクトへのポインターを渡します。

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

データベースオブジェクトのリレーションコレクションから既存のリレーションシップを削除するには、このメンバー関数を呼び出します。

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
削除するリレーションシップの名前。

### <a name="remarks"></a>コメント

その後、リレーションシップは存在しなくなります。

関連情報については、DAO ヘルプの「Delete メソッド」を参照してください。

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

このメンバー関数を呼び出して、指定したテーブルとそのすべてのデータを `CDaoDatabase` オブジェクトのテーブル定義コレクションから削除します。

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
削除するテーブル名を指定します。

### <a name="remarks"></a>コメント

その後、そのテーブルはデータベースで定義されなくなります。

> [!NOTE]
>  システムテーブルを削除しないように注意してください。

テーブルオブジェクトの作成の詳細については、「クラス[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)」を参照してください。 `CDaoTableDef` オブジェクトを構築するときに、テーブルオブジェクトが特定の `CDaoDatabase` オブジェクトに関連付けられ、データベースオブジェクトへのポインターが渡されます。

関連情報については、DAO ヘルプの「Delete メソッド」を参照してください。

##  <a name="execute"></a>  CDaoDatabase::Execute

このメンバー関数を呼び出して、アクションクエリを実行するか、データベースに対して SQL ステートメントを実行します。

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>パラメーター

*lpszSQL*<br/>
実行する有効な SQL コマンドを含む null で終わる文字列へのポインター。

*nOptions*<br/>
クエリの整合性に関連するオプションを指定する整数です。 ビットごとの OR 演算子 ( **&#124;** ) を使用して、次の定数のいずれかを組み合わせることができます (たとえば、`dbInconsistent` を `dbConsistent`と組み合わせることはできません)。

- `dbDenyWrite` 他のユーザーに対する書き込み権限を拒否します。

- 整合性のない更新プログラムを `dbInconsistent` (既定)。

- 整合性のある更新プログラムを `dbConsistent` します。

- SQL パススルーを `dbSQLPassThrough` します。 SQL ステートメントを処理のために ODBC データソースに渡します。

- エラーが発生した場合は、更新をロールバック `dbFailOnError` ます。

- 別のユーザーが編集中のデータを変更している場合は、`dbSeeChanges` 実行時エラーが生成されます。

> [!NOTE]
>  `dbInconsistent` と `dbConsistent` の両方が含まれている場合、またはどちらも含まれていない場合は、結果が既定値になります。 これらの定数の詳細については、DAO ヘルプの「Execute メソッド」を参照してください。

### <a name="remarks"></a>コメント

`Execute` は、結果を返さないアクションクエリまたは SQL パススルークエリに対してのみ機能します。 レコードを返す select クエリに対しては機能しません。

アクションクエリの定義と情報については、DAO ヘルプの「アクションクエリ」と「Execute メソッド」を参照してください。

> [!TIP]
>  構文的に正しい SQL ステートメントと適切な権限が指定されている場合、1行の変更や削除ができない場合でも、`Execute` メンバー関数は失敗しません。 したがって、`Execute` メンバー関数を使用して update クエリまたは delete クエリを実行する場合は、常に `dbFailOnError` オプションを使用します。 このオプションを指定すると、MFC は[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローし、影響を受けるレコードがロックされており、更新または削除できない場合に、正常に行われたすべての変更をロールバックします。 常に `GetRecordsAffected` を呼び出して、影響を受けたレコードの数を確認できることに注意してください。

データベースオブジェクトの[GetRecordsAffected](#getrecordsaffected)メンバー関数を呼び出して、最新の `Execute` 呼び出しによって影響を受けたレコードの数を確認します。 たとえば、`GetRecordsAffected` は、アクションクエリの実行時に削除、更新、または挿入されたレコードの数に関する情報を返します。 返されるカウントには、連鎖更新または削除が有効になっている場合、関連テーブルの変更は反映されません。

`Execute` はレコードセットを返しません。 レコードを選択するクエリに対して `Execute` を使用すると、MFC が `CDaoException`型の例外をスローします。 (`CDatabase::ExecuteSQL`に似た `ExecuteSQL` メンバー関数はありません)。

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

このメンバー関数を呼び出して、`CDaoDatabase` オブジェクトを ODBC または ISAM データベースに接続するために使用される接続文字列を取得します。

```
CString GetConnect();
```

### <a name="return-value"></a>戻り値

ODBC データソースで[Open](#open)が正常に呼び出された場合の接続文字列です。それ以外の場合は、空の文字列。 Microsoft Jet (.MDB) データベースの場合、 [Execute](#execute)メンバー関数で使用される `dbSQLPassThrough` オプションと共に使用するか、レコードセットを開くときに使用するように設定しない限り、文字列は常に空です。

### <a name="remarks"></a>コメント

文字列は、パススルークエリで使用される、開いているデータベースまたはデータベースのソースに関する情報を提供します。 接続文字列は、データベース型指定子と0個以上のパラメーターで構成され、セミコロンで区切られます。

> [!NOTE]
>  MFC DAO クラスを使用して ODBC 経由でデータソースに接続することは、アタッチされたテーブルを介して接続するよりも効率が悪くなります。

> [!NOTE]
>  接続文字列は、必要に応じて ODBC および特定の ISAM ドライバーに追加情報を渡すために使用されます。 では使用されません。MDB データベース。 Microsoft Jet データベースベーステーブルの場合、接続文字列は空の文字列 ("") です。ただし、上記の「戻り値」で説明されているように、SQL パススルークエリに使用する場合は除きます。

接続文字列の作成方法の詳細については、「 [Open](#open) member 関数」を参照してください。 接続文字列が `Open` 呼び出しで設定されたら、後でその接続文字列を使用して設定を確認し、データベースの種類、パス、ユーザー ID、パスワード、または ODBC データソースを確認できます。

##  <a name="getname"></a>  CDaoDatabase::GetName

このメンバー関数を呼び出して、現在開いているデータベースの名前を取得します。これは、既存のデータベースファイルの名前、または登録されている ODBC データソースの名前です。

```
CString GetName();
```

### <a name="return-value"></a>戻り値

成功した場合は、データベースの完全なパスとファイル名。それ以外の場合は、空の[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>コメント

ネットワークで汎用名前付け規則 (UNC) がサポートされている場合は、ネットワークパスを指定することもできます。たとえば、"\\\\\\\MYSHARE\\\\\MYDIR\\\MYDB.MDB "。 ("\\" はC++エスケープ文字であるため、文字列リテラルには二重の円記号が必要です)。

たとえば、この名前を見出しに表示することができます。 名前の取得中にエラーが発生した場合、MFC は[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローします。

> [!NOTE]
>  外部データベースにアクセスするときのパフォーマンスを向上させるために、外部データベーステーブルを Microsoft Jet データベース () にアタッチすることをお勧めします。MDB) は、データソースに直接接続するのではなく、

データベースの種類は、パスが指すファイルまたはディレクトリによって示されます。次に例を示します。

|パス名は. を指します。|データベースの種類|
|--------------------------|-------------------|
|.MDB ファイル|Microsoft Jet データベース (Microsoft Access)|
|が格納されているディレクトリ。DBF ファイル|dBASE データベース|
|が格納されているディレクトリ。XLS ファイル|Microsoft Excel データベース|
|が格納されているディレクトリ。PDX ファイル|Paradox データベース|
|適切に書式設定されたテキストデータベースファイルを含むディレクトリ|テキスト形式のデータベース|

SQL Server や Oracle などの ODBC データベースの場合、データベースの接続文字列によって、ODBC によって登録されたデータソース名 (DSN) が識別されます。

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

このメンバー関数を呼び出して、データベースのクエリ定義コレクションで定義されたクエリの数を取得します。

```
short GetQueryDefCount();
```

### <a name="return-value"></a>戻り値

データベースで定義されたクエリの数。

### <a name="remarks"></a>コメント

`GetQueryDefCount` は、クエリ定義コレクション内のすべてのクエリをループ処理する必要がある場合に便利です。 コレクション内の特定のクエリに関する情報を取得するには、「 [Getqueryていぎ fo](#getquerydefinfo)」を参照してください。

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

このメンバー関数を呼び出して、データベースで定義されているクエリに関するさまざまな種類の情報を取得します。

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによって検索するための、データベースのクエリ定義コレクション内の定義済みクエリのインデックス。

*queryていぎ fo*<br/>
要求された情報を返す[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)オブジェクトへの参照。

*オプション*<br/>
取得するレコードセットに関する情報を指定するオプション。 使用可能なオプションを次に示します。この一覧には、関数がレコードセットに関して返す原因が示されています。

- AFX_DAO_PRIMARY_INFO (既定) 名前、型

- プライマリ情報に加えて、[作成日]、[最終更新日]、[レコードを返す]、[更新可能] を AFX_DAO_SECONDARY_INFO します。

- プライマリとセカンダリの情報に加えて、SQL、Connect、ODBCTimeout を AFX_DAO_ALL_INFO します。

*lpszName*<br/>
名前で参照するために、データベースで定義されているクエリの名前を含む文字列。

### <a name="remarks"></a>コメント

関数の2つのバージョンが用意されているので、データベースのクエリ定義のコレクションでインデックスを使用するか、クエリの名前を使用してクエリを選択できます。

*Queryていぎ fo*で返される情報の説明については、 [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)構造体を参照してください。 この構造体には、前に説明した情報の項目に対応するメンバーが含まれ*ています。* 1レベルの情報を要求すると、以前のレベルの情報も取得されます。

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

このメンバー関数を呼び出して、接続されたデータベースでの後続の操作がタイムアウトになるまでの現在の許容秒数を取得します。

```
short GetQueryTimeout();
```

### <a name="return-value"></a>戻り値

タイムアウト値を秒単位で示す短整数。

### <a name="remarks"></a>コメント

操作は、ネットワークアクセスの問題、クエリ処理時間の超過などによってタイムアウトする場合があります。 設定が有効になっている間は、この `CDaoDatabase` オブジェクトに関連付けられているすべてのレコードセットに対して、開いているすべての新しい、追加、更新、削除の各操作に影響します。 [Setquerytimeout](#setquerytimeout)を呼び出すことにより、現在のタイムアウト設定を変更できます。 を開いた後でレコードセットのクエリタイムアウト値を変更しても、レコードセットの値は変更されません。 たとえば、後続の[移動](../../mfc/reference/cdaorecordset-class.md#move)操作では、新しい値は使用されません。 既定値は、データベースエンジンが初期化されるときに初期設定されます。

クエリタイムアウトの既定値は、Windows レジストリから取得されます。 レジストリ設定がない場合、既定値は60秒です。 一部のデータベースでは、クエリのタイムアウト値を設定する機能がサポートされていません。 クエリのタイムアウト値を0に設定すると、タイムアウトは発生しません。また、データベースとの通信が応答しなくなる場合があります。 この動作は、開発時に便利な場合があります。 呼び出しが失敗した場合、MFC は[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローします。

関連情報については、DAO ヘルプの「データのプロパティ」を参照してください。

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

このメンバー関数を呼び出して、 [Execute](#execute)メンバー関数の最新の呼び出しによって影響を受けたレコードの数を確認します。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>戻り値

影響を受けたレコードの数を表す長整数。

### <a name="remarks"></a>コメント

返される値には、`Execute`で実行するアクションクエリによって削除、更新、または挿入されたレコードの数が含まれます。 返されるカウントには、連鎖更新または削除が有効になっている場合、関連テーブルの変更は反映されません。

関連情報については、DAO ヘルプの「RecordsAffected プロパティ」を参照してください。

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

このメンバー関数を呼び出して、データベース内のテーブル間に定義されているリレーションシップの数を取得します。

```
short GetRelationCount();
```

### <a name="return-value"></a>戻り値

データベース内のテーブル間に定義されているリレーションシップの数。

### <a name="remarks"></a>コメント

`GetRelationCount` は、データベースのリレーションコレクション内で定義されているすべてのリレーションをループ処理する必要がある場合に便利です。 コレクション内の特定の関係に関する情報を取得するには、「 [GetRelationInfo](#getrelationinfo)」を参照してください。

リレーションシップの概念を示すために、1対多のリレーションシップがある仕入先テーブルと Products テーブルを考えてみます。 このリレーションシップでは、1つの仕入先が複数の製品を提供できます。 その他のリレーションシップは、一対一と多対多です。

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

このメンバー関数を呼び出して、データベースのリレーションコレクション内の指定されたリレーションシップに関する情報を取得します。

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによる検索のための、データベースのリレーションコレクション内のリレーションシップオブジェクトのインデックスです。

*relinfo*<br/>
要求された情報を返す[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)オブジェクトへの参照。

*オプション*<br/>
取得する関係に関する情報を指定するオプション。 ここには、使用可能なオプションと、そのリレーションシップについて関数が返す原因が示されています。

- AFX_DAO_PRIMARY_INFO (既定) 名前、テーブル、外部テーブル

- AFX_DAO_SECONDARY_INFO 属性、フィールド情報

フィールド情報は、リレーションシップに関係するプライマリテーブルのフィールドを含む[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)オブジェクトです。

*lpszName*<br/>
名前で参照するための、リレーションシップオブジェクトの名前を含む文字列。

### <a name="remarks"></a>コメント

この関数の2つのバージョンでは、インデックスまたは名前によってアクセスが提供されます。 *Relinfo*で返される情報の説明については、 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)構造体を参照してください。 この構造体には、前に説明した情報の項目に対応するメンバーが含まれ*ています。* 1つのレベルで情報を要求する場合は、前のレベルでも情報を取得できます。

> [!NOTE]
>  リレーションシップオブジェクトの属性を設定して cascade 操作 (`dbRelationUpdateCascades` または `dbRelationDeleteCascades`) をアクティブ化すると、関連する主キーテーブルが変更されたときに、Microsoft Jet データベースエンジンによって、他の1つ以上のテーブルのレコードが自動的に更新または削除されます。 たとえば、Customers テーブルと Orders テーブルの間に連鎖削除リレーションシップを設定したとします。 Customers テーブルからレコードを削除すると、その顧客に関連する Orders テーブルのレコードも削除されます。 さらに、Orders テーブルと他のテーブル間の連鎖削除リレーションシップを確立すると、Customers テーブルからレコードを削除すると、それらのテーブルのレコードが自動的に削除されます。

##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount

このメンバー関数を呼び出して、データベースに定義されているテーブルの数を取得します。

```
short GetTableDefCount();
```

### <a name="return-value"></a>戻り値

データベースで定義されているテーブルテーブルの数。

### <a name="remarks"></a>コメント

`GetTableDefCount` は、データベースのテーブル定義コレクション内のすべてのテーブルをループ処理する必要がある場合に便利です。 コレクション内の特定のテーブルに関する情報を取得するには、「 [Gettableていぎ fo](#gettabledefinfo)」を参照してください。

##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo

このメンバー関数を呼び出して、データベースで定義されているテーブルに関するさまざまな種類の情報を取得します。

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによって検索するための、データベースのテーブル作成コレクション内のテーブル定義オブジェクトのインデックスです。

*tableていぎ fo*<br/>
要求された情報を返す[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)オブジェクトへの参照。

*オプション*<br/>
取得するテーブルに関する情報を指定するオプション。 ここには、使用可能なオプションと、そのリレーションシップについて関数が返す原因が示されています。

- AFX_DAO_PRIMARY_INFO (既定) 名前、更新可能、属性

- プライマリ情報に加えて、[作成日]、[最終更新日]、[ソーステーブル名]、[接続] を AFX_DAO_SECONDARY_INFO します。

- プライマリとセカンダリの情報に加え、検証規則、検証テキスト、レコード数を AFX_DAO_ALL_INFO します。

*lpszName*<br/>
名前で参照するための、tabledef オブジェクトの名前。

### <a name="remarks"></a>コメント

2つのバージョンの関数が用意されているので、データベースのインデックス作成コレクション内のインデックスでテーブルを選択するか、テーブルの名前を使用してテーブルを選択できます。

*Tableていぎ fo*で返される情報の説明については、 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)構造体を参照してください。 この構造体には、前に説明した情報の項目に対応するメンバーが含まれ*ています。* 1つのレベルで情報を要求すると、以前のレベルについても情報が得られます。

> [!NOTE]
>  AFX_DAO_ALL_INFO オプションでは、取得に時間がかかる情報が提供されます。 この場合、多数のレコードがあると、テーブル内のレコードをカウントするのに非常に時間がかかる可能性があります。

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Microsoft Jet データベースファイルのバージョンを確認するには、このメンバー関数を呼び出します。

```
CString GetVersion();
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられているデータベースファイルのバージョンを示す[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>コメント

返される値は、"major. minor" という形式のバージョン番号を表します。たとえば、"3.0" のようになります。 製品バージョン番号 (3.0 など) は、バージョン番号 (3)、ピリオド、およびリリース番号 (0) で構成されます。 最新バージョンは、1.0、1.1、2.0、および3.0 です。

関連情報については、DAO ヘルプの「バージョンプロパティ」を参照してください。

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

このメンバー関数を呼び出して、`CDaoDatabase` オブジェクトがデータベースで現在開いているかどうかを確認します。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

`CDaoDatabase` オブジェクトが現在開いている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

`CDaoDatabase` オブジェクトの基になる DAO データベースオブジェクトの OLE インターフェイスへのポインターを格納します。

### <a name="remarks"></a>コメント

DAO インターフェイスに直接アクセスする必要がある場合は、このポインターを使用します。

DAO を直接呼び出す方法については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

##  <a name="m_pworkspace"></a>CDaoDatabase:: m_pWorkspace

Database オブジェクトを含む[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)オブジェクトへのポインターを格納します。

### <a name="remarks"></a>コメント

ワークスペースに直接アクセスする必要がある場合 (たとえば、ワークスペースの Databases コレクション内の他のデータベースオブジェクトへのポインターを取得する場合) は、このポインターを使用します。

##  <a name="open"></a>  CDaoDatabase::Open

既存のデータベースを表す新しく構築された `CDaoDatabase` オブジェクトを初期化するには、このメンバー関数を呼び出す必要があります。

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
既存の Microsoft Jet () の名前を表す文字列式です。MDB) データベースファイル。 ファイル名に拡張子が付いている場合は必須です。 ネットワークで汎用名前付け規則 (UNC) がサポートされている場合は、ネットワークパスを指定することもできます。たとえば、"\\\\\\\MYSHARE\\\MYDIR\\\\\MYDB.MDB "。 ("\\" はC++エスケープ文字であるため、文字列リテラルには二重の円記号が必要です)。

*Lpszname*を使用する場合は、いくつかの考慮事項が適用されます。 次のようになります。

- は、既に別のユーザーによって排他アクセス用に開かれているデータベースを参照しています。 MFC は、 [CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローします。 この例外をトラップして、データベースが使用できないことをユーザーに知らせます。

- が空の文字列 ("") であり、 *Lpszconnect*が "ODBC;" である場合、ユーザーがデータベースを選択できるように、登録されているすべての ODBC データソース名を一覧表示するダイアログボックスが表示されます。 ODBC データソースへの直接接続は避ける必要があります。代わりに、アタッチされたテーブルを使用してください。

- それ以外の場合、既存のデータベースまたは有効な ODBC データソース名を参照していない場合、MFC は `CDaoException`型の例外をスローします。

> [!NOTE]
>  DAO エラーコードの詳細については、DAOERR を参照してください。H ファイル。 関連情報については、DAO ヘルプの「トラップ可能なデータアクセスエラー」を参照してください。

*bExclusive*<br/>
ブール値。データベースを排他 (非共有) アクセス用に開く場合は TRUE、データベースを共有アクセス用に開く場合は FALSE を指定します。 この引数を省略した場合、データベースは共有アクセス用に開かれます。

*bReadOnly*<br/>
ブール値。データベースが読み取り専用アクセスで開かれる場合は TRUE、データベースを読み取り/書き込みアクセス用に開く場合は FALSE です。 この引数を省略すると、データベースは読み取り/書き込みアクセス用に開かれます。 すべての依存レコードセットは、この属性を継承します。

*lpszConnect*<br/>
データベースを開くために使用される文字列式です。 この文字列は、ODBC 接続の引数を構成します。 ソース文字列を指定するには、排他および読み取り専用の引数を指定する必要があります。 データベースが Microsoft Jet データベース (.MDB)、この文字列は空 ("") です。 既定値の構文 ( **_T**("")) を使用すると、アプリケーションの ANSI ビルドに加えて、Unicode の移植性が提供されます。

### <a name="remarks"></a>コメント

`Open` によって、データベースが基になる DAO オブジェクトに関連付けられます。 データベースオブジェクトを使用して、レコードセット、テーブル、または定義オブジェクトを初期化するまで、そのオブジェクトを作成することはできません。 `Open`、関連付けられているワークスペースの Databases コレクションにデータベースオブジェクトを追加します。

次のようにパラメーターを使用します。

- Microsoft Jet を開いている場合 (MDB) データベースで、 *Lpszname*パラメーターを使用して、 *lpszname*パラメーターに空の文字列を渡すか、または ";" という形式のパスワード文字列を渡します。PWD = password "データベースがパスワードで保護されている場合 (MDB データベースのみ)。

- ODBC データソースを開いている場合は、 *Lpszconnect*に有効な odbc 接続文字列を渡し、 *lpszconnect*に空の文字列を渡します。

関連情報については、DAO ヘルプの「OpenDatabase メソッド」を参照してください。

> [!NOTE]
>  ISAM データベースや ODBC データソースなど、外部データベースにアクセスするときのパフォーマンスを向上させるには、Microsoft Jet エンジンデータベース () に外部データベーステーブルをアタッチすることをお勧めします。MDB) は、データソースに直接接続するのではなく、

たとえば、DBMS ホストが使用できない場合、接続のタイムアウトが発生する可能性があります。 接続試行が失敗した場合、`Open` は[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローします。

残りの解説は、ODBC データベースにのみ適用されます。

データベースが ODBC データベースであり、`Open` 呼び出しのパラメーターに接続を確立するための十分な情報が含まれていない場合、ODBC ドライバーはダイアログボックスを開き、ユーザーから必要な情報を取得します。 `Open`を呼び出すと、接続文字列の*Lpszconnect*がプライベートに格納され、 [getconnect](#getconnect)メンバー関数を呼び出すことによって使用できるようになります。

必要に応じて、独自のダイアログボックスを開いて、ユーザーからの情報 (パスワードなど) を取得し、その情報を `Open`に渡す接続文字列に追加する前 `Open` に、独自のダイアログボックスを開くことができます。 または、(通常は Windows レジストリに) 渡された接続文字列を保存して、次にアプリケーションが `CDaoDatabase` オブジェクトで `Open` を呼び出すときに再利用できるようにすることもできます。

また、複数のレベルのログイン認証 (それぞれ別の `CDaoDatabase` オブジェクト用) の接続文字列を使用したり、他のデータベース固有の情報を伝達したりすることもできます。

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

このメンバー関数を呼び出して、接続されているデータベースでの後続の操作がタイムアウトになるまでの既定の秒数を上書きします。

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>パラメーター

*nSeconds*<br/>
クエリ試行がタイムアウトするまでに許容される秒数。

### <a name="remarks"></a>コメント

ネットワークアクセスの問題、クエリの過剰な処理時間などが原因で、操作がタイムアウトすることがあります。 クエリのタイムアウト値を変更する場合は、レコードセットを開く前、またはレコードセットの[AddNew](../../mfc/reference/cdaorecordset-class.md#addnew)、 [Update](../../mfc/reference/cdaorecordset-class.md#update)、または[Delete](../../mfc/reference/cdaorecordset-class.md#delete)メンバー関数を呼び出す前に `SetQueryTimeout` を呼び出します。 この設定は、この[ オブジェクトに関連付けられているすべてのレコードセットに対して、それ以降のすべての](../../mfc/reference/cdaorecordset-class.md#open)オープン`AddNew`、`Update`、`Delete`、および`CDaoDatabase`呼び出しに影響します。 を開いた後でレコードセットのクエリタイムアウト値を変更しても、レコードセットの値は変更されません。 たとえば、後続の[移動](../../mfc/reference/cdaorecordset-class.md#move)操作では、新しい値は使用されません。

クエリタイムアウトの既定値は60秒です。 一部のデータベースでは、クエリのタイムアウト値を設定する機能がサポートされていません。 クエリのタイムアウト値を0に設定すると、タイムアウトは発生しません。データベースとの通信が応答しなくなる場合があります。 この動作は、開発時に便利な場合があります。

関連情報については、DAO ヘルプの「データのプロパティ」を参照してください。

## <a name="see-also"></a>参照

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace クラス](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset クラス](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef クラス](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException クラス](../../mfc/reference/cdaoexception-class.md)
