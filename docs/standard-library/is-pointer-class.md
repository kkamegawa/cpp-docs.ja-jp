---
title: is_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pointer
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
ms.openlocfilehash: d8b15f9eb5ef817f5576387b0d8119b86aa86af7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455729"
---
# <a name="ispointer-class"></a>is_pointer クラス

型がポインターであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型の述語のインスタンスは、型*Ty*が**void**へのポインター、オブジェクトへのポインター、関数へのポインター、または`cv-qualified`そのいずれかの形式である場合は true を保持します。それ以外の場合は、false を保持します。 Ty が`is_pointer`メンバーへのポインターまたはメンバー関数へのポインターである場合、は false を保持することに注意してください。

## <a name="example"></a>例

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }
```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_member_pointer クラス](../standard-library/is-member-pointer-class.md)\
[is_reference クラス](../standard-library/is-reference-class.md)
