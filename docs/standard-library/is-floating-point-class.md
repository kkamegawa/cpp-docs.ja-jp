---
title: is_floating_point クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_floating_point
helpviewer_keywords:
- is_floating_point class
- is_floating_point
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
ms.openlocfilehash: c46b74cc9c1d3c6f3a93925d6df46f46d0151e2d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452589"
---
# <a name="isfloatingpoint-class"></a>is_floating_point クラス

型が浮動小数点かどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_floating_point;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型*Ty*が浮動小数点型または`cv-qualified`浮動小数点型の形式である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

浮動小数点型は、 **float**、 **double**、または**long double**のいずれかです。

## <a name="example"></a>例

```cpp
// std__type_traits__is_floating_point.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_floating_point<trivial> == " << std::boolalpha
        << std::is_floating_point<trivial>::value << std::endl;
    std::cout << "is_floating_point<int> == " << std::boolalpha
        << std::is_floating_point<int>::value << std::endl;
    std::cout << "is_floating_point<float> == " << std::boolalpha
        << std::is_floating_point<float>::value << std::endl;

    return (0);
    }
```

```Output
is_floating_point<trivial> == false
is_floating_point<int> == false
is_floating_point<float> == true
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_integral クラス](../standard-library/is-integral-class.md)
