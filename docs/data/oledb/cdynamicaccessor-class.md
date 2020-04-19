---
title: CDynamicAccessor クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 19b8d0c86044e04cc60fd7aab89ec828c46f5fb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209298"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor クラス

データベース スキーマ (データベースの基になる構造) の知識があるない場合にデータ ソースにアクセスすることができます。

## <a name="syntax"></a>構文

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>必要条件

**ヘッダー**: atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddBindEntry](#addbindentry)|既定のアクセサーをオーバーライドする場合は、出力列にバインド エントリを追加します。|
|[CDynamicAccessor](#cdynamicaccessor)|インスタンスを作成し、初期化、`CDynamicAccessor`オブジェクト。|
|[閉じる](#close)|すべての列をバインド解除、割り当て済みのメモリを解放し、解放、 [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))クラスのインターフェイス ポインター。|
|[GetBlobHandling](#getblobhandling)|BLOB の処理の現在の行の値を取得します。|
|[GetBlobSizeLimit](#getblobsizelimit)|BLOB の最大サイズ (バイト単位) を取得します。|
|[GetBookmark](#getbookmark)|現在の行のブックマークを取得します。|
|[GetColumnCount](#getcolumncount)|行セットの列の数を取得します。|
|[GetColumnFlags](#getcolumnflags)|列の特性を取得します。|
|[GetColumnInfo](#getcolumninfo)|列のメタデータを取得します。|
|[GetColumnName](#getcolumnname)|指定した列の名前を取得します。|
|[GetColumnType](#getcolumntype)|指定された列のデータ型を取得します。|
|[GetLength](#getlength)|(バイト単位) の列の可能な最大長を取得します。|
|[GetOrdinal](#getordinal)|列名を指定された列インデックスを取得します。|
|[GetStatus](#getstatus)|指定された列の状態を取得します。|
|[GetValue](#getvalue)|バッファーからデータを取得します。|
|[SetBlobHandling](#setblobhandling)|BLOB の現在の行の値の処理を設定します。|
|[SetBlobSizeLimit](#setblobsizelimit)|BLOB の最大サイズをバイト単位で設定します。|
|[SetLength](#setlength)|列の長さをバイト単位で設定します。|
|[SetStatus](#setstatus)|指定された列の状態を設定します。|
|[SetValue](#setvalue)|バッファーにデータを格納します。|

## <a name="remarks"></a>Remarks

使用`CDynamicAccessor`列名、列数、データ型などの列情報を取得するメソッド。 この列の情報を使用するには、実行時に動的にアクセサーを作成します。

列情報が作成され、このクラスで管理されるバッファーに格納されます。 使用してバッファーからデータを取得[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)します。

動的アクセサー クラスの使用例とについては、次を参照してください。[動的アクセサーの使用](../../data/oledb/using-dynamic-accessors.md)します。

## <a name="addbindentry"></a> CDynamicAccessor::AddBindEntry

出力列にバインド エントリを追加します。

### <a name="syntax"></a>構文

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>パラメーター

*情報*<br/>
[in]A`DBCOLUMNINFO`列情報を含む構造体。 「DBCOLUMNINFO 構造体」を参照してください[icolumnsinfo::getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

作成された既定のアクセサーをオーバーライドする場合は、このメソッドを使用して`CDynamicAccessor`(を参照してください[データのフェッチを How Do I?](../../data/oledb/fetching-data.md))。

## <a name="cdynamicaccessor"></a> Cdynamicaccessor::cdynamicaccessor

インスタンスを作成し、初期化、`CDynamicAccessor`オブジェクト。

### <a name="syntax"></a>構文

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>パラメーター

*eBlobHandling*<br/>
バイナリ ラージ オブジェクト (BLOB) データの処理方法を指定します。 既定値は、DBBLOBHANDLING_DEFAULT です。 参照してください[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) DBBLOBHANDLINGENUM 値の説明をします。

*nBlobSize*<br/>
BLOB の最大サイズ (バイト単位)この値を列データは、BLOB として扱われます。 既定値は、8,000 です。 参照してください[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)詳細についてはします。

### <a name="remarks"></a>Remarks

初期化するために、コンス トラクターを使用する場合、`CDynamicAccessor`オブジェクト、Blob にバインドする方法を指定することができます。 Blob は、グラフィック、サウンド、またはコンパイル済みコードなどのバイナリ データを含めることができます。 既定の動作が Blob として 8,000 バイトを超える列を処理してにバインドするには、`ISequentialStream`オブジェクト。 ただし、BLOB のサイズに別の値を指定できます。

指定することも方法`CDynamicAccessor`BLOB データと見なされる列のデータの処理: 既定の方法で BLOB データを処理できます。 これを省略できます (バインドしない) または BLOB のデータ プロバイダーに割り当てられたメモリ内の BLOB データをバインドできます。

## <a name="close"></a> CDynamicAccessor::Close

すべての列をバインド解除、割り当て済みのメモリを解放し、解放、 [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))クラスのインターフェイス ポインター。

### <a name="syntax"></a>構文

```cpp
void Close() throw();
```

## <a name="getblobhandling"></a> CDynamicAccessor::GetBlobHandling

BLOB の処理の現在の行の値を取得します。

### <a name="syntax"></a>構文

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Remarks

BLOB の処理値を返します*eBlobHandling*によって設定[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)します。

## <a name="getblobsizelimit"></a> CDynamicAccessor::GetBlobSizeLimit

BLOB の最大サイズ (バイト単位) を取得します。

### <a name="syntax"></a>構文

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Remarks

BLOB の処理値を返します*nBlobSize*によって設定[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)します。

## <a name="getbookmark"></a> CDynamicAccessor::GetBookmark

現在の行のブックマークを取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>パラメーター

*pBookmark*<br/>
[out]ポインター、 [CBookmark](../../data/oledb/cbookmark-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

設定する必要がある`DBPROP_IRowsetLocate`に variant_true を設定すると、ブックマークを取得します。

## <a name="getcolumncount"></a> CDynamicAccessor::GetColumnCount

列の数を取得します。

### <a name="syntax"></a>構文

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>戻り値

列の数を取得します。

## <a name="getcolumnflags"></a> CDynamicAccessor::GetColumnFlags

列の特性を取得します。

### <a name="syntax"></a>構文

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pFlags*<br/>
[out]列の特性を記述するビットマスクへのポインター。 「DBCOLUMNFLAGS 列挙型」を参照してください[icolumnsinfo::getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

返します**true**列の特性が正常に取得される場合。 それ以外の場合は **false**を返します。

### <a name="remarks"></a>Remarks

列の番号は 1 つからオフセットします。 列 0 は特殊なケースでは、使用可能な場合、ブックマークになります。

## <a name="getcolumninfo"></a> CDynamicAccessor::GetColumnInfo

ほとんどのコンシューマーが必要な列のメタデータを返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>パラメーター

*pRowset*<br/>
[in]ポインター、 [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))インターフェイス。

*pColumns*<br/>
[out]行セットで列の数を返すメモリへのポインターこの数には、1 つを使用する必要がある場合に、ブックマーク列が含まれます。

*ppColumnInfo*<br/>
[out]配列を返すメモリへのポインター`DBCOLUMNINFO`構造体。 「DBCOLUMNINFO 構造体」を参照してください[icolumnsinfo::getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))で、 *OLE DB プログラマーズ リファレンス*します。

*ppStringsBuffer*<br/>
[out]すべての文字列値のストレージへのポインターを返すメモリへのポインター (内でいずれかの名前が使用*columnid*または*pwszName*) 1 つの割り当てブロック内で。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

参照してください[icolumnsinfo::getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))で、 *OLE DB プログラマーズ リファレンス*データ型について`DBORDINAL`、 `DBCOLUMNINFO`、および`OLECHAR`します。

## <a name="getcolumnname"></a> CDynamicAccessor::GetColumnName

指定された列の名前を取得します。

### <a name="syntax"></a>構文

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

### <a name="return-value"></a>戻り値

指定された列の名前。

## <a name="getcolumntype"></a> CDynamicAccessor::GetColumnType

指定された列のデータ型を取得します。

### <a name="syntax"></a>構文

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pType*<br/>
[out]指定された列のデータ型へのポインター。

### <a name="return-value"></a>戻り値

返します**true**成功した場合または**false**失敗します。

## <a name="getlength"></a> CDynamicAccessor::GetLength

指定された列の長さを取得します。

### <a name="syntax"></a>構文

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

*pLength*<br/>
[out]列のバイト単位の長さを表す整数を指すポインター。

### <a name="return-value"></a>戻り値

返します**true**指定された列が見つかった場合します。 この関数を返しますそれ以外の場合、 **false**します。

### <a name="remarks"></a>Remarks

最初のオーバーライドは、列番号を受け取り、2 番目と 3 番目のオーバーライドの列名から、ANSI または Unicode 形式でのそれぞれを。

## <a name="getordinal"></a> CDynamicAccessor::GetOrdinal

列名を指定された列番号を取得します。

### <a name="syntax"></a>構文

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>パラメーター

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

*pOrdinal*<br/>
[out]列の番号へのポインター。

### <a name="return-value"></a>戻り値

返します**true**指定した名前の列が見つかった場合します。 この関数を返しますそれ以外の場合、 **false**します。

## <a name="getstatus"></a> CDynamicAccessor::GetStatus

指定された列の状態を取得します。

### <a name="syntax"></a>構文

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

*pStatus*<br/>
[out]列の状態を格納する変数へのポインター。 参照してください[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*詳細についてはします。

### <a name="return-value"></a>戻り値

返します**true**指定された列が見つかった場合します。 この関数を返しますそれ以外の場合、 **false**します。

## <a name="getvalue"></a> CDynamicAccessor::GetValue

指定された列のデータを取得します。

### <a name="syntax"></a>構文

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>パラメーター

*ctype*<br/>
[in]文字列型を除く任意のデータ型を処理するテンプレート パラメーター (`CHAR*`、 `WCHAR*`)、特別な処理を必要とします。 `GetValue` ここでの指定に基づいて適切なデータ型を使用します。

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pColumnName*<br/>
[in]列の名前。

*pData*<br/>
[out]指定された列の内容へのポインター。

### <a name="return-value"></a>戻り値

文字列データを渡す場合は、template 宣言されていないバージョンを使用して、`GetValue`します。 このメソッドの template 宣言されていないバージョンを返す`void*`、指定された列のデータを格納しているバッファーの一部を表しています。 列が見つからない場合は、NULL を返します。

その他のすべてのデータ型は、テンプレート化されたバージョンを使用する方が簡単`GetValue`します。 テンプレート化されたバージョンを返す**true**成功した場合または**false**失敗します。

### <a name="remarks"></a>Remarks

Template 宣言されていないバージョンを使用して、文字列およびその他のデータ型を含む列のテンプレート化されたバージョンが含まれている列が返されます。

デバッグ モードの場合、アサーションを取得は、サイズの*pData*ポイントする列のサイズと等しくないです。

## <a name="setblobhandling"></a> CDynamicAccessor::SetBlobHandling

BLOB の現在の行の値の処理を設定します。

### <a name="syntax"></a>構文

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>パラメーター

*eBlobHandling*<br/>
BLOB データの処理方法を指定します。 次の値がかかることができます。

- DBBLOBHANDLING_DEFAULT:大きな列データを処理*nBlobSize* (によって設定`SetBlobSizeLimit`) と BLOB データだけで取得して、`ISequentialStream`または`IStream`オブジェクト。 このオプションはより大きなデータを格納しているすべての列をバインドしよう*nBlobSize* BLOB データとして DBTYPE_IUNKNOWN としてリストされているか。

- DBBLOBHANDLING_NOSTREAMS:大きな列データを処理*nBlobSize* (によって設定`SetBlobSizeLimit`) と BLOB データだけで、を通じてプロバイダーに割り当てられた、コンシューマーが所有しているメモリ内の参照を取得します。 このオプションは 1 つ以上の BLOB 列を持つテーブルに対して使用し、プロバイダーは、1 つだけサポート`ISequentialStream`アクセサーごとにオブジェクト。

- DBBLOBHANDLING_SKIP:スキップ (バインドしない) として Blob を含む修飾列 (アクセサーはないバインドまたは列の値を取得が列のステータスや長さも取得されます)。

### <a name="remarks"></a>Remarks

`SetBlobHandling` を呼び出してから `Open` を呼び出す必要があります。

コンス トラクター メソッド[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) BLOB 処理 DBBLOBHANDLING_DEFAULT に値を設定します。

## <a name="setblobsizelimit"></a> CDynamicAccessor::SetBlobSizeLimit

BLOB の最大サイズをバイト単位で設定します。

### <a name="syntax"></a>構文

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>パラメーター

*nBlobSize*<br/>
BLOB のサイズの上限を指定します。

### <a name="remarks"></a>Remarks

BLOB の最大サイズを設定 (バイト単位)この値より大きい列のデータは BLOB として扱われます。 一部のプロバイダーは、列 (2 GB) などの非常に大きなサイズを付与します。 このサイズの列のメモリの割り当てにしようとするではなく Blob としてこれらの列をバインドするとは通常します。 この方法で、すべてのメモリを割り当てる必要はありませんが、切り捨てに与えることがなく、すべてのデータの読み取りは引き続き可能です。 ただし、場合によっては強制するがある`CDynamicAccessor`ネイティブ データ型の大きな列をバインドします。 これを行うには、呼び出す`SetBlobSizeLimit`呼び出す前に`Open`します。

コンス トラクター メソッド[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) BLOB の最大サイズを 8,000 バイトの既定値に設定します。

## <a name="setlength"></a> CDynamicAccessor::SetLength

指定された列の長さを設定します。

### <a name="syntax"></a>構文

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*nLength*<br/>
[in]列のバイト単位の長さ。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

### <a name="return-value"></a>戻り値

返します**true**指定された列の長さは正常に設定されている場合。 この関数を返しますそれ以外の場合、 **false**します。

## <a name="setstatus"></a> CDynamicAccessor::SetStatus

指定された列の状態を設定します。

### <a name="syntax"></a>構文

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*status*<br/>
[in]列の状態。 参照してください[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*詳細についてはします。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

### <a name="return-value"></a>戻り値

返します**true**指定された列の状態が正常に設定されている場合。 この関数を返しますそれ以外の場合、 **false**します。

## <a name="setvalue"></a> CDynamicAccessor::SetValue

指定した列にデータを格納します。

### <a name="syntax"></a>構文

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype> 
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>パラメーター

*ctype*<br/>
[in]文字列型を除く任意のデータ型を処理するテンプレート パラメーター (`CHAR*`、 `WCHAR*`)、特別な処理を必要とします。 `GetValue` ここでの指定に基づいて適切なデータ型を使用します。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

*data*<br/>
[in]データを含むメモリへのポインター。

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

### <a name="return-value"></a>戻り値

文字列データを設定する場合は、template 宣言されていないバージョンを使用して、`GetValue`します。 このメソッドの template 宣言されていないバージョンを返す`void*`、指定された列のデータを格納しているバッファーの一部を表しています。 列が見つからない場合は、NULL を返します。

その他のすべてのデータ型は、テンプレート化されたバージョンを使用する方が簡単`GetValue`します。 テンプレート化されたバージョンを返す**true**成功した場合または**false**失敗します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor クラス](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor クラス](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor クラス](../../data/oledb/cmanualaccessor-class.md)