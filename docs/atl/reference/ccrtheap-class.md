---
title: CCRTHeap クラス
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: 3c5030b9cfbfd636a783d27bcc8f9469f8348acb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246063"
---
# <a name="ccrtheap-class"></a>CCRTHeap クラス

このクラスは実装[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) CRT ヒープ関数を使用します。

## <a name="syntax"></a>構文

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCRTHeap::Allocate](#allocate)|メモリ ブロックを割り当てるには、このメソッドを呼び出します。|
|[Ccrtheap::free](#free)|このメモリ マネージャーによって割り当てられたメモリ ブロックを解放するには、このメソッドを呼び出します。|
|[CCRTHeap::GetSize](#getsize)|このメモリ マネージャーによって割り当てられたメモリ ブロックの割り当てサイズを取得するには、このメソッドを呼び出します。|
|[CCRTHeap::Reallocate](#reallocate)|このメソッドを呼び出し、このメモリ マネージャーによって割り当てられたメモリの再割り当てを行います。|

## <a name="remarks"></a>Remarks

`CCRTHeap` メモリ割り当て関数が CRT を使用するヒープなど、機能を実装する[malloc](../../c-runtime-library/reference/malloc.md)、[無料](../../c-runtime-library/reference/free.md)、 [realloc](../../c-runtime-library/reference/realloc.md)、および[_msize](../../c-runtime-library/reference/msize.md)します。

## <a name="example"></a>例

例をご覧ください[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlmem.h

##  <a name="allocate"></a>  CCRTHeap::Allocate

メモリ ブロックを割り当てるには、このメソッドを呼び出します。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
新しいメモリ ブロック内の要求されたバイト数。

### <a name="return-value"></a>戻り値

新しく割り当てられたメモリ ブロックの先頭へのポインターを返します。

### <a name="remarks"></a>Remarks

呼び出す[ccrtheap::free](#free)または[ccrtheap::reallocate](#reallocate)このメソッドによって割り当てられたメモリを解放します。

使用して実装[malloc](../../c-runtime-library/reference/malloc.md)します。

##  <a name="free"></a>  CCRTHeap::Free

このメモリ マネージャーによって割り当てられたメモリ ブロックを解放するには、このメソッドを呼び出します。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。 NULL は有効な値を何も行われません。

### <a name="remarks"></a>Remarks

使用して実装[無料](../../c-runtime-library/reference/free.md)します。

##  <a name="getsize"></a>  CCRTHeap::GetSize

このメモリ マネージャーによって割り当てられたメモリ ブロックの割り当てサイズを取得するには、このメソッドを呼び出します。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。

### <a name="return-value"></a>戻り値

割り当てられたメモリ ブロックのサイズをバイト単位で返します。

### <a name="remarks"></a>Remarks

使用して実装[_msize](../../c-runtime-library/reference/msize.md)します。

##  <a name="reallocate"></a>  CCRTHeap::Reallocate

このメソッドを呼び出し、このメモリ マネージャーによって割り当てられたメモリの再割り当てを行います。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。

*nBytes*<br/>
新しいメモリ ブロック内の要求されたバイト数。

### <a name="return-value"></a>戻り値

新しく割り当てられたメモリ ブロックの先頭へのポインターを返します。

### <a name="remarks"></a>Remarks

呼び出す[ccrtheap::free](#free)このメソッドによって割り当てられたメモリを解放します。 使用して実装[realloc](../../c-runtime-library/reference/realloc.md)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComHeap クラス](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap クラス](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap クラス](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap クラス](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr クラス](../../atl/reference/iatlmemmgr-class.md)
