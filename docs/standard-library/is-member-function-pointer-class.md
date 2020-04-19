---
title: is_member_function_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_function_pointer
helpviewer_keywords:
- is_member_function_pointer class
- is_member_function_pointer
ms.assetid: 02e372c4-2714-40f2-b376-2e10ca91c8ed
ms.openlocfilehash: 1f51c389e86f2d0550a6418d04080f40f4bf4204
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456178"
---
# <a name="ismemberfunctionpointer-class"></a>is_member_function_pointer クラス

型がメンバー関数へのポインターであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_member_function_pointer;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型*Ty*がメンバー関数へのポインターまたは`cv-qualified`メンバー関数へのポインターである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

## <a name="example"></a>例

```cpp
// std__type_traits__is_member_function_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_function_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_function_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_function_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_function_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_function_pointer<trivial *> == false
is_member_function_pointer<int trivial::*> == false
is_member_function_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_member_pointer クラス](../standard-library/is-member-pointer-class.md)
