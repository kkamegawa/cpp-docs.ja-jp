---
title: OLE DB コンシューマー テンプレート用マクロおよびグローバル関数
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: d4ed6b86d99cdfc272b5df10ede6af6bd05ed366
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361348"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB コンシューマー テンプレート用マクロおよびグローバル関数

OLE DB コンシューマー テンプレートには、次のマクロとグローバル関数が含まれます。

## <a name="global-functions"></a>グローバル関数

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|エラーが返された場合は、ダンプ デバイスに OLE DB エラー レコード情報をダンプします。|

## <a name="accessor-map-macros"></a>アクセサー マップに関するマクロ

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|アクセサーのエントリの先頭をマークします。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|アクセサー マップ エントリの開始位置を示します。|
|[END_ACCESSOR](#end_accessor)|アクセサーのエントリの終了を示します。|
|[END_ACCESSOR_MAP](#end_accessor_map)|アクセサー マップ エントリの終了を示します。|

## <a name="column-map-macros"></a>列マップに関するマクロ

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|ユーザー レコード クラス内の列のマップ エントリの先頭をマークします。|
|[BLOB_ENTRY](#blob_entry)|バイナリ ラージ オブジェクト (BLOB) をバインドするために使用します。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|BLOB のデータ列の長さを報告します。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|長さと BLOB のデータ列のステータスを報告します。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|BLOB のデータ列のステータスを報告します。|
|[BLOB_NAME](#blob_name)|列名で、バイナリ ラージ オブジェクトをバインドするために使用します。|
|[BLOB_NAME_LENGTH](#blob_name_length)|BLOB のデータ列の長さを報告します。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|長さと BLOB のデータ列のステータスを報告します。|
|[BLOB_NAME_STATUS](#blob_name_status)|BLOB のデータ列のステータスを報告します。|
|[BOOKMARK_ENTRY](#bookmark_entry)|行セットに対してブックマーク エントリを表します。 ブックマークのエントリは、列のエントリの特別な種類です。|
|[COLUMN_ENTRY](#column_entry)|データベースの特定の列へのバインドを表します。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|データベースの特定の列へのバインドを表します。 サポート*型*、*長さ*、*精度*、*スケール*、および*状態*パラメーター。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|データベースの特定の列へのバインドを表します。 では、*長さ*変数。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|データベースの特定の列へのバインドを表します。 サポート*状態*と*長さ*パラメーター。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|データベースの特定の列へのバインドを表します。 サポート*精度*と*スケール*パラメーター。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|データベースの特定の列へのバインドを表します。 サポート、*長さ*変数*精度*と*スケール*パラメーター。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|データベースの特定の列へのバインドを表します。 サポート*状態*と*長さ*変数、*精度*と*スケール*パラメーター。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|データベースの特定の列へのバインドを表します。 サポート、*状態*変数*精度*と*スケール*パラメーター。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|データベースの特定の列へのバインドを表します。 では、*状態*変数。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|データベースの特定の列へのバインドを表します。 サポート*型*パラメーター。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|データベースの特定の列へのバインドを表します。 サポート*型*と*サイズ*パラメーター。|
|[COLUMN_NAME](#column_name)|名前で、データベースの特定の列へのバインドを表します。|
|[COLUMN_NAME_EX](#column_name_ex)|名前で、データベースの特定の列へのバインドを表します。 データ型、サイズ、桁数、小数点、列の長さ、および列の状態の仕様をサポートしています。|
|[COLUMN_NAME_LENGTH](#column_name_length)|名前で、データベースの特定の列へのバインドを表します。 列の長さの仕様をサポートしています。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|名前で、データベースの特定の列へのバインドを表します。 列の長さと状態の仕様をサポートしています。|
|[COLUMN_NAME_PS](#column_name_ps)|名前で、データベースの特定の列へのバインドを表します。 有効桁数と小数点の仕様をサポートしています。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|名前で、データベースの特定の列へのバインドを表します。 有効桁数、小数点、および列の長さの仕様をサポートしています。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|名前で、データベースの特定の列へのバインドを表します。 有効桁数、小数点、列の長さ、および列の状態の仕様をサポートしています。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|名前で、データベースの特定の列へのバインドを表します。 有効桁数、小数点、および列の状態の仕様をサポートしています。|
|[COLUMN_NAME_STATUS](#column_name_status)|名前で、データベースの特定の列へのバインドを表します。 列の状態の仕様をサポートしています。|
|[COLUMN_NAME_TYPE](#column_name_type)|名前で、データベースの特定の列へのバインドを表します。 データ型の仕様をサポートしています。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|名前で、データベースの特定の列へのバインドを表します。 データ型、有効桁数、およびスケールの仕様をサポートしています。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|名前で、データベースの特定の列へのバインドを表します。 データ型とサイズの仕様をサポートしています。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|名前で、データベースの特定の列へのバインドを表します。 データ型と列の状態の仕様をサポートしています。|
|[END_COLUMN_MAP](#end_column_map)|列マップ エントリの終了を示します。|

## <a name="command-macros"></a>コマンド マクロ

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|使用する場合、行セットを作成するために使用するコマンドを指定します、 [CCommand](../../data/oledb/ccommand-class.md)クラス。 指定したアプリケーションの種類 (ANSI または Unicode) に一致する文字列型のみを受け入れます。 使用することをお勧め[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) DEFINE_COMMAND の代わりにします。|
|[DEFINE_COMMAND_EX](#define_command_ex)|使用する場合、行セットを作成するために使用するコマンドを指定します、 [CCommand](../../data/oledb/ccommand-class.md)クラス。 ANSI および Unicode のアプリケーションをサポートしています。|

## <a name="parameter-map-macros"></a>パラメーターのマップに関するマクロ

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|ユーザー レコード クラスのパラメーターのマップ エントリの先頭をマークします。|
|[END_PARAM_MAP](#end_param_map)|パラメーターのマップ エントリの終了を示します。|
|[SET_PARAM_TYPE](#set_param_type)|入力、出力、または入力/出力として SET_PARAM_TYPE マクロに続く COLUMN_ENTRY マクロを指定します。|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

エラーが返された場合は、ダンプ デバイスに OLE DB エラー レコード情報をダンプします。

#### <a name="syntax"></a>構文

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>パラメーター

*だ*<br/>
[in]OLE DB コンシューマー テンプレートのメンバー関数によって返される HRESULT です。

#### <a name="remarks"></a>Remarks

場合*だ*は S_OK、`AtlTraceErrorRecords`ダンプ デバイスに OLE DB エラー レコード情報をダンプ (、**デバッグ**ファイルまたは出力ウィンドウのタブ)。 プロバイダーから取得されるエラー レコード情報には、各エラー レコード エントリの行番号、ソース、説明、ヘルプ ファイル、コンテキスト、および GUID が含まれます。 `AtlTraceErrorRecords` デバッグ ビルドでのみこの情報をダンプします。 リリース ビルドでは、out に最適化された空のスタブを勧めします。詳細については、次を参照してください。 [CDBErrorInfo クラス](../../data/oledb/cdberrorinfo-class.md)します。

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

アクセサーのエントリの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>パラメーター

*num*<br/>
[in]このアクセサー マップのアクセサーのゼロ オフセット番号。

*bAuto*<br/>
[in]このアクセサーが自動アクセサーまたは手動のアクセサーを指定します。 場合**true**場合、アクセサーが自動; **false**アクセサーは手動で行います。 自動アクセサーでは、移動操作でデータをフェッチすることを意味します。

#### <a name="remarks"></a>Remarks

行セットの複数アクセサーの場合は、BEGIN_ACCESSOR_MAP を指定して、個々 のアクセサーに対して BEGIN_ACCESSOR マクロを使用する必要があります。 END_ACCESSOR マクロ BEGIN_ACCESSOR マクロが入力されます。 END_ACCESSOR_MAP マクロ BEGIN_ACCESSOR_MAP マクロが入力されます。

#### <a name="example"></a>例

参照してください[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)します。

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

アクセサー マップ エントリの開始位置を示します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>パラメーター

*x*<br/>
[入力] ユーザー レコード クラスの名前。

*num*<br/>
[入力] このアクセサー マップのアクセサーの数。

#### <a name="remarks"></a>Remarks

行セットの複数アクセサーの場合は、先頭 BEGIN_ACCESSOR_MAP を指定し、個々 のアクセサーに対して BEGIN_ACCESSOR マクロを使用する必要があります。 END_ACCESSOR マクロ BEGIN_ACCESSOR マクロが入力されます。 END_ACCESSOR_MAP マクロ アクセサー マップが完了しました。

ユーザー レコードに含まれるアクセサーが 1 つのみの場合は、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)マクロを使用します。

#### <a name="example"></a>例

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a> END_ACCESSOR

アクセサーのエントリの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Remarks

行セットに対して複数のアクセサー、BEGIN_ACCESSOR_MAP を指定し、個々 のアクセサーに対して BEGIN_ACCESSOR マクロを使用する必要があります。 END_ACCESSOR マクロ BEGIN_ACCESSOR マクロが入力されます。 END_ACCESSOR_MAP マクロ BEGIN_ACCESSOR_MAP マクロが入力されます。

#### <a name="example"></a>例

参照してください[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)します。

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

アクセサー マップ エントリの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Remarks

行セットに対して複数のアクセサー、BEGIN_ACCESSOR_MAP を指定し、個々 のアクセサーに対して BEGIN_ACCESSOR マクロを使用する必要があります。 END_ACCESSOR マクロ BEGIN_ACCESSOR マクロが入力されます。 END_ACCESSOR_MAP マクロ BEGIN_ACCESSOR_MAP マクロが入力されます。

#### <a name="example"></a>例

参照してください[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)します。

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

列マップ エントリの先頭を示します。

#### <a name="syntax"></a>構文

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>パラメーター

*x*<br/>
[入力] `CAccessor`から派生したユーザー レコード クラスの名前。

#### <a name="remarks"></a>Remarks

このマクロは、行セットに対してアクセサーが 1 つしか必要ない場合に使用します。 1 つの行セットに対して複数のアクセサーが必要な場合は、 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)を使用します。

END_COLUMN_MAP マクロ BEGIN_COLUMN_MAP マクロが入力されます。 このマクロは、ユーザー レコードで 1 つのアクセサーだけが必要な場合に使用します。

列は、バインドする行セットのフィールドに相当します。

#### <a name="example"></a>例

列およびパラメーター マップのコード例を次に示します。

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。

#### <a name="syntax"></a>構文

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="example"></a>例

参照してください[BLOB を取得する方法でしょうか。](../../data/oledb/retrieving-a-blob.md)します。

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_ENTRY](../../data/oledb/blob-entry.md)も、このマクロは、BLOB 列のバイトの長さを取得する点を除いて、します。

#### <a name="syntax"></a>構文

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[out]BLOB 列の (実際) の長さ (バイト単位)。

#### <a name="example"></a>例

参照してください[BLOB を取得する方法でしょうか。](../../data/oledb/retrieving-a-blob.md)します。

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_ENTRY](../../data/oledb/blob-entry.md)ただし、このマクロは、長さと、BLOB 列の状態も取得します。

#### <a name="syntax"></a>構文

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[out]BLOB 列の (実際) の長さ (バイト単位)。

*status*<br/>
[out]BLOB のデータ列の状態。

#### <a name="example"></a>例

参照してください[BLOB を取得する方法でしょうか。](../../data/oledb/retrieving-a-blob.md)します。

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

バイナリ ラージ オブジェクトをバインドする BEGIN_COLUMN_MAP または BEGIN_ACCESSOR_MAP と共に使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_ENTRY](../../data/oledb/blob-entry.md)ただし、このマクロは、BLOB 列の状態も取得します。

#### <a name="syntax"></a>構文

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[out]BLOB フィールドの状態です。

#### <a name="example"></a>例

参照してください[BLOB を取得する方法でしょうか。](../../data/oledb/retrieving-a-blob.md)します。

### <a name="blob_name"></a> BLOB_NAME

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_ENTRY](../../data/oledb/blob-entry.md)このマクロは列番号ではなく列名を点が異なります。

#### <a name="syntax"></a>構文

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="example"></a>例

参照してください[BLOB を取得する方法でしょうか。](../../data/oledb/retrieving-a-blob.md)します。

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_NAME](../../data/oledb/blob-name.md)も、このマクロは、BLOB のデータ列のバイトの長さを取得する点を除いて、します。

#### <a name="syntax"></a>構文

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[out]BLOB 列の (実際) の長さ (バイト単位)。

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_NAME](../../data/oledb/blob-name.md)ただし、このマクロは、長さと BLOB のデータ列の状態も取得します。

#### <a name="syntax"></a>構文

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[out]BLOB 列の (実際) の長さ (バイト単位)。

*status*<br/>
[out]BLOB フィールドの状態です。

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

BEGIN_COLUMN_MAP と END_COLUMN_MAP バイナリ ラージ オブジェクトをバインドするために使用 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85)))。 ような[BLOB_NAME](../../data/oledb/blob-name.md)ただし、このマクロでは、BLOB のデータ列の状態も取得します。

#### <a name="syntax"></a>構文

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*IID*<br/>
[in]など、GUID をインターフェイス`IDD_ISequentialStream`BLOB の取得に使用されます。

*flags*<br/>
[in]OLE 構造化ストレージ モデルで定義されているストレージ モード フラグを設定 (たとえば、 `STGM_READ`)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[out]BLOB フィールドの状態です。

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

ブックマーク列をバインドします。

#### <a name="syntax"></a>構文

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>パラメーター

*variable*<br/>
[in]ブックマーク列にバインドする変数です。

#### <a name="example"></a>例

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

詳細については、次を参照してください。[ブックマークを使って](using-bookmarks.md)と[CBookmark クラス](../../data/oledb/cbookmark-class.md)します。

### <a name="column_entry"></a> COLUMN_ENTRY

行セットの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

COLUMN_ENTRY マクロは、次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

#### <a name="example"></a>例

マクロのトピックで例を参照して[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)します。

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*wType*<br/>
[in]データ型。

*nLength*<br/>
[in]データ サイズ (バイト単位)。

*nPrecision*<br/>
[in]データを取得するときに使用する最大有効桁数と*wType*は`DBTYPE_NUMERIC`します。 それ以外の場合、このパラメーターは無視されます。

*nScale*<br/>
[in]データを取得するときに使用するスケールと*wType*は`DBTYPE_NUMERIC`または`DBTYPE_DECIMAL`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

COLUMN_ENTRY_EX マクロは、次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

#### <a name="example"></a>例

参照してください[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)します。

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]以降では、1 つの列数。 ブックマークは、列 0 に対応します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

#### <a name="remarks"></a>Remarks

このマクロをサポートしています、*長さ*変数。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

長さと状態変数をサポートする場合は、このマクロを使用します。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

行セットの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

精度とバインドする列の小数点以下桁数を指定することができます。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]以降では、1 つの列数。 ブックマークは、列 0 に対応します。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

#### <a name="remarks"></a>Remarks

精度とバインドする列の小数点以下桁数を指定することができます。 このマクロをサポートしています、*長さ*変数。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

精度とバインドする列の小数点以下桁数を指定することができます。 長さと状態変数をサポートする場合は、このマクロを使用します。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

精度とバインドする列の小数点以下桁数を指定することができます。 このマクロをサポートしています、*状態*変数。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

データベースの特定の列を行セットのバインディングを表します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>パラメーター

参照してください[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

*nOrdinal*<br/>
[in]列の番号。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

このマクロをサポートしています、*状態*変数。 次の場所で使用されます。

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

データベースの特定の列へのバインドを表します。 サポート*型*パラメーター。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*wType*<br/>
[in]列のエントリのデータ型。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

このマクロの特殊なバリアントは、 [COLUMN_ENTRY](../../data/oledb/column-entry.md)マクロのデータ型を指定する手段を提供します。

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

データベースの特定の列へのバインドを表します。 サポート*型*と*サイズ*パラメーター。

#### <a name="syntax"></a>構文

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>パラメーター

*nOrdinal*<br/>
[in]列の番号。

*wType*<br/>
[in]列のエントリのデータ型。

*nLength*<br/>
[in] (バイト単位) の列のエントリのサイズです。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

このマクロの特殊なバリアントは、 [COLUMN_ENTRY](../../data/oledb/column-entry.md)データ サイズと種類を指定する手段を提供するマクロ。

### <a name="column_name"></a> COLUMN_NAME

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_ENTRY](../../data/oledb/column-entry.md)このマクロは列番号ではなく、列名を点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

COLUMN_NAME_ のマクロと同じ場所で使用される[COLUMN_ENTRY](../../data/oledb/column-entry.md):

- 間、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)と[END_COLUMN_MAP](../../data/oledb/end-column-map.md)マクロ。

- 間、 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)と[END_ACCESSOR](../../data/oledb/end-accessor.md)マクロ。

- 間、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)と[END_PARAM_MAP](../../data/oledb/end-param-map.md)マクロ。

### <a name="column_name_ex"></a> COLUMN_NAME_EX

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)このマクロは、データ型、サイズ、桁数、小数点、列の長さ、および列の状態にも受け取ることを除いて、します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*wType*<br/>
[in]データ型。

*nLength*<br/>
[in]データ サイズ (バイト単位)。

*nPrecision*<br/>
[in]データを取得するときに使用する最大有効桁数と*wType*は`DBTYPE_NUMERIC`します。 それ以外の場合、このパラメーターは無視されます。

*nScale*<br/>
[in]データを取得するときに使用するスケールと*wType*は`DBTYPE_NUMERIC`または`DBTYPE_DECIMAL`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、列の長さを点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)このマクロは、列の長さと列の状態にも受け取ることを除いて、します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_ps"></a> COLUMN_NAME_PS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)このマクロは有効桁数と小数点も受け取ることを除いて、します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、有効桁数、小数点、および列の長さを点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md), このマクロは、有効桁数、小数点、列の長さ、および列の状態にもは点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*length*<br/>
[in]列の長さにバインドする変数です。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、有効桁数、小数点、および列の状態を点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*nPrecision*<br/>
[in]バインドする列の最大有効桁数。

