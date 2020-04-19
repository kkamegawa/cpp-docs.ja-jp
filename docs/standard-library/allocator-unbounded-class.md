---
title: allocator_unbounded クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 38ecec3848808585ac0ed7cb1b076480a79f6d41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448297"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded クラス

[Max_unbounded](../standard-library/max-unbounded-class.md)によって管理される長さを持つ[cache_freelist](../standard-library/cache-freelist-class.md)型のキャッシュ*を使用し*て、型型のオブジェクトのストレージ割り当てと解放を管理するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Type*|アロケーターによって割り当てられた要素の型。|

## <a name="remarks"></a>Remarks

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)マクロは、このクラスを次のステートメントの*name*パラメーターとして渡します。`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>必要条件

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
