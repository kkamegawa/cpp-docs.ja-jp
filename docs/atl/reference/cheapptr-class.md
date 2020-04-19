---
title: CHeapPtr クラス
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: 8cb35139e707d81a53edb762a2b7fc2ab41ff247
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258677"
---
# <a name="cheapptr-class"></a>CHeapPtr クラス

ヒープのポインターを管理するためのスマート ポインター クラス。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ヒープに格納されるオブジェクトの種類。

*アロケーター*<br/>
メモリの割り当ては、使用するクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|オブジェクトを格納するヒープにメモリを割り当てるには、このメソッドを呼び出します。|
|[CHeapPtr::Reallocate](#reallocate)|ヒープにメモリを再割り当てするには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|代入演算子です。|

## <a name="remarks"></a>Remarks

`CHeapPtr` 派生[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) 、既定では、CRT ルーチン (で[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) を割り当てたり、メモリを解放します。 クラスは、 [CHeapPtrList](../../atl/reference/cheapptrlist-class.md)にヒープのポインターのリストを構築することができます。 参照してください[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)、COM メモリ割り当てルーチンが使用されます。

## <a name="inheritance-hierarchy"></a>継承階層

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

オブジェクトを格納するヒープにメモリを割り当てるには、このメソッドを呼び出します。

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>パラメーター

*nElements*<br/>
割り当てるメモリの量を計算するために使用する要素の数。 既定値は 1 です。

### <a name="return-value"></a>戻り値

失敗した場合に、メモリが正常である場合は true を返しますが割り当てられます。

### <a name="remarks"></a>Remarks

アロケーターのルーチンは、ヒープを格納するための十分なメモリを予約するために使用*nElement*コンス トラクターで定義された型のオブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

コンストラクターです。

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
既存のヒープ ポインターまたは`CHeapPtr`します。

### <a name="remarks"></a>Remarks

既存のポインターを使用して、ヒープのポインターを作成することができます必要に応じて、`CHeapPtr`オブジェクト。 そうである場合、新しい`CHeapPtr`オブジェクトを新しいポインターとリソースを管理する責任を前提としています。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

代入演算子。

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
既存の `CHeapPtr` オブジェクト。

### <a name="return-value"></a>戻り値

更新されたへの参照を返します`CHeapPtr`します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

ヒープにメモリを再割り当てするには、このメソッドを呼び出します。

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>パラメーター

*nElements*<br/>
新しいに割り当てるメモリの量を計算するための要素数。

### <a name="return-value"></a>戻り値

失敗した場合に、メモリが正常である場合は true を返しますが割り当てられます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>関連項目

[CHeapPtrBase クラス](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator クラス](../../atl/reference/ccrtallocator-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