*nScale*<br/>
[in]バインドする列の小数点以下桁数。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、列の状態を点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

*status*<br/>
[in]列の状態にバインドする変数です。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、データ型を点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*wType*<br/>
[in]データ型。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)このマクロは、データ型、有効桁数、およびスケールにも受け取ることを除いて、します。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*wType*<br/>
[in]データ型。

*nPrecision*<br/>
[in]データを取得するときに使用する最大有効桁数と*wType*は`DBTYPE_NUMERIC`します。 それ以外の場合、このパラメーターは無視されます。

*nScale*<br/>
[in]データを取得するときに使用するスケールと*wType*は`DBTYPE_NUMERIC`または`DBTYPE_DECIMAL`します。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md), このマクロは、データ型とサイズにもかかる点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*wType*<br/>
[in]データ型。

*nLength*<br/>
[in]データ サイズ (バイト単位)。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

行セットの特定の列を行セットのバインディングを表します。 ような[COLUMN_NAME](../../data/oledb/column-name.md)また、このマクロは、データ型と列の状態を点が異なります。

#### <a name="syntax"></a>構文

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>パラメーター

*pszName*<br/>
[in]列の名前へのポインター。 名前は、Unicode 文字列にする必要があります。 たとえば、名前の前に 'L' を配置することでこれを実現できます。`L"MyColumn"`します。

