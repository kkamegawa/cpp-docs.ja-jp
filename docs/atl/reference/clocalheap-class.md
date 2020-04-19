---
title: CLocalHeap クラス
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496748"
---
# <a name="clocalheap-class"></a>CLocalHeap クラス

このクラスは、Win32 ローカルヒープ関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CLocalHeap:: Allocate](#allocate)|メモリ ブロックを割り当てるには、このメソッドを呼び出します。|
|[CLocalHeap:: Free](#free)|このメモリマネージャーによって割り当てられたメモリブロックを解放するには、このメソッドを呼び出します。|
|[CLocalHeap:: GetSize](#getsize)|このメモリマネージャーによって割り当てられたメモリブロックの割り当てサイズを取得するには、このメソッドを呼び出します。|
|[CLocalHeap::Reallocate](#reallocate)|このメソッドを呼び出し、このメモリ マネージャーによって割り当てられたメモリの再割り当てを行います。|

## <a name="remarks"></a>Remarks

`CLocalHeap`Win32 ローカルヒープ関数を使用して、メモリ割り当て関数を実装します。

> [!NOTE]
>  ローカルヒープ関数は、他のメモリ管理関数よりも低速であり、多くの機能を提供するわけではありません。 そのため、新しいアプリケーションでは、[ヒープ関数](/windows/win32/Memory/heap-functions)を使用する必要があります。 これらは、 [CWin32Heap](../../atl/reference/cwin32heap-class.md)クラスで使用できます。

## <a name="example"></a>例

[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)の例を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlmem. h

##  <a name="allocate"></a>  CLocalHeap::Allocate

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

[Clocalheap:: Free](#free)または[clocalheap::](#reallocate)の再割り当てを呼び出して、このメソッドによって割り当てられたメモリを解放します。

LMEM_FIXED のフラグパラメーターと共に[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)を使用して実装されます。

##  <a name="free"></a>  CLocalHeap::Free

このメモリマネージャーによって割り当てられたメモリブロックを解放するには、このメソッドを呼び出します。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
このメモリ マネージャーによって以前に割り当てられたメモリへのポインター。 NULL は有効な値であり、何も行いません。

### <a name="remarks"></a>Remarks

[LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)を使用して実装されます。

##  <a name="getsize"></a>  CLocalHeap::GetSize

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

[Localsize](/windows/win32/api/winbase/nf-winbase-localsize)を使用して実装されます。

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

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

[Clocalheap:: free](#free)を呼び出して、このメソッドによって割り当てられたメモリを解放します。

[Localrealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)を使用して実装されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComHeap クラス](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap クラス](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap クラス](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap クラス](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr クラス](../../atl/reference/iatlmemmgr-class.md)
