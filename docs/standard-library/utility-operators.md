---
title: '&lt;utility&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: ec6c996487dc2e6c5ce628fe5e080b4f601479d9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246289"
---
# <a name="ltutilitygt-operators"></a>&lt;utility&gt; 演算子

> [!NOTE]
> 演算子を使用して`Type&`下に含まれている`namespace rel_ops`します。

## <a name="op_neq"></a> operator!=

演算子の左辺のペア オブジェクトが右辺のペア オブジェクトと等しくないかどうかを調べます。

```cpp
template <class Type>
    constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`pair` 型のオブジェクト。

*そうです*\
`pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

ペアが等しくない場合には **true**。等しい場合は **false**。

### <a name="remarks"></a>Remarks

ペアのそれぞれの要素が等しい場合に、ペアが等しくなります。 片方のペアの最初または 2 番目の要素のいずれかがもう一方のペアの対応する要素と等しくない場合には、2 つのペアは等しくありません。

### <a name="example"></a>例

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="op_eq_eq"></a> 演算子 = =

演算子の左辺のペア オブジェクトが右辺のペア オブジェクトと等しいかどうかを調べます。

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`pair` 型のオブジェクト。

*そうです*\
`pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

ペアが等しい場合には **true**。`pair` が等しくないときには **false**。

### <a name="remarks"></a>Remarks

ペアのそれぞれの要素が等しい場合に、ペアが等しくなります。 `left` が返されます。 **first** == `right`。 **first** && `left`。 **second** == `right`。 **second**。 片方のペアの最初または 2 番目の要素のいずれかがもう一方のペアの対応する要素と等しくない場合には、2 つのペアは等しくありません。

### <a name="example"></a>例

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="op_lt"></a> 演算子&lt;

演算子の左辺のペア オブジェクトが右辺のペア オブジェクトより小さいかどうかを調べます。

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
演算子の左辺にある `pair` 型のオブジェクト。

*そうです*\
演算子の右辺にある `pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の `pair` が演算子の右辺の `pair` より厳密に小さい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

`left` `pair`オブジェクトは厳密にはより小さい`right``pair`オブジェクトの場合*左*が等しくないと、それよりも小さい*右*します。

ペアを比較する場合、2 つのペアの最初の要素の値が、最も優先度が高くなります。 最初の要素の値が異なる場合、その比較の結果がペアの比較の結果として扱われます。 最初の要素の値が同じである場合、2 番目の要素の値が比較され、その比較の結果がペアの比較の結果として扱われます。

### <a name="example"></a>例

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="op_lt_eq"></a> 演算子&lt;=

演算子の左辺のペア オブジェクトが右辺のペア オブジェクト以下かどうかを調べます。

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
演算子の左辺にある `pair` 型のオブジェクト。

*そうです*\
演算子の右辺にある `pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の `pair` が演算子の右辺の `pair` 以下である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

ペアを比較する場合、2 つのペアの最初の要素の値が、最も優先度が高くなります。 最初の要素の値が異なる場合、その比較の結果がペアの比較の結果として扱われます。 最初の要素の値が同じである場合、2 番目の要素の値が比較され、その比較の結果がペアの比較の結果として扱われます。

### <a name="example"></a>例

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="op_gt"></a> 演算子&gt;

演算子の左辺のペア オブジェクトが右辺のペア オブジェクトより大きいかどうかを調べます。

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
演算子の左辺にある `pair` 型のオブジェクト。

*そうです*\
演算子の右辺にある `pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺にある `pair` が演算子の右辺の `pair` より厳密に大きい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

`left` `pair`オブジェクトはより厳密に大きいと呼ばれます、 `right` `pair`オブジェクトの場合*左*より大きくかつ等しくない*右*します。

ペアを比較する場合、2 つのペアの最初の要素の値が、最も優先度が高くなります。 最初の要素の値が異なる場合、その比較の結果がペアの比較の結果として扱われます。 最初の要素の値が同じである場合、2 番目の要素の値が比較され、その比較の結果がペアの比較の結果として扱われます。

### <a name="example"></a>例

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="op_gt_eq"></a> 演算子&gt;=

演算子の左辺のペア オブジェクトが右辺のペア オブジェクト以上かどうかを調べます。

```cpp
template <class Type>
    constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
演算子の左辺にある `pair` 型のオブジェクト。

*そうです*\
演算子の右辺にある `pair` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の `pair` が演算子の右辺の `pair` 以上である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

ペアを比較する場合、2 つのペアの最初の要素の値が、最も優先度が高くなります。 最初の要素の値が異なる場合、その比較の結果がペアの比較の結果として扱われます。 最初の要素の値が同じである場合、2 番目の要素の値が比較され、その比較の結果がペアの比較の結果として扱われます。

### <a name="example"></a>例

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```
