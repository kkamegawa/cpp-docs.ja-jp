---
title: back_insert_iterator クラス
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: d8f48b1f714697aff63a4ee658a69fce6dab8041
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459538"
---
# <a name="backinsertiterator-class"></a>back_insert_iterator クラス

出力反復子の要件を満たす反復子アダプターについて説明します。 シーケンスのバック エンドに要素を上書きではなく、挿入し、C++ のシーケンス コンテナーの反復子が提供する上書きセマンティクスとは異なるセマンティクスを提供します。 `back_insert_iterator` クラスはコンテナーの型でテンプレート化されます。

## <a name="syntax"></a>構文

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>パラメーター

*コンテナー*\
要素が `back_insert_iterator` によって後方に挿入されるコンテナーの型。

## <a name="remarks"></a>Remarks

コンテナーは償却定数時間でシーケンスの末尾に要素を挿入できる、有効な後方挿入シーケンスの要件を満たしている必要があります。 [deque クラス](../standard-library/deque-class.md)、[list クラス](../standard-library/list-class.md)、[vector クラス](../standard-library/vector-class.md)によって定義された、C++ 標準ライブラリ シーケンス コンテナーは、`push_back` メンバー関数を提供し、次の要件を満たします。 この 3 種類のコンテナー、および文字列はそれぞれ `back_insert_iterator` で使用するために改変される可能性があります。 `back_insert_iterator` は、常に、コンテナーで初期化されている必要があります。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|コンテナー内の最後の要素の後に要素を挿入する `back_insert_iterator` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[container_type](#container_type)|`back_insert_iterator` にコンテナーを提供する型。|
|[reference](#reference)|`back_insert_iterator` に参照を提供する型。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator*](#op_star)|後方挿入のための出力反復子式\* `i`  =  `x`を実装するために使用される逆参照演算子。|
|[operator++](#op_add_add)|値を格納できる次の位置に `back_insert_iterator` をインクリメントします。|
|[operator=](#op_eq)|後方挿入のための出力反復子式\* `i`  =  `x`を実装するために使用される代入演算子。|

## <a name="requirements"></a>必要条件

**ヘッダー**: \<iterator>

**名前空間:** std

## <a name="back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator

コンテナー内の最後の要素の後に要素を挿入する `back_insert_iterator` を構築します。

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>パラメーター

*続き*\
`back_insert_iterator` が要素を挿入するためのコンテナー。

### <a name="return-value"></a>戻り値

パラメーター コンテナーの `back_insert_iterator`。

### <a name="example"></a>例

```cpp
// back_insert_iterator_back_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions with member function
   back_inserter ( vec ) = 40;
   back_inserter ( vec ) = 50;

   // Alternatively, insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 600;
   backiter++;
*backiter = 700;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 1 2 3 ).
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).
```

## <a name="container_type"></a>  back_insert_iterator::container_type

`back_insert_iterator` にコンテナーを提供する型。

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **Container** のシノニムです。

### <a name="example"></a>例

```cpp
// back_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The original vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::container_type vec1 = vec;
   back_inserter ( vec1 ) = 40;

   cout << "After the insertion, the vector is: ( ";
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector vec is: ( 1 2 3 ).
After the insertion, the vector is: ( 1 2 3 40 ).
```

## <a name="op_star"></a>  back_insert_iterator::operator\*

出力反復子式 \* *i* = *x* を実装するために使用される逆参照演算子。

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>戻り値

コンテナーの後ろに挿入される要素への参照。

### <a name="remarks"></a>Remarks

出力反復子式 **\*Iter** = **value** を実装するために使用されます。 **Iter** がシーケンス内の要素をアドレス指定する反復子である場合、 **\*Iter** = **value** はその要素を値に置き換え、シーケンス内の要素の合計数は変えません。

### <a name="example"></a>例

```cpp
// back_insert_iterator_back_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).
```

## <a name="op_add_add"></a>  back_insert_iterator::operator++

値を格納できる次の位置に `back_insert_iterator` をインクリメントします。

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>戻り値

値を格納できる次の位置をアドレス指定する `back_insert_iterator`。

### <a name="remarks"></a>Remarks

preincrementation と postincrementation の演算子は、どちらも同じ結果を返します。

### <a name="example"></a>例

```cpp
// back_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 3 ; ++i )
   {
      vec.push_back ( 10 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;      // Increment to the next element
*backiter = 40;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 10 20 ).
After the insertions, the vector vec becomes: ( 10 20 30 40 ).
```

## <a name="op_eq"></a>  back_insert_iterator::operator=

値をコンテナーのバック エンドに追加またはプッシュします。

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>パラメーター

*val*\
コンテナーに挿入される値。

### <a name="return-value"></a>戻り値

コンテナーの後ろに挿入される最後の要素への参照。

### <a name="remarks"></a>Remarks

1 つ目のメンバー演算子は、`Container.push_back( val)` を評価し、

その後、`*this` を返します。 2 つ目のメンバー演算子は次の評価をします。

`container->push_back((typename Container::value_type&&)val)`、

その後、`*this` を返します。

### <a name="example"></a>例

```cpp
// back_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

## <a name="reference"></a>  back_insert_iterator::reference

`back_insert_iterator` に参照を提供する型。

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Remarks

この型は、関連するコンテナーによって制御されるシーケンスの要素への参照を示します。

### <a name="example"></a>例

```cpp
// back_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::reference
        RefLast = *(vec.end ( ) - 1 );
   cout << "The last element in the vector vec is: "
        << RefLast << "." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
The last element in the vector vec is: 3.
```

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
