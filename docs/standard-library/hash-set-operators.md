---
title: '&lt;hash_set&gt; 演算子'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 3900e9c6e4fb7f5a163279165a51b440d138a8e5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452032"
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set&gt; 演算子

||||
|-|-|-|
|[operator!=](#op_neq)|[operator!= (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[operator== (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>  operator!=

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

演算子の左辺の hash_set オブジェクトが右辺の hash_set オブジェクトと等しくないかどうかを調べます。

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`hash_set` 型のオブジェクト。

*そうです*\
`hash_set` 型のオブジェクト。

### <a name="return-value"></a>戻り値

hash_sets が等しくない場合は **true**、hash_sets が等しい場合は **false**。

### <a name="remarks"></a>Remarks

hash_set オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの hash_sets は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

[< Hash_map >](../standard-library/hash-map.md)と[< > hash_set](../standard-library/hash-set.md)ヘッダーファイルのメンバーは、 [stdext 名前空間](../standard-library/stdext-namespace.md)にあります。

### <a name="example"></a>例

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="op_eq_eq"></a>  operator==

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

演算子の左辺の hash_set オブジェクトが右辺の hash_set オブジェクトと等しいかどうかを調べます。

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`hash_set` 型のオブジェクト。

*そうです*\
`hash_set` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の hash_set が演算子の右辺の hash_set と等しい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

hash_set オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの hash_sets は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="op_neq_hash_multiset"></a>  operator!= (hash_multiset)

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

演算子の左側の hash_multiset オブジェクトが右側の hash_multiset オブジェクトと等しくないかどうかをテストします。

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`hash_multiset` 型のオブジェクト。

*そうです*\
`hash_multiset` 型のオブジェクト。

### <a name="return-value"></a>戻り値

hash_multisets が等しくない場合は **true**、hash_multisets が等しい場合は **false**。

### <a name="remarks"></a>Remarks

hash_multiset オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの hash_multisets は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="op_eq_eq_hash_multiset"></a>  operator== (hash_multiset)

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

演算子の左側の hash_multiset オブジェクトが右側の hash_multiset オブジェクトと等しいかどうかをテストします。

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
`hash_multiset` 型のオブジェクト。

*そうです*\
`hash_multiset` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の hash_multiset が演算子の右辺の hash_multiset と等しい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

hash_multiset オブジェクト間の比較は、要素のペアの比較に基づいています。 2 つの hash_multisets は、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

### <a name="example"></a>例

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>関連項目

[<hash_set>](../standard-library/hash-set.md)
