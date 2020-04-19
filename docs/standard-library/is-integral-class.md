---
title: is_integral クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456239"
---
# <a name="isintegral-class"></a>is_integral クラス

型が整数かどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型*Ty*が整数型の1つ、または`cv-qualified`整数型の1つの形式である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

整数型は、 **bool**、 **char**、 **unsigned char**、 **signed char**、 **wchar_t**、 **short**、 **unsigned short**、 **int**、 **unsigned int**、 **long**、 **unsigned long**のいずれかです。 また、これらを提供するコンパイラでは、整数型は long 長、 **unsigned long long**、 **__int64**、 **unsigned __int64** **のいずれ**かになります。

## <a name="example"></a>例

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_enum クラス](../standard-library/is-enum-class.md)\
[is_floating_point クラス](../standard-library/is-floating-point-class.md)