*wType*<br/>
[in]データ型。

*status*<br/>
[in]列の状態にバインドする変数です。

*data*<br/>
[in]ユーザー レコードに対応するデータ メンバー。

#### <a name="remarks"></a>Remarks

参照してください[COLUMN_NAME](../../data/oledb/column-name.md) COLUMN_NAME_ のマクロが使用されているについて。

### <a name="end_column_map"></a> END_COLUMN_MAP

列マップ エントリの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Remarks

行セットに対してアクセサーが 1 つで使用されます。 END_COLUMN_MAP マクロ BEGIN_COLUMN_MAP マクロが入力されます。

#### <a name="example"></a>例

参照してください[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)します。

### <a name="define_command"></a> DEFINE_COMMAND

使用する場合、行セットを作成するために使用するコマンドを指定します、 [CCommand](../../data/oledb/ccommand-class.md)クラス。 指定したアプリケーションの種類 (ANSI または Unicode) に一致する文字列型のみを受け入れます。

> [!NOTE]
>  使用することをお勧め[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) DEFINE_COMMAND の代わりにします。

#### <a name="syntax"></a>構文

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>パラメーター

*x*<br/>
[in]ユーザー レコード (コマンド) クラスの名前。

*szCommand*<br/>
[in]使用する場合、行セットの作成に使用されるコマンド文字列[CCommand](../../data/oledb/ccommand-class.md)します。

