---
title: remove_all_extents クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_all_extents
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
ms.openlocfilehash: 0909da3f08cec62bcb915a65c353abdd33c96c9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451402"
---
# <a name="removeallextents-class"></a>remove_all_extents クラス

配列型から非配列型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct remove_all_extents;

template <class T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

の`remove_all_extents<T>`インスタンスは、すべての配列次元が削除された配列型*T*の要素型である修飾型を保持します。 *t*が配列型でない場合は*t*を保持します。

## <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_all_extents<int> == "
        << typeid(std::remove_all_extents_t<int>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5]> == "
        << typeid(std::remove_all_extents_t<int[5]>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5][10]> == "
        << typeid(std::remove_all_extents_t<int[5][10]>).name()
        << std::endl;

    return (0);
    }
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_extent クラス](../standard-library/remove-extent-class.md)
