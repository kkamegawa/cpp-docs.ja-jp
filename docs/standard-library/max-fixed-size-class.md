---
title: max_fixed_size クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: bbc39a169f9a4bbac3e78b208b3a1a31e4e30ff2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456374"
---
# <a name="maxfixedsize-class"></a>max_fixed_size クラス

[freelist](../standard-library/freelist-class.md) オブジェクトを固定の最長値までに制限する[最大クラス](../standard-library/allocators-header.md) オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Max*|`freelist` に格納する要素の最大数を決定する、最大クラス。|

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[max_fixed_size](#max_fixed_size)|`max_fixed_size` 型のオブジェクトを構築します。|

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

## <a name="allocated"></a>  max_fixed_size::allocated

割り当てられたメモリ ブロックの数を増やします。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 このメンバー関数は、operator `cache_freelist::allocate` **new**によるの呼び出しが成功するたびに呼び出されます。 引数 *(_s)* は、 **new**演算子によって割り当てられたチャンク内のメモリブロックの数です。

## <a name="deallocated"></a>  max_fixed_size::deallocated

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

## <a name="full"></a>  max_fixed_size::full

フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。

```cpp
bool full();
```

### <a name="return-value"></a>戻り値

の場合`Max <= _Nblocks`は true、それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

このメンバー関数は `cache_freelist::deallocate` によって呼び出されます。 呼び出しで**true**が返され`deallocate`た場合、はメモリブロックをフリーリストに格納します。 `deallocate` false が返された場合は、operator **delete**を呼び出してブロックの割り当てを解除します。

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

`max_fixed_size` 型のオブジェクトを構築します。

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Remarks

このコンストラクターは、格納された値 `_Nblocks` をゼロに初期化します。

## <a name="released"></a>  max_fixed_size::released

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void released();
```

### <a name="remarks"></a>Remarks

格納された `_Nblocks`を減らします。 現在の[最大クラス](../standard-library/allocators-header.md)の`released` メンバー関数は、`cache_freelist::allocate` によって、フリー リストからメモリ ブロックが削除されるたびに、呼び出されます。

## <a name="saved"></a>  max_fixed_size::saved

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void saved();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納された値 `_Nblocks` を増やします。 このメンバー関数は、`cache_freelist::deallocate` によって、フリー リストにメモリ ブロックが置かれるたびに、呼び出されます。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
