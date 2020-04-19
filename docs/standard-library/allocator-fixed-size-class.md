---
title: allocator_fixed_size クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: 5ee506838ea723b82f04bba301c19c0149d986bf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451009"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size クラス

[Max_fixed_size](../standard-library/max-fixed-size-class.md)によって管理される長さを持つ[cache_freelist](../standard-library/cache-freelist-class.md)型のキャッシュ*を使用し*て、型型のオブジェクトのストレージ割り当てと解放を管理するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Type*|アロケーターによって割り当てられた要素の型。|

## <a name="remarks"></a>Remarks

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)マクロは、このクラスを次のステートメントの*name*パラメーターとして渡します。`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>必要条件

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
