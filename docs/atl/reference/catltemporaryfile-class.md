---
title: CAtlTemporaryFile クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: d6a7a61d1886a264f8575e8d7325d6639d21338d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497713"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile クラス

このクラスには、一時ファイルを作成して使用するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlTemporaryFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|コンストラクターです。|
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlTemporaryFile:: Close](#close)|一時ファイルを閉じ、その内容を削除するか、指定したファイル名で格納します。|
|[CAtlTemporaryFile::Create](#create)|一時ファイルを作成するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: Flush](#flush)|ファイルバッファーに残っているデータを一時ファイルに強制的に書き込むには、このメソッドを呼び出します。|
|[CAtlTemporaryFile::GetPosition](#getposition)|現在のファイルポインターの位置を取得するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: GetSize](#getsize)|このメソッドを呼び出して、一時ファイルのサイズ (バイト単位) を取得します。|
|[CAtlTemporaryFile::HandsOff](#handsoff)|`CAtlTemporaryFile`オブジェクトからファイルの関連付けを解除するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: ハンドラー Son](#handson)|このメソッドを呼び出して、既存の一時ファイルを開き、ポインターをファイルの末尾に配置します。|
|[CAtlTemporaryFile::LockRange](#lockrange)|他のプロセスがアクセスできないように、ファイル内の領域をロックするには、このメソッドを呼び出します。|
|[CAtlTemporaryFile::Read](#read)|ファイルポインターによって示される位置から開始して、一時ファイルからデータを読み取るには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: Seek](#seek)|一時ファイルのファイルポインターを移動するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: SetSize](#setsize)|一時ファイルのサイズを設定するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|一時ファイルの名前を返すには、このメソッドを呼び出します。|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|一時ファイルの領域をロック解除するには、このメソッドを呼び出します。|
|[CAtlTemporaryFile:: Write](#write)|ファイルポインターによって示される位置から開始して、一時ファイルにデータを書き込むには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlTemporaryFile:: operator ハンドル](#operator_handle)|一時ファイルへのハンドルを返します。|

## <a name="remarks"></a>Remarks

`CAtlTemporaryFile`では、一時ファイルの作成と使用が簡単になります。 ファイルは、自動的に名前が付けられ、開いて閉じられ、削除されます。 ファイルが閉じられた後にファイルの内容が必要な場合は、指定した名前の新しいファイルに保存できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlfile .h

## <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

コンストラクターです。

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Remarks

[CAtlTemporaryFile:: Create](#create)が呼び出されるまで、ファイルは実際には開かれません。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile

デストラクターです。

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Remarks

デストラクターは[CAtlTemporaryFile:: Close](#close)を呼び出します。

##  <a name="close"></a>  CAtlTemporaryFile::Close

一時ファイルを閉じ、その内容を削除するか、指定したファイル名で格納します。

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*szNewName*<br/>
一時ファイルの内容を格納する新しいファイルの名前。 この引数が NULL の場合、一時ファイルの内容は削除されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="create"></a>  CAtlTemporaryFile::Create

一時ファイルを作成するには、このメソッドを呼び出します。

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>パラメーター

*pszDir*<br/>
一時ファイルのパス。 NULL の場合は、パスを割り当てるために[GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)が呼び出されます。

*dwDesiredAccess*<br/>
目的のアクセス。 Windows SDK の[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)の*dwDesiredAccess*を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="flush"></a>CAtlTemporaryFile:: Flush

ファイルバッファーに残っているデータを一時ファイルに強制的に書き込むには、このメソッドを呼び出します。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlTemporaryFile:: HandsOff](#handsoff)に似ていますが、ファイルが閉じられていない点が異なります。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

現在のファイルポインターの位置を取得するには、このメソッドを呼び出します。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
バイト単位の位置。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

ファイルポインターの位置を変更するには、 [CAtlTemporaryFile:: Seek](#seek)を使用します。

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

このメソッドを呼び出して、一時ファイルのサイズ (バイト単位) を取得します。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>パラメーター

*nLen*<br/>
ファイル内のバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff

`CAtlTemporaryFile`オブジェクトからファイルの関連付けを解除するには、このメソッドを呼び出します。

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

`HandsOff`また、 [CAtlTemporaryFile::](#handson)の場合、オブジェクトからファイルの関連付けを解除し、必要に応じて再アタッチするために使用されます。 `HandsOff`は、ファイルバッファーに残っているすべてのデータを一時ファイルに強制的に書き込み、ファイルを閉じます。 ファイルを完全に閉じて削除する場合、または指定した名前のファイルの内容を閉じて保持する場合は、 [CAtlTemporaryFile:: close](#close)を使用します。

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

このメソッドを呼び出して、既存の一時ファイルを開き、ポインターをファイルの末尾に配置します。

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlTemporaryFile:: HandsOff](#handsoff)および`HandsOn`は、オブジェクトからのファイルの関連付けを解除するために使用され、必要に応じて再アタッチします。

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

他のプロセスがアクセスできないように、一時ファイル内の領域をロックするには、このメソッドを呼び出します。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
ロックを開始するファイル内の位置。

*nCount*<br/>
ロックするバイト範囲の長さ。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

ファイル内のバイトをロックすると、他のプロセスがそれらのバイトにアクセスできなくなります。 ファイルの複数の領域をロックすることはできますが、重複する領域は許可されません。 領域のロックを正常に解除するには、 [CAtlTemporaryFile:: UnlockRange](#unlockrange)を使用します。これにより、バイト範囲が以前にロックされていた領域と完全に一致することが保証されます。 `LockRange`隣接する領域をマージしません。2つのロックされた領域が隣接している場合は、それぞれを個別にロック解除する必要があります。

##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator HANDLE

一時ファイルへのハンドルを返します。

```
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

ファイルポインターによって示される位置から開始して、一時ファイルからデータを読み取るには、このメソッドを呼び出します。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>パラメーター

*pBuffer*<br/>
ファイルから読み取られたデータを受け取るバッファーへのポインター。

*nBufSize*<br/>
バイト単位のバッファー サイズ。

*nBytesRead*<br/>
読み取られたバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlFile:: Read](../../atl/reference/catlfile-class.md#read)を呼び出します。 ファイルポインターの位置を変更するには、 [CAtlTemporaryFile:: Seek](#seek)を呼び出します。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

一時ファイルのファイルポインターを移動するには、このメソッドを呼び出します。

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>パラメーター

*nOffset*<br/>
*Dwfrom*によって指定された開始点からのオフセット (バイト単位)。

*dwFrom*<br/>
開始点 (FILE_BEGIN、FILE_CURRENT、または FILE_END)。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlFile:: Seek](../../atl/reference/catlfile-class.md#seek)を呼び出します。 現在のファイルポインターの位置を取得するには、 [CAtlTemporaryFile:: GetPosition](#getposition)を呼び出します。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

一時ファイルのサイズを設定するには、このメソッドを呼び出します。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>パラメーター

*nNewLen*<br/>
ファイルの新しい長さ (バイト単位)。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlFile:: SetSize](../../atl/reference/catlfile-class.md#setsize)を呼び出します。 返されると、ファイルポインターがファイルの末尾に配置されます。

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

一時ファイルの名前を返すには、このメソッドを呼び出します。

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>戻り値

ファイル名を指す LPCTSTR を返します。

### <a name="remarks"></a>Remarks

ファイル名は、 [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 関数の呼び出しで[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)に生成されます。 ファイル拡張子は常に、一時ファイルの "TFR" になります。

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

一時ファイルの領域をロック解除するには、このメソッドを呼び出します。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
ロック解除を開始するファイル内の位置。

*nCount*<br/>
ロックを解除するバイト範囲の長さ。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlFile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)を呼び出します。

##  <a name="write"></a>  CAtlTemporaryFile::Write

ファイルポインターによって示される位置から開始して、一時ファイルにデータを書き込むには、このメソッドを呼び出します。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*pBuffer*<br/>
ファイルに書き込まれるデータを格納しているバッファー。

*nBufSize*<br/>
バッファーから転送されるバイト数。

*pnBytesWritten*<br/>
書き込むバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlFile:: Write](../../atl/reference/catlfile-class.md#write)を呼び出します。

### <a name="example"></a>例

[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)の例を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CAtlFile クラス](../../atl/reference/catlfile-class.md)
