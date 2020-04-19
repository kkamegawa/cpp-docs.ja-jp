---
title: raw_storage_iterator クラス
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: eb32d1846c4e94fbd275dcc416de4f37d9bb53f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240373"
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator クラス

アルゴリズムの結果を初期化されていないメモリに格納するために用意されたアダプター クラスです。

## <a name="syntax"></a>構文

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>パラメーター

*OutputIterator*\
格納されるオブジェクトの出力反復子を指定します。

*型*\
ストレージが割り当てられるオブジェクトの型。

## <a name="remarks"></a>Remarks

クラスは、型のオブジェクトを構築する出力反復子を表します`Type`で、生成するシーケンス。 クラスのオブジェクト`raw_storage_iterator` \< **ForwardIterator**、**型**> クラスの前方反復子オブジェクトを介してストレージにアクセス`ForwardIterator`、タイミングを指定します。オブジェクトを構築します。 オブジェクトのクラスの最初の`ForwardIterator`、式 **&\*最初**未構築のストレージを次のオブジェクトを指定する必要があります (型の`Type`) で生成されたシーケンス。

このアダプター クラスは、メモリの割り当てとオブジェクトの構築を分離する必要がある場合に使用されます。 `raw_storage_iterator` は、`malloc` 関数を使用して割り当てられたメモリなど、初期化されていないストレージにオブジェクトをコピーするために使用できます。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|指定した基になる出力反復子を使用して、生のストレージの反復子を構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[element_type](#element_type)|生のストレージ反復子によって格納される要素を記述する型を提供します。|
|[iter_type](#iter_type)|生のストレージ反復子の基になる反復子を記述する型を提供します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator*](#op_star)|出力反復子の式を実装するために使用される逆参照演算子\* `ii`  = `x`します。|
|[operator=](#op_eq)|生のストレージ反復子式を実装するために使用される代入演算子は、 \* `i`  =  `x`メモリに格納するためです。|
|[operator++](#op_add_add)|生のストレージ反復子の前置インクリメント演算子と後置インクリメント演算子。|

### <a name="element_type"></a> element_type

生のストレージ反復子によって格納される要素を記述する型を提供します。

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Remarks

型は raw_storage_iterator クラス テンプレート パラメーターのシノニム`Type`します。

### <a name="iter_type"></a> iter_type

生のストレージ反復子の基になる反復子を記述する型を提供します。

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `ForwardIterator` のシノニムです。

### <a name="op_star"></a> 演算子\*

生のストレージ反復子式 \* *ii* = *x* を実装するために使用される逆参照演算子。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>戻り値

生のストレージ反復子への参照

#### <a name="remarks"></a>Remarks

要件、`ForwardIterator`は、生のストレージ反復子の式のみを必要を満たす必要があります\* *ii* = *t*有効であるし、は何も書かれている、**operator**または`operator=`自体にします。 メンバー演算子は、この実装で返します **\*this**ように[演算子 =](#op_eq)(**constType**(& a)) を指定する式の実際の格納を実行できますなど\* *ptr* = `val`します。

#### <a name="example"></a>例

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_eq"></a> 演算子 =

生のストレージ反復子式 \* *i* = *x* をメモリへの格納用に実装するために使用される代入演算子。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>パラメーター

*val*\
型のオブジェクトの値`Type`メモリに挿入します。

#### <a name="return-value"></a>戻り値

この演算子は、メモリに `val` を挿入し、生のストレージ反復子への参照を返します。

#### <a name="remarks"></a>Remarks

要件、`ForwardIterator`生のストレージ反復子が満たす必要がある状態は、式のみを必要と\* *ii* = *t* 、有効であること、およびについて何も書かれています。**演算子**または`operator=`自体にします。 これらのメンバー演算子は **\*this** を返します。

代入演算子は、placement new 式 **new** ( ( `void` \*)&\* **first**) **Type**( `val`) を評価することによって、格納された反復子の値 first を使用して出力シーケンス内に次のオブジェクトを構築します。

#### <a name="example"></a>例

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_add_add"></a> + + 演算子

生のストレージ反復子の前置インクリメント演算子と後置インクリメント演算子。

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>戻り値

生のストレージ反復子または生のストレージ反復子への参照。

#### <a name="remarks"></a>Remarks

1 つ目の演算子は、最終的に抽出し、型のオブジェクトを格納を試みます`CharType`関連付けられている入力ストリームから。 2 つ目の演算子は、オブジェクトのコピーを作成して、オブジェクトをインクリメントしてから、そのコピーを返します。

最初の preincrement 演算子は格納されている出力反復子オブジェクトをインクリメントしてから、 **\*this** を返します。

2 つ目の postincrement 演算子は **\*this** のコピーを作成し、格納されている出力反復子オブジェクトをインクリメントしてからコピーを返します。

コンス トラクター ストア`first`出力反復子オブジェクトとして。

#### <a name="example"></a>例

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a> raw_storage_iterator

指定した基になる出力反復子を使用して、生のストレージの反復子を構築します。

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>パラメーター

*まずは*\
構築されている `raw_storage_iterator` オブジェクトを基にすることになる前方反復子。

#### <a name="example"></a>例

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
```

```Output
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
```