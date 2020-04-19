---
title: is_copy_assignable クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: 5fedd32f026828e49ea29cb2975a2529ca28c862
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452833"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable クラス

割り当て時に型をコピーできるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型*Ty*がコピー代入演算子を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 is_assignable\<Ty&, const Ty&> に相当します。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
