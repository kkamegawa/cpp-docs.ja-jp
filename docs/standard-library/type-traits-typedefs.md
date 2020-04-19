---
title: '&lt;type_traits&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: eff1a99fb95f15c6377e8a74cca36e718cbd6fd9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455083"
---
# <a name="lttypetraitsgt-typedefs"></a>&lt;type_traits&gt; typedef

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type"></a>  false_type Typedef

false 値を持つ整数定数を保持します。

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート `integral_constant` から特化したテンプレートのシノニムです。

### <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type"></a>  true_type Typedef

true 値を持つ整数定数を保持します。

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート `integral_constant` から特化したテンプレートのシノニムです。

### <a name="example"></a>例

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
