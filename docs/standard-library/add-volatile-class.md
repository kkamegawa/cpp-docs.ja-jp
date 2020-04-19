---
title: add_volatile クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: becea4ff52342a79d0b87ffe0022e2cf84c47949
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456531"
---
# <a name="addvolatile-class"></a>add_volatile クラス

指定した型から**volatile**型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

のインスタンスに`add_volatile<T>`は、t が参照、関数、または volatile で修飾された型で*ある場合は* *t* 、それ以外の場合は**volatile** *t*であるメンバー **typedef** `type`があります。エイリアス`add_volatile_t`は、メンバー **typedef** `type`にアクセスするためのショートカットです。

## <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_volatile クラス](../standard-library/remove-volatile-class.md)