#### <a name="remarks"></a>Remarks

指定したコマンド文字列は、コマンド テキストを指定しない場合は、既定として使用されます、 [ccommand::open](../../data/oledb/ccommand-open.md)メソッド。

このマクロは Unicode としてアプリケーションをビルドする場合、ANSI としてアプリケーションをビルドする場合、ANSI 文字列または Unicode 文字列を受け取ります。 使用することをお勧め[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) DEFINE_COMMAND ではなく、以前は ANSI または Unicode アプリケーションの種類に関係なく、Unicode 文字列を受け入れるため。

#### <a name="example"></a>例

参照してください[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)します。

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

使用する場合、行セットを作成するために使用するコマンドを指定します、 [CCommand](../../data/oledb/ccommand-class.md)クラス。 Unicode と ANSI のアプリケーションをサポートしています。

#### <a name="syntax"></a>構文

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>パラメーター

*x*<br/>
[in]ユーザー レコード (コマンド) クラスの名前。

*wszCommand*<br/>
[in]使用する場合、行セットの作成に使用されるコマンド文字列[CCommand](../../data/oledb/ccommand-class.md)します。

#### <a name="remarks"></a>Remarks

指定したコマンド文字列は、コマンド テキストを指定しない場合は、既定として使用されます、 [ccommand::open](../../data/oledb/ccommand-open.md)メソッド。

