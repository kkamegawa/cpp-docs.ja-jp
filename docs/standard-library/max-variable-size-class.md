---
title: max_variable_size クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f8b3c61676f784bf9369c22b5db97d7b251f7ac6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447279"
---
# <a name="maxvariablesize-class"></a>max_variable_size クラス

割り当てたメモリ ブロックの数にほぼ比例した最長値までに [freelist](../standard-library/freelist-class.md) オブジェクトを制御する、[最大クラス](../standard-library/allocators-header.md) オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
class max_variable_size
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[max_variable_size](#max_variable_size)|`max_variable_size` 型のオブジェクトを構築します。|

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

## <a name="allocated"></a>  max_variable_size::allocated

割り当てられたメモリ ブロックの数を増やします。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は 、格納されている`_Nallocs`値に Nx を追加します。 このメンバー関数は、operator `cache_freelist::allocate` **new**によるの呼び出しが成功するたびに呼び出されます。 引数 *(_s)* は、 **new**演算子によって割り当てられたチャンク内のメモリブロックの数です。

## <a name="deallocated"></a>  max_variable_size::deallocated

割り当てられたメモリ ブロックの数を減らします。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は 、格納されている`_Nallocs`値から Nx を減算します。 このメンバー関数は、が operator **delete**に`cache_freelist::deallocate`対してを呼び出すたびに呼び出されます。 引数 *(_s)* は、 **delete**演算子によって割り当て解除されたチャンク内のメモリブロックの数です。

## <a name="full"></a>  max_variable_size::full

フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。

```cpp
bool full();
```

### <a name="return-value"></a>戻り値

の場合`_Nallocs / 16 + 16 <= _Nblocks`は true。

### <a name="remarks"></a>Remarks

このメンバー関数は `cache_freelist::deallocate` によって呼び出されます。 呼び出しで**true**が返され`deallocate`た場合、はメモリブロックをフリーリストに格納します。 `deallocate` false が返された場合は、operator **delete**を呼び出してブロックの割り当てを解除します。

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

`max_variable_size` 型のオブジェクトを構築します。

```cpp
max_variable_size();
```

### <a name="remarks"></a>Remarks

このコンストラクターは、格納された値 `_Nblocks` および `_Nallocs` をゼロに初期化します。

## <a name="released"></a>  max_variable_size::released

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void released();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納された値 `_Nblocks` を減らします。 現在の最大クラスの `released` メンバー関数は、`cache_freelist::allocate` によって、フリー リストからメモリ ブロックが削除されるたびに、呼び出されます。

## <a name="saved"></a>  max_variable_size::saved

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void saved();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納された値 `_Nblocks` を増やします。 このメンバー関数は、`cache_freelist::deallocate` によって、フリー リストにメモリ ブロックが置かれるたびに、呼び出されます。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
