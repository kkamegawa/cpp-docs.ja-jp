---
title: rts_alloc クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: b0ec7d4d3dbe5ef1334bf3c394819a4f5235c28c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688983"
---
# <a name="rts_alloc-class"></a>rts_alloc クラス

Rts_alloc クラステンプレートは、キャッシュインスタンスの配列を保持し、コンパイル時ではなく実行時に割り当てと割り当て解除に使用するインスタンスを決定する[フィルター](../standard-library/allocators-header.md)を記述します。

## <a name="syntax"></a>構文

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*キャッシュ*|配列に含まれているキャッシュ インスタンスの型。 これは、[cache_chunklist クラス](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md)、[cache_suballoc](../standard-library/cache-suballoc-class.md) のいずれかです。|

## <a name="remarks"></a>Remarks

このクラステンプレートは、複数のブロックアロケーターインスタンスを保持し、コンパイル時ではなく、実行時に割り当てまたは割り当て解除に使用するインスタンスを決定します。 再バインドをコンパイルできないコンパイラと一緒に使用します。

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[allocate](#allocate)|メモリのブロックを割り当てます。|
|[deallocate](#deallocate)|指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。|
|[equals](#equals)|2 つのキャッシュが等しいかどうかを比較します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="allocate"></a>  rts_alloc::allocate

メモリのブロックを割り当てます。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*count*|割り当てられる配列内の要素の数。|

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は `caches[_IDX].allocate(count)` を返します。インデックス `_IDX` は、要求されたブロックサイズの*カウント*によって決定されます。*カウント*が大きすぎる場合は、`operator new(count)` が返されます。 キャッシュ オブジェクトを表す `cache`。

## <a name="deallocate"></a>  rts_alloc::deallocate

指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|記憶域から割り当てを解除される最初のオブジェクトへのポインター。|
|*count*|記憶域から割り当てを解除されるオブジェクトの数。|

### <a name="remarks"></a>Remarks

このメンバー関数は `caches[_IDX].deallocate(ptr, count)` を呼び出します。インデックス `_IDX` は、要求されたブロックサイズの*カウント*によって決定されます。*カウント*が大きすぎる場合は、`operator delete(ptr)` が返されます。

## <a name="equals"></a>  rts_alloc::equals

2 つのキャッシュが等しいかどうかを比較します。

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*キャッシュ (_l)*|フィルターに関連付けられているキャッシュ オブジェクト。|
|*その他 (_d)*|等しいかどうかを比較するキャッシュ オブジェクト。|

### <a name="remarks"></a>Remarks

`caches[0].equals(other.caches[0])` の結果の場合は**true** 。それ以外の場合は**false**。 `caches` はキャッシュ オブジェクトの配列を表します。

## <a name="see-also"></a>関連項目

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