このマクロは、アプリケーションの種類に関係なく、Unicode 文字列を受け取ります。 このマクロは優先[DEFINE_COMMAND](../../data/oledb/define-command.md) Unicode をサポートしているためと ANSI アプリケーション。

#### <a name="example"></a>例

参照してください[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)します。

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

パラメーターのマップ エントリの先頭をマークします。

#### <a name="syntax"></a>構文

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>パラメーター

*x*<br/>
[入力] ユーザー レコード クラスの名前。

#### <a name="remarks"></a>Remarks

パラメーターの使用は[コマンド](/previous-versions/windows/desktop/ms724608(v=vs.85))します。

#### <a name="example"></a>例

例をご覧ください、 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)マクロ。

### <a name="end_param_map"></a> END_PARAM_MAP

パラメーターのマップ エントリの終了を示します。

#### <a name="syntax"></a>構文

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>例

例をご覧ください、 [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)マクロ。

### <a name="set_param_type"></a> SET_PARAM_TYPE

SET_PARAM_TYPE マクロが入力、出力、または入力/出力に続く COLUMN_ENTRY マクロを指定します。

#### <a name="syntax"></a>構文

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>パラメーター

*type*<br/>
[入力] 設定するパラメーターの種類。

#### <a name="remarks"></a>Remarks

プロバイダーは、基になるデータ ソースによってサポートされているパラメーター入出力タイプだけをサポートします。 種類は、1 つ以上を組み合わせた`DBPARAMIO`値 (を参照してください[DBBINDING 構造体](/previous-versions/windows/desktop/ms716845(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*)。

- `DBPARAMIO_NOTPARAM` アクセサーにパラメーターがありません。 通常、設定`eParamIO`行アクセサーは、ユーザーに通知するパラメーターを無視することで、この値にします。

- `DBPARAMIO_INPUT` 入力パラメーター。

- `DBPARAMIO_OUTPUT` 出力パラメーター。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` パラメーターでは、入力と出力パラメーターの両方です。

#### <a name="example"></a>例

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート用マクロおよびグローバル関数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)