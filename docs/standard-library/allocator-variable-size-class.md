---
title: allocator_variable_size クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: bf243089ee8f4e26930e183b007a108e38f444e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458152"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size クラス

[Max_variable_size](../standard-library/max-variable-size-class.md)によって管理される長さを持つ[cache_freelist](../standard-library/cache-freelist-class.md)型のキャッシュ*を使用し*て、型型のオブジェクトのストレージ割り当てと解放を管理するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Type*|アロケーターによって割り当てられた要素の型。|

## <a name="remarks"></a>Remarks

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)マクロは、このクラスを次のステートメントの*name*パラメーターとして渡します。`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>必要条件

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
