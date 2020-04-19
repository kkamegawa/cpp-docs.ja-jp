---
title: '&lt;tuple&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- tuple/std::operator!=
- tuple/std::operator>
- tuple/std::operator>=
- tuple/std::operator<
- tuple/std::operator<=
- tuple/std::operator==
ms.assetid: f25752dc-d3e2-4e12-b5ac-9a8682ca60ed
ms.openlocfilehash: 5554f08f32048bafde5bdb2c316e12e1e01c6ffb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241657"
---
# <a name="lttuplegt-operators"></a>&lt;tuple&gt; 演算子

## <a name="op_neq"></a> operator!=

`tuple` オブジェクトどうしが等しくないかどうかを比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator!=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

この関数は、`N` が 0 の場合は false、それ以外の場合は `get<0>(tpl1) != get<0>(tpl2) || get<1>(tpl1) != get<1>(tpl2) || ... || get<N - 1>(tpl1) == get<N - 1>(tpl2)` を返します。

### <a name="example"></a>例

```cpp
// std__tuple__operator_ne.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 != c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 != c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_lt"></a> 演算子&lt;

`tuple` オブジェクトの大小関係 (未満) を比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator<(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

この関数は、`N` が 0 より大きくかつ `tpl1` 内の最初に異なる値が `tpl2` 内の対応する値よりも小さい場合は true、それ以外の場合は false を返します。

### <a name="example"></a>例

```cpp
// std__tuple__operator_lt.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 < c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 < c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_lt_eq"></a> 演算子&lt;=

`tuple` オブジェクトの大小関係 (以下) を比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator<=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

`!(tpl2 < tpl1)` が返されます。

### <a name="example"></a>例

```cpp
// std__tuple__operator_le.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 <= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 <= c0);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```

## <a name="op_eq_eq"></a> 演算子 = =

`tuple` オブジェクトどうしが等しいかどうかを比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator==(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

この関数は、`N` が 0 の場合は true、それ以外の場合は `get<0>(tpl1) == get<0>(tpl2) && get<1>(tpl1) == get<1>(tpl2) && ... && get<N - 1>(tpl1) == get<N - 1>(tpl2)` を返します。

### <a name="example"></a>例

```cpp
// std__tuple__operator_eq.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 == c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 == c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```

## <a name="op_gt"></a> 演算子&gt;

`tuple` オブジェクトの大小関係 (より大きい) を比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator>(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

`tpl2 < tpl1` が返されます。

### <a name="example"></a>例

```cpp
// std__tuple__operator_gt.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 > c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 > c0);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_gt_eq"></a> 演算子&gt;=

`tuple` オブジェクトの大小関係 (以上) を比較します。

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator>=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

### <a name="remarks"></a>Remarks

`!(tpl1 < tpl2)` が返されます。

### <a name="example"></a>例

```cpp
// std__tuple__operator_ge.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 >= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 >= c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```
