---
title: is_base_of クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: d56222f218033d00583e5e3def9790720ef7bb94
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456618"
---
# <a name="isbaseof-class"></a>is_base_of クラス

一方の型がもう一方の型の基底クラスであるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>パラメーター

*常用*\
テスト対象の基底クラス。

*導出*\
テスト対象の派生型。

## <a name="remarks"></a>Remarks

型の述語のインスタンスは、型の*ベース*が*派生*型の基底クラスである場合は true を保持します。それ以外の場合は、false を保持します。

## <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[is_convertible クラス](../standard-library/is-convertible-class.md)
