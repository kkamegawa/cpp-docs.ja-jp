---
title: '&lt;list&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 7b0b7540c1b9a55140405a55e8e034f9c6ec646c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246464"
---
# <a name="ltlistgt-operators"></a>&lt;list&gt; 演算子

## <a name="op_neq"></a> operator!=

演算子の左辺の list オブジェクトが右辺の list オブジェクトと等しくないかどうかを調べます。

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

リストが等しくない場合は **true**、リストが等しい場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの list は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
/* Output:
Lists not equal.
*/
```

## <a name="op_lt"></a> 演算子&lt;

演算子の左辺の list オブジェクトが右辺の list オブジェクトより小さいかどうかを調べます。

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list 未満である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の小なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
/* Output:
List c1 is less than list c2.
*/
```

## <a name="op_lt_eq"></a> 演算子&lt;=

演算子の左辺の list オブジェクトが右辺の list オブジェクト以下かどうかを調べます。

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list 以下である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の "以下" 関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="op_eq_eq"></a> 演算子 = =

演算子の左辺の list オブジェクトが右辺の list オブジェクトと等しいかどうかを調べます。

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list と等しい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの list は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
/* Output:
The lists are equal.
*/
```

## <a name="op_gt"></a> 演算子&gt;

演算子の左辺の list オブジェクトが右辺の list オブジェクトより大きいかどうかを調べます。

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list より大きい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の大なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="op_gt_eq"></a> 演算子&gt;=

演算子の左辺の list オブジェクトが右辺の list オブジェクト以上かどうかを調べます。

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list 以上である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

list オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の "以上" 関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
/* Output:
List c1 is greater than or equal to list c2.
*/
```
