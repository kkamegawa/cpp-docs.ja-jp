---
title: CCRTAllocator クラス
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: c08d594e1c0f4d532f46961e266bf6ced98c51b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259080"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator クラス

このクラスは、CRT メモリ ルーチンを使用してメモリを管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class ATL::CCRTAllocator
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|(静的)メモリを割り当てるには、このメソッドを呼び出します。|
|[CCRTAllocator::Free](#free)|(静的)メモリを解放するには、このメソッドを呼び出します。|
|[CCRTAllocator::Reallocate](#reallocate)|(静的)メモリを再割り当てするには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

このクラスによって使用されます[CHeapPtr](../../atl/reference/cheapptr-class.md) CRT メモリ割り当てルーチンを提供します。 対応するクラス、 [CComAllocator](../../atl/reference/ccomallocator-class.md)COM のルーチンを使用する同じメソッドを提供します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="allocate"></a>  CCRTAllocator::Allocate

メモリを割り当てる場合は、この静的関数を呼び出します。

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
割り当てるバイト数。

### <a name="return-value"></a>戻り値

メモリが不足している場合、割り当てられた領域に void ポインターを返すか、NULL を返します。

### <a name="remarks"></a>Remarks

メモリを割り当てます。 参照してください[malloc](../../c-runtime-library/reference/malloc.md)の詳細。

##  <a name="free"></a>  CCRTAllocator::Free

メモリを解放する、この静的関数を呼び出します。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

### <a name="remarks"></a>Remarks

割り当てられたメモリを解放します。 参照してください[無料](../../c-runtime-library/reference/free.md)の詳細。

##  <a name="reallocate"></a>  CCRTAllocator::Reallocate

メモリを再割り当てする場合は、この静的関数を呼び出します。

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
割り当てられたメモリへのポインター。

*nBytes*<br/>
再割り当てするバイト数。

### <a name="return-value"></a>戻り値

メモリが不足している場合、割り当てられた領域に void ポインターを返すか、NULL を返します。

### <a name="remarks"></a>Remarks

割り当てられたメモリの量を変更します。 参照してください[realloc](../../c-runtime-library/reference/realloc.md)の詳細。

## <a name="see-also"></a>関連項目

[CHeapPtr クラス](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator クラス](../../atl/reference/ccomallocator-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
