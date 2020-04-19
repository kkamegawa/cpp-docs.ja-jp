---
title: add_const クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: 6f27a8e4bc0bea3a469d46a56e8885dabe5894df
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456579"
---
# <a name="addconst-class"></a>add_const クラス

型から const 型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>パラメーター

*~* \
変更する型。

## <a name="remarks"></a>Remarks

この型修飾子のインスタンスは、 *ty*が参照、関数、または const で修飾された型で*ある場合は*、修飾型を保持`const Ty`します。それ以外の場合は、を保持します。

## <a name="example"></a>例

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_const クラス](../standard-library/remove-const-class.md)
