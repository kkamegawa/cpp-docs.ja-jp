---
title: CComAllocator クラス
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: de302c7a58bf1b15e63e7cd391621ed9558e5a70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497597"
---
# <a name="ccomallocator-class"></a>CComAllocator クラス

このクラスには、COM メモリルーチンを使用してメモリを管理するためのメソッドが用意されています。

## <a name="syntax"></a>構文

```
class CComAllocator
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComAllocator:: Allocate](#allocate)|この静的メソッドを呼び出してメモリを割り当てます。|
|[CComAllocator:: Free](#free)|割り当てられたメモリを解放するには、この静的メソッドを呼び出します。|
|[CComAllocator:: 再割り当て](#reallocate)|この静的メソッドを呼び出してメモリを再割り当てします。|

## <a name="remarks"></a>Remarks

このクラスは、COM メモリ割り当てルーチンを提供するために[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)によって使用されます。 対応するクラス[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)は、CRT ルーチンを使用して同じメソッドを提供します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="allocate"></a>  CComAllocator::Allocate

メモリを割り当てる場合は、この静的関数を呼び出します。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
割り当てるバイト数。

### <a name="return-value"></a>戻り値

メモリが不足している場合、割り当てられた領域に void ポインターを返すか、NULL を返します。

### <a name="remarks"></a>Remarks

メモリを割り当てます。 詳細については、「 [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) 」を参照してください。

##  <a name="free"></a>CComAllocator:: Free

割り当てられたメモリを解放するには、この静的関数を呼び出します。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

### <a name="remarks"></a>Remarks

割り当てられたメモリを解放します。 詳細については、「 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) 」を参照してください。

##  <a name="reallocate"></a>  CComAllocator::Reallocate

メモリを再割り当てする場合は、この静的関数を呼び出します。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

*nBytes*<br/>
再割り当てするバイト数。

### <a name="return-value"></a>戻り値

割り当てられた領域への void ポインターを返すか、メモリが不足している場合は NULL を返します。

### <a name="remarks"></a>Remarks

割り当てられたメモリの量を変更します。 詳細については、「 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) 」を参照してください。

## <a name="see-also"></a>関連項目

[CComHeapPtr クラス](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator クラス](../../atl/reference/ccrtallocator-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
