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
ms.openlocfilehash: a20a8f6c00f9404aa819b87a6a69ad2c08fb4561
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739546"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase クラス

このクラスは、メモリマップトファイルを表します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlFileMappingBase
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|コンストラクターです。|
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|ファイルマッピングオブジェクトからコピーするには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::GetData](#getdata)|ファイルマッピングオブジェクトからデータを取得するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase:: GetHandle](#gethandle)|ファイルハンドルを返すには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|ファイルマッピングオブジェクトからマッピングサイズを取得するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::MapFile](#mapfile)|ファイルマッピングオブジェクトを作成するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|すべてのプロセスへのフルアクセスを許可するファイルマッピングオブジェクトを作成するには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|ファイルマッピングオブジェクトへのハンドルを返すには、このメソッドを呼び出します。|
|[CAtlFileMappingBase::Unmap](#unmap)|ファイルマッピングオブジェクトをマップ解除するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAtlFileMappingBase::operator =](#operator_eq)|現在のファイルマッピングオブジェクトを別のファイルマッピングオブジェクトに設定します。|

## <a name="remarks"></a>Remarks

ファイルマッピングとは、プロセスの仮想アドレス空間の一部にファイルの内容を関連付けることです。 このクラスには、プログラムがデータに簡単にアクセスして共有できるファイルマッピングオブジェクトを作成するためのメソッドが用意されています。

詳細については、「Windows SDK での[ファイルマッピング](/windows/win32/Memory/file-mapping)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlfile .h

##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase

コンストラクターです。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>パラメーター

*著*<br/>
新しいオブジェクトを作成するためにコピーする元のファイルマッピングオブジェクト。

### <a name="remarks"></a>Remarks

新しいファイルマッピングオブジェクトを作成します。必要に応じて、既存のオブジェクトを使用します。 また、 [CAtlFileMappingBase:: MapFile](#mapfile)を呼び出して、特定のファイルのファイルマッピングオブジェクトを開いたり作成したりすることも必要です。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase::~CAtlFileMappingBase

デストラクターです。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Remarks

クラスによって割り当てられたすべてのリソースを解放し、 [CAtlFileMappingBase:: マップ](#unmap)解除メソッドを呼び出します。

##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom

ファイルマッピングオブジェクトからコピーするには、このメソッドを呼び出します。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>パラメーター

*著*<br/>
コピー元のファイルマッピングオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="getdata"></a>  CAtlFileMappingBase::GetData

ファイルマッピングオブジェクトからデータを取得するには、このメソッドを呼び出します。

```
void* GetData() const throw();
```

### <a name="return-value"></a>戻り値

データへのポインターを返します。

##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle

ファイルマッピングオブジェクトへのハンドルを返すには、このメソッドを呼び出します。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>戻り値

ファイルマッピングオブジェクトへのハンドルを返します。

##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize

ファイルマッピングオブジェクトからマッピングサイズを取得するには、このメソッドを呼び出します。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>戻り値

マッピングサイズを返します。

### <a name="example"></a>例

[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)の例を参照してください。

##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile

このメソッドを呼び出して、指定したファイルのファイルマッピングオブジェクトを開くか、作成します。

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
マッピングオブジェクトの作成元のファイルを処理します。 *hFile*は有効である必要があり、INVALID_HANDLE_VALUE に設定することはできません。

*nMappingSize*<br/>
マッピングサイズ。 0の場合、ファイルマッピングオブジェクトの最大サイズは、HFile によって識別されるファイルの現在のサイズと同じに*なります。*

*nOffset*<br/>
マッピングを開始するファイルオフセット。 オフセット値は、システムのメモリ割り当ての粒度の倍数である必要があります。

*dwMappingProtection*<br/>
ファイルがマップされるときにファイルビューに必要な保護。 Windows SDK の「 *Flprotect* in [createfilemapping に](/windows/win32/api/winbase/nf-winbase-createfilemappinga)」を参照してください。

*dwViewDesiredAccess*<br/>
ファイルビューへのアクセスの種類を指定します。したがって、ファイルによってマップされたページの保護が使用されます。 Windows SDK の[mapviewoffileex に](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)の*dwDesiredAccess*を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

ファイルマッピングオブジェクトが作成された後、ファイルのサイズがファイルマッピングオブジェクトのサイズを超えることはできません。その場合、すべてのファイルの内容を共有できるわけではありません。 詳細については、Windows SDK の「 [createfilemapping に](/windows/win32/api/winbase/nf-winbase-createfilemappinga)and [mapviewoffileex に](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)」を参照してください。

### <a name="example"></a>例

[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)の例を参照してください。

##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem

すべてのプロセスへのフルアクセスを許可するファイルマッピングオブジェクトを作成するには、このメソッドを呼び出します。

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
マッピングサイズ。 0の場合、ファイルマッピングオブジェクトの最大サイズは、 *szName*によって識別されるファイルマッピングオブジェクトの現在のサイズと同じになります。

*szName*<br/>
マッピングオブジェクトの名前。

*pbAlreadyExisted*<br/>
マッピングオブジェクトが既に存在する場合は、TRUE に設定されているブール値を指します。

*lpsa*<br/>
返されたハンドル`SECURITY_ATTRIBUTES`を子プロセスが継承できるかどうかを決定する構造体へのポインター。 Windows SDK の「 [createfilemapping に](/windows/win32/api/winbase/nf-winbase-createfilemappinga)の*lpattributes* 」を参照してください。

*dwMappingProtection*<br/>
ファイルがマップされるときに、ファイルビューに必要な保護。 Windows SDK の「 *flprotect* `CreateFileMapping` 」を参照してください。

*dwViewDesiredAccess*<br/>
ファイルビューへのアクセスの種類を指定します。したがって、ファイルによってマップされたページの保護が使用されます。 Windows SDK の[mapviewoffileex に](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)の*dwDesiredAccess*を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

`MapShareMem`[createfilemapping に](/windows/win32/api/winbase/nf-winbase-createfilemappinga)によって作成された既存のファイルマッピングオブジェクトをプロセス間で共有できるようにします。

##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping

指定したファイルの名前付きファイルマッピングオブジェクトを開くには、このメソッドを呼び出します。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>パラメーター

*szName*<br/>
マッピングオブジェクトの名前。 この名前によってファイルマッピングオブジェクトを開くハンドルが存在し、マッピングオブジェクトのセキュリティ記述子が*dwViewDesiredAccess*パラメーターと競合しない場合、オープン操作は成功します。

*nMappingSize*<br/>
マッピングサイズ。 0の場合、ファイルマッピングオブジェクトの最大サイズは、 *szName*によって識別されるファイルマッピングオブジェクトの現在のサイズと同じになります。

*nOffset*<br/>
マッピングを開始するファイルオフセット。 オフセット値は、システムのメモリ割り当ての粒度の倍数である必要があります。

*dwViewDesiredAccess*<br/>
ファイルビューへのアクセスの種類を指定します。したがって、ファイルによってマップされたページの保護が使用されます。 Windows SDK の[mapviewoffileex に](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)の*dwDesiredAccess*を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

デバッグビルドでは、入力パラメーターが無効な場合にアサーションエラーが発生します。

##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =

現在のファイルマッピングオブジェクトを別のファイルマッピングオブジェクトに設定します。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>パラメーター

*著*<br/>
現在のファイルマッピングオブジェクト。

### <a name="return-value"></a>戻り値

現在のオブジェクトへの参照を返します。

##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap

ファイルマッピングオブジェクトをマップ解除するには、このメソッドを呼び出します。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [unmapviewoffile に](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile)」を参照してください。

## <a name="see-also"></a>関連項目

[CAtlFileMapping クラス](../../atl/reference/catlfilemapping-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
