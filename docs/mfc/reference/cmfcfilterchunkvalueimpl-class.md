---
title: CMFCFilterChunkValueImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: b883d442342dd9fbbd074d9f8fcab76f81ef9864
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237559"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl クラス

これは、チャンクとプロパティの値のペアのロジックを単純化するクラスです。

## <a name="syntax"></a>構文

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|オブジェクトを破棄します。|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|ChunkValue をクリアします。|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|このチャンクをチャンクの特性を記述する構造体にコピーします。|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|その他の値からこのチャンク値を初期化します。|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|チャンクの GUID を取得します。|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|チャンクの PID (プロパティ ID) を取得します。|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|チャンクの種類を取得します。|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|文字列値を取得します。|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|割り当て済みの propvariant として値を取得します。|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|値を返しますに割り当てられた非 (内部値)。|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|このプロパティの値が有効かどうかどうかを確認します。|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|オーバーロードされます。 ブール値をキーにプロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|DWORD へのキー プロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|キー、filetime にプロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Int64 にキー プロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Int です。 キー プロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|キー長整数型にプロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|キーを SystemTime にプロパティを設定します。|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Unicode 文字列へのキー プロパティを設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|チャンクの共通プロパティを設定するヘルパー関数。|

## <a name="remarks"></a>Remarks

適切な種類の CMFCFilterChunkValueImpl クラスの作成だけを使用するには

例:

CMFCFilterChunkValueImpl チャンクです。

hr = chunk.SetBoolValue(PKEY_IsAttachment, true);

または

hr チャンクを = です。SetFileTimeValue (PKEY_ItemDate、ftLastModified)。

## <a name="inheritance-hierarchy"></a>継承階層

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear

ChunkValue をクリアします。

```
void Clear();
```

### <a name="remarks"></a>Remarks

##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

オブジェクトを構築します。

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Remarks

##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl

オブジェクトを破棄します。

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Remarks

##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk

このチャンクをチャンクの特性を記述する構造体にコピーします。

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>パラメーター

*pStatChunk*<br/>
チャンクの特性を記述する宛先値へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom

その他の値からこのチャンク値を初期化します。

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>パラメーター

*pValue*<br/>
コピーするソース値を指定します。

### <a name="remarks"></a>Remarks

##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID

チャンクの GUID を取得します。

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>戻り値

チャンクを識別する GUID への参照。

### <a name="remarks"></a>Remarks

##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID

チャンクの PID (プロパティ ID) を取得します。

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>戻り値

プロパティ ID を含む DWORD 値

### <a name="remarks"></a>Remarks

##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType

チャンクの種類を取得します。

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>戻り値

CHUNKSTATE 列挙値、現在のチャンクがテキスト型のプロパティまたは値型のプロパティであるかどうかを指定します。

### <a name="remarks"></a>Remarks

##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString

文字列値を取得します。

```
CString &GetString();
```

### <a name="return-value"></a>戻り値

チャンク値を含む文字列。

### <a name="remarks"></a>Remarks

##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue

割り当て済みの propvariant として値を取得します。

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>パラメーター

*ppPropVariant*<br/>
関数から制御が戻るときに、このパラメーターには、チャンクの値が含まれています。

### <a name="return-value"></a>戻り値

PROPVARIANT が正常に割り当てられているし、チャンクの値を正常にコピーする場合は S_OK *ppPropVariant*。 そうしないと、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc

非割り当て (内部値) の値を返します。

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>戻り値

現在のチャンク値を返します。

### <a name="remarks"></a>Remarks

##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid

このプロパティの値が有効かどうかどうかを確認します。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

現在のチャンク値が有効な場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue

オーバーロードされます。 ブール値をキーにプロパティを設定します。

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*bVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk

チャンクの共通プロパティを設定するヘルパー関数。

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合のエラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue

DWORD へのキーのプロパティを設定します。

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*dwVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue

キー、filetime にプロパティを設定します。

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*dtVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value

Int64 にキーによって、プロパティを設定します。

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*nVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue

Int です。 キー プロパティを設定します。

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*nVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue

キー長整数型にプロパティを設定します。

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*lVal*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue

キーを SystemTime にプロパティを設定します。

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*systemTime*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue

Unicode 文字列へのキー プロパティを設定します。

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>パラメーター

*鍵*<br/>
プロパティのキーを指定します。

*終端*<br/>
設定するチャンクの値を指定します。

*chunkType*<br/>
フラグは、このチャンクが text 型または値型のプロパティを含むかどうかを示します。 フラグの値は、CHUNKSTATE 列挙から取得されます。

*locale*<br/>
言語とサブ言語のテキストのチャンクに関連付けられています。 ドキュメント インデクサーによってチャンクのロケールを使用して、適切な単語がテキストの分割を実行できます。 チャンクが text 型でも VT_LPWSTR や: VT_LPSTR、VT_BSTR データ型の値型の場合は、このフィールドは無視されます。

*cwcLenSource*<br/>
現在のチャンクの派生元のソース テキストの文字の数。 値が 0 では、ソース テキストと派生のテキストの文字の対応を示します。 0 以外の値は、このような直接通信が存在しないことを意味します。

*cwcStartSource*<br/>
派生チャンクをソース テキストのソースのチャンクで起動元のオフセット。

*chunkBreakType*<br/>
現在のチャンクから前のチャンクを分ける区切りの型。 値は CHUNK_BREAKTYPE 列挙体です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
