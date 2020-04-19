---
title: CComHeap クラス
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497345"
---
# <a name="ccomheap-class"></a>CComHeap クラス

このクラスは、COM メモリ割り当て関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComHeap:: Allocate](#allocate)|メモリ ブロックを割り当てるには、このメソッドを呼び出します。|
|[CComHeap:: Free](#free)|このメモリマネージャーによって割り当てられたメモリブロックを解放するには、このメソッドを呼び出します。|
|[CComHeap:: GetSize](#getsize)|このメモリマネージャーによって割り当てられたメモリブロックの割り当てサイズを取得するには、このメソッドを呼び出します。|
|[CComHeap:: 再割り当て](#reallocate)|このメソッドを呼び出し、このメモリ マネージャーによって割り当てられたメモリの再割り当てを行います。|

## <a name="remarks"></a>Remarks

`CComHeap`は、 [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)、 [Imalloc:: GETSIZE](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)、 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)などの COM 割り当て関数を使用して、メモリ割り当て関数を実装します。 割り当てることができるメモリの最大量は、INT_MAX (2147483647) バイトと同じです。

## <a name="example"></a>例

[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)の例を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>必要条件

**ヘッダー:** ATLComMem.h

##  <a name="allocate"></a>  CComHeap::Allocate

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

[CComHeap:: Free](#free)または[CComHeap::](#reallocate)の再割り当てを呼び出して、このメソッドによって割り当てられたメモリを解放します。

[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)を使用して実装されます。

##  <a name="free"></a>CComHeap:: Free

このメモリマネージャーによって割り当てられたメモリブロックを解放するには、このメソッドを呼び出します。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。 NULL は有効な値であり、何も行いません。

### <a name="remarks"></a>Remarks

[CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)を使用して実装されます。

##  <a name="getsize"></a>CComHeap:: GetSize

このメモリマネージャーによって割り当てられたメモリブロックの割り当てサイズを取得するには、このメソッドを呼び出します。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。

### <a name="return-value"></a>戻り値

割り当てられたメモリブロックのサイズをバイト数で返します。

### <a name="remarks"></a>Remarks

[Imalloc:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)を使用して実装されます。

##  <a name="reallocate"></a>  CComHeap::Reallocate

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

[CComHeap:: free](#free)を呼び出して、このメソッドによって割り当てられたメモリを解放します。

[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)を使用して実装されます。

## <a name="see-also"></a>関連項目

[DynamicConsumer サンプル](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CWin32Heap クラス](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap クラス](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap クラス](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap クラス](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr クラス](../../atl/reference/iatlmemmgr-class.md)
