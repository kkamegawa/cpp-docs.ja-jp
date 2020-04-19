---
title: CDynamicParameterAccessor クラス
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: a655d95cf165ab2c5cba3a391b81d6f420f8322f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230867"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor クラス

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) と類似していますが、 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) インターフェイスを呼び出すことで設定されるパラメーター情報を取得します。

## <a name="syntax"></a>構文

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>必要条件

**ヘッダー**: atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|コンストラクターです。|
|[GetParam](#getparam)|バッファーからパラメーター データを取得します。|
|[GetParamCount](#getparamcount)|アクセサー内のパラメーターの数を取得します。|
|[GetParamIO](#getparamio)|指定されたパラメーターが入力または出力パラメーターであるかどうかを判断します。|
|[GetParamLength](#getparamlength)|バッファーに格納され、指定されたパラメーターの長さを取得します。|
|[GetParamName](#getparamname)|指定されたパラメーターの名前を取得します。|
|[GetParamStatus](#getparamstatus)|バッファーに格納され、指定されたパラメーターのステータスを取得します。|
|[GetParamString](#getparamstring)|バッファーに格納され、指定されたパラメーターの文字列データを取得します。|
|[GetParamType](#getparamtype)|指定されたパラメーターのデータ型を取得します。|
|[SetParam](#setparam)|パラメーター データを使用してバッファーを設定します。|
|[SetParamLength](#setparamlength)|バッファーに格納され、指定されたパラメーターの長さを設定します。|
|[SetParamStatus](#setparamstatus)|バッファーに格納され、指定されたパラメーターのステータスを設定します。|
|[SetParamString](#setparamstring)|バッファーに格納され、指定されたパラメーターの文字列データを設定します。|

## <a name="remarks"></a>Remarks

コンシューマーがこのクラスを使用するには、プロバイダーで `ICommandWithParameters` がサポートされている必要があります。

パラメーター情報は、このクラスによって作成および管理されるバッファーに格納されます。 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) と [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)を使用してバッファーからパラメーター データを取得します。

このクラスを使用して、SQL Server のストアド プロシージャを実行し、出力パラメーターの値を取得する方法を示す例では、次を参照してください、 [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)サンプル コード、 [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) 。GitHub のリポジトリ。

## <a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor::CDynamicParameterAccessor

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>パラメーター

*eBlobHandling*<br/>
BLOB データの処理方法を指定します。 既定値は、DBBLOBHANDLING_DEFAULT です。 参照してください[cdynamicaccessor::setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) DBBLOBHANDLINGENUM 値の説明をします。

*nBlobSize*<br/>
BLOB の最大サイズ (バイト単位)この値を列データは、BLOB として扱われます。 既定値は、8,000 です。 参照してください[cdynamicaccessor::setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)詳細についてはします。

### <a name="remarks"></a>Remarks

参照してください、 [cdynamicaccessor::cdynamicaccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) BLOB 処理の詳細については、コンス トラクター。

## <a name="getparam"></a> CDynamicParameterAccessor::GetParam

パラメーターのバッファーから指定したパラメーターの文字列以外のデータを取得します。

### <a name="syntax"></a>構文

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>パラメーター

*ctype*<br/>
データ型であるテンプレート パラメーター。

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pParamName*<br/>
[in]パラメーターの名前。

*pData*<br/>
[out]バッファーから取得されたデータを格納しているメモリへのポインター。

### <a name="return-value"></a>戻り値

Template 宣言されていないバージョンでは、バッファーからデータを含むメモリへのポインターを取得します。 テンプレート化されたバージョンでは、次のように返されます。 **true**成功した場合または**false**失敗します。

使用`GetParam`バッファーから文字列パラメーターのデータを取得します。 使用[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)バッファーから文字列パラメーターのデータを取得します。

## <a name="getparamcount"></a> CDynamicParameterAccessor::GetParamCount

バッファーに格納されているパラメーターの数を取得します。

### <a name="syntax"></a>構文

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>戻り値

パラメーターの数。

## <a name="getparamio"></a> CDynamicParameterAccessor::GetParamIO

指定されたパラメーターが入力または出力パラメーターであるかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pParamIO*<br/>
変数の格納先へのポインター、`DBPARAMIO`指定したパラメーターの型 (入力または出力)。 次のように定義されます。

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>戻り値

返します**true**成功した場合または**false**失敗します。

## <a name="getparamlength"></a> CDynamicParameterAccessor::GetParamLength

バッファーに格納され、指定されたパラメーターの長さを取得します。

### <a name="syntax"></a>構文

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pLength*<br/>
[out]指定したパラメーターの長さ (バイト単位) を格納する変数へのポインター。

### <a name="remarks"></a>Remarks

最初のオーバーライド**true**成功した場合または**false**失敗します。 2 番目のオーバーライド パラメーターの長さを格納しているメモリへのポインター。

## <a name="getparamname"></a> CDynamicParameterAccessor::GetParamName

指定されたパラメーターの名前を取得します。

### <a name="syntax"></a>構文

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

### <a name="return-value"></a>戻り値

指定されたパラメーターの名前。

## <a name="getparamstatus"></a> CDynamicParameterAccessor::GetParamStatus

バッファーに格納され、指定されたパラメーターのステータスを取得します。

### <a name="syntax"></a>構文

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pStatus*<br/>
[out]指定したパラメーターの DBSTATUS 状態を格納する変数へのポインター。 DBSTATUS 値については、次を参照してください。[状態](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*、または DBSTATUS oledb.h で検索します。

### <a name="remarks"></a>Remarks

最初のオーバーライド**true**成功した場合または**false**失敗します。 2 つ目は、指定されたパラメーターの状態を表すメモリへのポインターをオーバーライドします。

## <a name="getparamstring"></a> CDynamicParameterAccessor::GetParamString

バッファーに格納され、指定されたパラメーターの文字列データを取得します。

### <a name="syntax"></a>構文

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*strOutput*<br/>
[out]ANSI (`CSimpleStringA`) または Unicode (`CSimpleStringW`)、指定されたパラメーターのデータの文字列します。 型のパラメーターを渡す必要があります`CString`など。

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
[out]ANSI へのポインター (**CHAR**) または Unicode (**WCHAR**)、指定されたパラメーターのデータの文字列します。

*pMaxLen*<br/>
[out]バッファーのサイズへのポインターが指す*pBuffer* (文字数を含む、終端の NULL)。

### <a name="remarks"></a>Remarks

返します**true**成功した場合または**false**失敗します。

場合*pBuffer*が null の場合、このメソッドはによって示されるメモリ内で必要なバッファー サイズを設定*pMaxLen*戻って**true**データをコピーせずします。

このメソッドが失敗する場合、バッファー *pBuffer*文字列全体を格納するのに十分な大きさでないです。

使用`GetParamString`バッファーから文字列パラメーターのデータを取得します。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)バッファーから文字列パラメーターのデータを取得します。

## <a name="getparamtype"></a> CDynamicParameterAccessor::GetParamType

指定されたパラメーターのデータ型を取得します。

### <a name="syntax"></a>構文

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pType*<br/>
[out]指定したパラメーターのデータ型を格納する変数へのポインター。

### <a name="return-value"></a>戻り値

返します**true**成功した場合または**false**失敗します。

## <a name="setparam"></a> CDynamicParameterAccessor::SetParam

指定された (文字列以外の) データを使用してパラメーターのバッファーを設定します。

### <a name="syntax"></a>構文

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>パラメーター

*ctype*<br/>
データ型であるテンプレート パラメーター。

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 例:

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
[in]パラメーターの名前。

*pData*<br/>
[in]バッファーに書き込まれるデータを含むメモリへのポインター。

*status*<br/>
[in]DBSTATUS 列の状態。 DBSTATUS 値については、次を参照してください。[状態](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*、または DBSTATUS oledb.h で検索します。

### <a name="return-value"></a>戻り値

返します**true**成功した場合または**false**失敗します。

使用`SetParam`バッファーに文字列パラメーターのデータを設定します。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)をバッファーに文字列パラメーターのデータを設定します。

## <a name="setparamlength"></a> CDynamicParameterAccessor::SetParamLength

バッファーに格納され、指定されたパラメーターの長さを設定します。

### <a name="syntax"></a>構文

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*length*<br/>
[in]指定したパラメーターの長さを (バイト単位)。

### <a name="remarks"></a>Remarks

返します**true**成功した場合または**false**失敗します。

## <a name="setparamstatus"></a> CDynamicParameterAccessor::SetParamStatus

バッファーに格納され、指定されたパラメーターのステータスを設定します。

### <a name="syntax"></a>構文

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*status*<br/>
[in]指定したパラメーターの DBSTATUS 状態です。 DBSTATUS 値については、次を参照してください。[状態](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*、または DBSTATUS oledb.h で検索します。

### <a name="remarks"></a>Remarks

返します**true**成功した場合または**false**失敗します。

## <a name="setparamstring"></a> CDynamicParameterAccessor::SetParamString

バッファーに格納され、指定されたパラメーターの文字列データを設定します。

### <a name="syntax"></a>構文

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>パラメーター

*nParam*<br/>
[in]パラメーターの数 (1 からのオフセット)。 パラメーターの 0 は、戻り値については予約されています。 パラメーターの数は、SQL またはストアド プロシージャの呼び出し内での順序に基づくパラメーターのインデックスです。 参照してください[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)例についてはします。

*pString*<br/>
[in]ANSI へのポインター (**CHAR**) または Unicode (**WCHAR**)、指定されたパラメーターのデータの文字列します。 Oledb.h DBSTATUS を参照してください。

*status*<br/>
[in]指定したパラメーターの DBSTATUS 状態です。 DBSTATUS 値については、次を参照してください。[状態](/previous-versions/windows/desktop/ms722617(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*、または DBSTATUS oledb.h で検索します。

### <a name="remarks"></a>Remarks

返します**true**成功した場合または**false**失敗します。

`SetParamString` 指定した最大サイズを超える文字列を設定しようとする場合は失敗*pString*します。

使用`SetParamString`をバッファーに文字列パラメーターのデータを設定します。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)バッファーに文字列パラメーターのデータを設定します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor クラス](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor クラス](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor クラス](../../data/oledb/cmanualaccessor-class.md)