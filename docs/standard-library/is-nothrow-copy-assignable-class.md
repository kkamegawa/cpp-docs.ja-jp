---
title: is_nothrow_copy_assignable クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 330c97cd945e161d2bf47deb377dd732bf53b3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455985"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable クラス

スローしないことがコンパイラに判明しているコピー代入演算子が型にあるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型述語のインスタンスは、が true を`is_nothrow_assignable<T&, const T&>`保持する参照可能 type *T*に対して true を保持します。それ以外の場合は、false を保持します。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_nothrow_assignable クラス](../standard-library/is-nothrow-assignable-class.md)
