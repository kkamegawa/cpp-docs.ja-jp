---
title: CAtlFileMappingBase クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: 12a8159cbf28c64efe36357761f4f404ccff9541
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894017"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase クラス

このクラスは、メモリ マップト ファイルを表します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlFileMappingBase
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|コンストラクターです。|
|[CAtlFileMappingBase::~CAtlFileMappingBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|ファイル マッピング オブジェクトからコピーするには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::GetData](#getdata)|ファイル マッピング オブジェクトからデータを取得するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::GetHandle](#gethandle)|このメソッドを呼び出してファイル ハンドルを返します。|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|ファイル マッピング オブジェクトからマップのサイズを取得するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::MapFile](#mapfile)|ファイル マッピング オブジェクトを作成するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|すべてのプロセスへのフル アクセスを許可するファイル マッピング オブジェクトを作成するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|ファイル マッピング オブジェクトを識別するハンドルを返すには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::Unmap](#unmap)|ファイル マッピング オブジェクトをマップ解除するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|現在のファイル マッピング オブジェクトを別のファイル マッピング オブジェクトに設定します。|

## <a name="remarks"></a>Remarks

ファイルのマッピングは、プロセスの仮想アドレス空間の一部で、ファイルの内容の関連付けです。 このクラスは、簡単にアクセスしてデータを共有するプログラムが使用できるファイル マッピング オブジェクトを作成するためのメソッドを提供します。

詳細については、次を参照してください。[ファイル マッピング](/windows/desktop/Memory/file-mapping)Windows SDK に含まれています。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlfile.h

##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase

コンストラクターです。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>パラメーター

*orig*<br/>
新しいオブジェクトを作成するコピー元のファイル マッピング オブジェクト。

### <a name="remarks"></a>Remarks

必要に応じて、既存のオブジェクトを使用して、新しいファイル マッピング オブジェクトを作成します。 呼び出す必要が[CAtlFileMappingBase::MapFile](#mapfile)を開くか、特定のファイルのファイル マッピング オブジェクトを作成します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase::~CAtlFileMappingBase

デストラクターです。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Remarks

クラスと呼び出しによって割り当てられているリソースを解放、 [CAtlFileMappingBase::Unmap](#unmap)メソッド。

##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom

ファイル マッピング オブジェクトからコピーするには、このメソッドを呼び出します。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>パラメーター

*orig*<br/>
コピーする元のファイル マッピング オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getdata"></a>  CAtlFileMappingBase::GetData

ファイル マッピング オブジェクトからデータを取得するには、このメソッドを呼び出します。

```
void* GetData() const throw();
```

### <a name="return-value"></a>戻り値

データへのポインターを返します。

##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle

ファイル マッピング オブジェクトを識別するハンドルを返すには、このメソッドを呼び出します。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>戻り値

ファイル マッピング オブジェクトを識別するハンドルを返します。

##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize

ファイル マッピング オブジェクトからマップのサイズを取得するには、このメソッドを呼び出します。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>戻り値

マップのサイズを返します。

### <a name="example"></a>例

例をご覧ください[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)します。

##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile

開くか、指定したファイルのファイル マッピング オブジェクトを作成するには、このメソッドを呼び出します。

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>パラメーター

*hFile*<br/>
マッピング オブジェクトを作成するためのファイルへのハンドルします。 *hFile*有効である必要があるあり、INVALID_HANDLE_VALUE に設定することはできません。

*nMappingSize*<br/>
マップのサイズ。 識別されるファイルの現在のサイズにファイル マッピング オブジェクトの最大サイズは 0 の場合、 *hFile します。*

*nOffset*<br/>
ファイル オフセット マッピングの開始位置。 オフセットの値は、システムのメモリ割り当ての粒度の倍数である必要があります。

*dwMappingProtection*<br/>
ファイルがマップされている場合、ファイルのビューに必要な保護。 参照してください*flProtect*で[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK に含まれています。

*dwViewDesiredAccess*<br/>
ファイルのビューと、ファイルによってマップされるページの保護へのアクセスの種類を指定します。 参照してください*dwDesiredAccess*で[mapviewoffileex に](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex)Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

ファイルのサイズが、ファイル マッピング オブジェクトのサイズを超えないファイル マッピング オブジェクトが作成されたら、場合は、すべてのファイルの内容を共有するために使用可能ななります。 詳細については、次を参照してください。 [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)と[mapviewoffileex に](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex)Windows SDK に含まれています。

### <a name="example"></a>例

例をご覧ください[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)します。

##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem

すべてのプロセスへのフル アクセスを許可するファイル マッピング オブジェクトを作成するには、このメソッドを呼び出します。

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>パラメーター

*nMappingSize*<br/>
マップのサイズ。 識別されるファイル マッピング オブジェクトの現在のサイズにファイル マッピング オブジェクトの最大サイズは 0 の場合、 *szName*します。

*szName*<br/>
マッピング オブジェクトの名前。

*pbAlreadyExisted*<br/>
設定されている場合は TRUE、マッピング オブジェクト既に BOOL 値へのポインターが存在します。

*lpsa*<br/>
ポインターを`SECURITY_ATTRIBUTES`を子プロセスが、返されたハンドルを継承できるかどうかを決定する構造体。 参照してください*lpAttributes*で[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK に含まれています。

*dwMappingProtection*<br/>
ファイルがマップされている場合は、ファイルの表示に必要な保護。 参照してください*flProtect*で`CreateFileMapping`Windows SDK に含まれています。

*dwViewDesiredAccess*<br/>
ファイルのビューと、ファイルによってマップされるページの保護へのアクセスの種類を指定します。 参照してください*dwDesiredAccess*で[mapviewoffileex に](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex)Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

`MapShareMem` によって作成された既存のファイル マッピング オブジェクトは、 [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)プロセス間で共有します。

##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping

指定したファイルの名前付きファイル マッピング オブジェクトを開くには、このメソッドを呼び出します。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>パラメーター

*szName*<br/>
マッピング オブジェクトの名前。 この名前のファイル マッピング オブジェクトを開いているハンドルがあるし、マップ オブジェクトのセキュリティ記述子と競合しない場合、 *dwViewDesiredAccess*パラメーター ファイルを開く操作が成功するとします。

*nMappingSize*<br/>
マップのサイズ。 識別されるファイル マッピング オブジェクトの現在のサイズにファイル マッピング オブジェクトの最大サイズは 0 の場合、 *szName*します。

*nOffset*<br/>
ファイル オフセット マッピングの開始位置。 オフセットの値は、システムのメモリ割り当ての粒度の倍数である必要があります。

*dwViewDesiredAccess*<br/>
ファイルのビューと、ファイルによってマップされるページの保護へのアクセスの種類を指定します。 参照してください*dwDesiredAccess*で[mapviewoffileex に](/windows/desktop/api/memoryapi/nf-memoryapi-mapviewoffileex)Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

デバッグ ビルドでは、入力パラメーターが有効でない場合に、アサーション エラーが発生します。

##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =

現在のファイル マッピング オブジェクトを別のファイル マッピング オブジェクトに設定します。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>パラメーター

*orig*<br/>
現在のファイル マッピング オブジェクト。

### <a name="return-value"></a>戻り値

現在のオブジェクトへの参照を返します。

##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap

ファイル マッピング オブジェクトをマップ解除するには、このメソッドを呼び出します。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

参照してください[unmapviewoffile に](/windows/desktop/api/memoryapi/nf-memoryapi-unmapviewoffile)詳細については、Windows SDK に含まれています。

## <a name="see-also"></a>関連項目

[CAtlFileMapping クラス](../../atl/reference/catlfilemapping-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
