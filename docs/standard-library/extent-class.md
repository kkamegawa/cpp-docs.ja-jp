---
title: extent クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 0cd53ba8537e706a68ffdcf08df998108266ad20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457786"
---
# <a name="extent-class"></a>extent クラス

配列の次元を取得します。

## <a name="syntax"></a>構文

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

*私*\
照会する配列の範囲。

## <a name="remarks"></a>Remarks

*Ty*が*i*次元以上の配列型である場合、型クエリは*i*で指定された次元の要素数を保持します。*Ty*が配列型ではない場合、またはランクが*I*より小さい場合、または*i*が0で*ty*が "不明`U`な範囲の配列" である場合、型クエリは値0を保持します。

## <a name="example"></a>例

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_all_extents クラス](../standard-library/remove-all-extents-class.md)\
[remove_extent クラス](../standard-library/remove-extent-class.md)
