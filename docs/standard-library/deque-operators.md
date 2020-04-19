---
title: '&lt;deque&gt; の演算子'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 868909ac4346a59cade3660f288a0f0e71bc4ed0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245660"
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; の演算子

## <a name="op_neq"></a> operator!=

演算子の左側の deque オブジェクトが右側の deque オブジェクトと等しくないかどうかを調べます。

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

deque オブジェクトが等しくない場合は **true**、deque オブジェクトが等しい場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの deque オブジェクトは、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
```

```Output
The deques are not equal.
```

## <a name="op_lt"></a> 演算子&lt;

演算子の左側の deque オブジェクトが右側の deque オブジェクトより小さいかどうかを調べます。

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の deque が演算子の右辺の deque 未満である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の小なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
```

```Output
Deque c1 is less than deque c2.
```

## <a name="op_lt_eq"></a> 演算子&lt;=

演算子の左側の deque オブジェクトが右側の deque オブジェクト以下かどうかを調べます。

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の deque が演算子の右辺の deque 以下である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の "以下" 関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="op_eq_eq"></a> 演算子 = =

演算子の左側の deque オブジェクトが右側の deque オブジェクトと等しいかどうかを調べます。

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の deque が演算子の右辺の deque と等しい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの deque は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="op_gt"></a> 演算子&gt;

演算子の左側の deque オブジェクトが右側の deque オブジェクトより大きいかどうかを調べます。

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の deque が演算子の右辺の deque より大きい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の大なり関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="op_gt_eq"></a> 演算子&gt;=

演算子の左側の deque オブジェクトが右側の deque オブジェクト以上かどうかを調べます。

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`deque` 型のオブジェクト。

*そうです*\
`deque` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の deque が演算子の右辺の deque 以上である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

deque オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つのオブジェクト間の "以上" 関係は、最初の等しくない要素のペアの比較に基づいています。

### <a name="example"></a>例

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
```

```Output
Deque c1 is greater than or equal to deque c2.
```
