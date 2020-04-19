---
title: max_none クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: b296c641be68efac7410328a448a4ad2bd0fa88e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626823"
---
# <a name="max_none-class"></a>max_none クラス

[freelist](../standard-library/freelist-class.md) オブジェクトを最長値ゼロまでに制限する[最大クラス](../standard-library/allocators-header.md) オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Max*|`freelist` に格納する要素の最大数を決定する、最大クラス。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[allocated](#allocated)|割り当てられたメモリ ブロックの数を増やします。|
|[deallocated](#deallocated)|割り当てられたメモリ ブロックの数を減らします。|
|[full](#full)|フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。|
|[released](#released)|フリー リスト上のメモリ ブロックの数を減らします。|
|[saved](#saved)|フリー リスト上のメモリ ブロックの数を減らします。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="allocated"></a>  max_none::allocated

割り当てられたメモリ ブロックの数を増やします。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 これは、operator **new**に `cache_freelist::allocate` ことによって、呼び出しが成功するたびに呼び出されます。 引数 *(_s)* は、 **new**演算子によって割り当てられたチャンク内のメモリブロックの数です。

## <a name="deallocated"></a>  max_none::deallocated

割り当てられたメモリ ブロックの数を減らします。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|増分値。|

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 このメンバー関数は、演算子**delete**に `cache_freelist::deallocate` によって呼び出されるたびに呼び出されます。 引数 *(_s)* は、 **delete**演算子によって割り当て解除されたチャンク内のメモリブロックの数です。

## <a name="full"></a>  max_none::full

フリー リストにメモリ ブロックを追加する必要があるかどうかを示す値を返します。

```cpp
bool full();
```

### <a name="return-value"></a>戻り値

このメンバー関数は常に**true**を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は `cache_freelist::deallocate` によって呼び出されます。 呼び出しによって**true**が返された場合、`deallocate` はメモリブロックをフリーリストに格納します。**false**が返された場合、`deallocate` は operator **delete**を呼び出して、ブロックの割り当てを解除します。

## <a name="released"></a>  max_none::released

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void released();
```

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 現在の最大クラスの `released` メンバー関数は、`cache_freelist::allocate` によって、フリー リストからメモリ ブロックが削除されるたびに、呼び出されます。

## <a name="saved"></a>  max_none::saved

フリー リスト上のメモリ ブロックの数を減らします。

```cpp
void saved();
```

### <a name="remarks"></a>Remarks

このメンバー関数は何も処理を行いません。 `cache_freelist::deallocate` によって、フリー リストにメモリ ブロックが置かれるたびに、呼び出されます。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
