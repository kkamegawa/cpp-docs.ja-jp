---
title: max_unbounded クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: cea2f09837e5efc6969e4ab305d106b9c9728412
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447214"
---
# <a name="maxunbounded-class"></a>max_unbounded クラス

[freelist](../standard-library/freelist-class.md) オブジェクトの最長値を制限しない[最大クラス](../standard-library/allocators-header.md) オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
class max_unbounded
```

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[allocated](#allocated)|割り当てられたメモリ ブロックの数を増やします。|
|[deallocated](#deallocated)|割り当てられたメモリ ブロックの数を減らします。|
|[full](#full)|フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。|
|[released](#released)|フリー リスト上のメモリ ブロックの数を減らします。|
|[saved](#saved)|フリー リスト上のメモリ ブロックの数を減らします。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="allocated"></a>  max_unbounded::allocated

割り当てられたメモリ ブロックの数を増やします。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 これは、operator `cache_freelist::allocate` **new**によるの呼び出しが成功するたびに呼び出されます。 引数 *(_s)* は、 **new**演算子によって割り当てられたチャンク内のメモリブロックの数です。

## <a name="deallocated"></a>  max_unbounded::deallocated

割り当てられたメモリ ブロックの数を減らします。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 このメンバー関数は、が operator **delete**に`cache_freelist::deallocate`対してを呼び出すたびに呼び出されます。 引数 *(_s)* は、 **delete**演算子によって割り当て解除されたチャンク内のメモリブロックの数です。

## <a name="full"></a>  max_unbounded::full

フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。

```cpp
bool full();
```

### <a name="return-value"></a>戻り値

このメンバー関数は常に**false**を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は `cache_freelist::deallocate` によって呼び出されます。 呼び出しで**true**が返され`deallocate`た場合、はメモリブロックをフリーリストに格納します。 `deallocate` false が返された場合は、operator **delete**を呼び出してブロックの割り当てを解除します。

## <a name="released"></a>  max_unbounded::released

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void released();
```

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 現在の最大クラスの `released` メンバー関数は、`cache_freelist::allocate` によって、フリー リストからメモリ ブロックが削除されるたびに、呼び出されます。

## <a name="saved"></a>  max_unbounded::saved

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void saved();
```

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 `cache_freelist::deallocate` によって、フリー リストにメモリ ブロックが置かれるたびに、呼び出されます。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
