---
title: allocator クラス
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
ms.openlocfilehash: 40e99901d4d4105902010a9e5b71ed3edf7d00db
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518867"
---
# <a name="allocator-class"></a>allocator クラス

このテンプレート クラスは、記憶域の割り当てと型のオブジェクトの配列の解放を管理するオブジェクトを表します`Type`します。 クラスのオブジェクト`allocator`は C++ 標準ライブラリのいくつかのコンテナー テンプレート クラスのコンス トラクターで指定された既定のアロケーター オブジェクト。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>パラメーター

*Type*<br/>
ストレージが割り当てまたは割り当て解除されるオブジェクトの型。

## <a name="remarks"></a>Remarks

すべての C++ 標準ライブラリ コンテナーは、その既定値はテンプレート パラメーターを持ちます`allocator`します。 カスタム アロケーターを持つコンテナーを作成すると、そのコンテナーの要素の割り当てと解放を制御できます。

たとえば、アロケーター オブジェクトは、プライベート ヒープまたは共有メモリ内でストレージを割り当てたり、小さなまたは大きなオブジェクトのサイズ用に最適化したりできます。 さらに、種類の型定義を介して、共有メモリを管理する特殊なアクセサー オブジェクトを経由で要素にアクセスすること、または自動ガベージ コレクションを実行することを指定できます。 そのため、アロケーター オブジェクトを使用してストレージを割り当てるクラスでは、C++ 標準ライブラリのコンテナーと同様に、これらの型を使用してポインターおよび参照オブジェクトを宣言する必要があります。

<strong>(C++ 98/03 のみ)</strong> Allocator クラスから派生するときに指定する必要が、[再バインド](#rebind)構造体が`_Other`typedef で新しく派生するクラスを参照します。

したがって、アロケーターは、次の型を定義します。

- [ポインター](#pointer)へのポインターのように動作`Type`します。

- [const_pointer](#const_pointer)への const ポインターのように動作`Type`します。

- [参照](#reference)への参照のように動作`Type`します。

- [const_reference](#const_reference)への const 参照のように動作`Type`します。

これら`Type`は割り当てられる要素に対してポインターと参照を行う必要のある形式を指定します。 ( [allocator::pointer](#pointer)が必ずしも同じ`Type*`のすべてのアロケーター オブジェクトがあるにもかかわらず、クラスの明確な定義`allocator`)。

**C++ 11 以降:** アロケーターでの移動操作を有効にするには、最小限のアロケーター インターフェイスを使用し、さらにコピー コンストラクター、== 演算子、! = 演算子、allocate、および deallocate を実装します。 詳細および例については、「[アロケーター](../standard-library/allocators.md)」を参照してください。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[allocator](#allocator)|`allocator` オブジェクトを作成するために使用するコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[const_pointer](#const_pointer)|アロケーターによって管理されるオブジェクトの型に対する定数ポインターを提供する型。|
|[const_reference](#const_reference)|アロケーターによって管理されるオブジェクトの型に対する定数参照を提供する型。|
|[difference_type](#difference_type)|アロケーターによって管理されるオブジェクトの型に対するポインターの値の差を表すことができる符号付き整数型。|
|[pointer](#pointer)|アロケーターによって管理されるオブジェクトの型に対するポインターを提供する型。|
|[reference](#reference)|アロケーターによって管理されるオブジェクトの型に対する参照を提供する型。|
|[size_type](#size_type)|テンプレート クラス `allocator` のオブジェクトが割り当てることができる、シーケンスの長さを表すことのできる符号なし整数型。|
|[value_type](#value_type)|アロケーターによって管理される型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[address](#address)|値が指定されたオブジェクトのアドレスを検索します。|
|[allocate](#allocate)|指定された要素数だけは格納できるメモリのブロックを割り当てます。|
|[construct](#construct)|指定された値で初期化され、指定されたアドレスに配置される、指定された型のオブジェクトを構築します。|
|[deallocate](#deallocate)|指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。|
|[destroy](#destroy)|オブジェクトが格納されたメモリの割り当てを解除せずに、オブジェクトのデストラクターを呼び出します。|
|[max_size](#max_size)|空きメモリがすべて使用される前に `allocator` クラスによって割り当てることのできる、型 `Type` の要素の数を返します。|
|[rebind](#rebind)|1 つの型のオブジェクトのアロケーターを使用して別の型のオブジェクトのストレージの割り当てを可能にする構造体。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|`allocator` オブジェクトを別の `allocator` オブジェクトに割り当てます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<memory>

**名前空間:** std

## <a name="address"></a>  allocator::address

値が指定されたオブジェクトのアドレスを検索します。

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

### <a name="parameters"></a>パラメーター

*val*<br/>
アドレスが検索対象となっているオブジェクトの const 値または nonconst 値。

### <a name="return-value"></a>戻り値

見つかった const 値または nonconst 値のそれぞれのオブジェクトに対する const ポインターまたは nonconst ポインター。

### <a name="remarks"></a>Remarks

メンバー関数のアドレスを返す*val*で、ポインターのために必要なフォームに割り当てられた要素。

### <a name="example"></a>例

```cpp
// allocator_address.cpp
// compile with: /EHsc
#include <memory>
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 8;
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );
   // v1Ptr = v1Alloc.address( k );
   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.
```

## <a name="allocate"></a>  allocator::allocate

指定された要素数だけは格納できるメモリのブロックを割り当てます。

```cpp
pointer allocate(size_type count, const void* _Hint);
```

### <a name="parameters"></a>パラメーター

*count*<br/>
十分な記憶域を割り当てる要素の数。

*_Hint*<br/>
アロケーター オブジェクトを支援できる const ポインターは、記憶域への要求を、要求の前に割り当てられたオブジェクトのアドレスを見つけることで満たします。

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター、またはメモリが割り当てられていない場合は null。

### <a name="remarks"></a>Remarks

メンバー関数は、のストレージ型の count 要素の配列を割り当てます`Type`、新しい演算子の呼び出しによって (*カウント*)。 この関数は、割り当てられたオブジェクトへのポインターを返します。 hint 引数は、参照の局所性を向上することにおいて、一部のアロケーターに役立ちます。有効な選択肢は、同じアロケーターによって以前に割り当てられ、まだ割り当て解除されていないオブジェクトのアドレスです。 hint を指定しない場合は、代わりに Null ポインター引数を使用します。

### <a name="example"></a>例

```cpp
// allocator_allocate.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<int> v1Alloc;
   allocator<int>::pointer v1aPtr;
   v1aPtr = v1Alloc.allocate ( 10 );

   int i;
   for ( i = 0 ; i < 10 ; i++ )
   {
      v1aPtr[ i ] = i;
   }

   for ( i = 0 ; i < 10 ; i++ )
   {
      cout << v1aPtr[ i ] << " ";
   }
   cout << endl;
   v1Alloc.deallocate( v1aPtr, 10 );
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

## <a name="allocator"></a>  allocator::allocator

オブジェクトを割り当てるために使用するコンストラクター。

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
allocator(const allocator<Other>& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするアロケーター オブジェクト。

### <a name="remarks"></a>Remarks

コンストラクターは何も行いません。 ただし、通常は、別のアロケーター オブジェクトから構築されたアロケーター オブジェクトは、それと等しいことを比較し、オブジェクトの割り当ての混在と、2 つのアロケーター オブジェクト間の解放を許可する必要があります。

### <a name="example"></a>例

```cpp
// allocator_allocator.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int( int i )
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<double> Alloc;
   vector <Int>:: allocator_type v1Alloc;

   allocator<double> cAlloc(Alloc);
   allocator<Int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

## <a name="const_pointer"></a>  allocator::const_pointer

アロケーターによって管理されるオブジェクトの型に対する定数ポインターを提供する型。

```cpp
typedef const value_type *const_pointer;
```

### <a name="remarks"></a>Remarks

ポインター型オブジェクトを表します`ptr`により、式を指定できる`*ptr`、テンプレート クラス アロケーターのオブジェクトを割り当てることができる任意の const オブジェクト。

### <a name="example"></a>例

```cpp
// allocator_const_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 10;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer's address found has a value of: "
        << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer's address found has a value of: 10.
```

## <a name="const_reference"></a>  allocator::const_reference

アロケーターによって管理されるオブジェクトの型に対する定数参照を提供する型。

```cpp
typedef const value_type& const_reference;
```

### <a name="remarks"></a>Remarks

参照型は、テンプレート クラス アロケーターのオブジェクトを割り当てることができる任意の const オブジェクトを指定できるオブジェクトを記述します。

### <a name="example"></a>例

```cpp
// allocator_const_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::const_reference vcref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vcref << ",\n the first element in the vector." << endl;

   // const references can have their elements modified,
   // so the following would generate an error:
   // vcref = 150;
   // but the value of the first element could be modified through
   // its nonconst iterator and the const reference would remain valid
*vfIter = 175;
   cout << "The value of the element referred to by vcref,"
        <<"\n after nofication through its nonconst iterator, is: "
        << vcref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The value of the element referred to by vcref,
after nofication through its nonconst iterator, is: 175.
```

## <a name="construct"></a>  allocator::construct

指定された値で初期化され、指定されたアドレスに配置される、指定された型のオブジェクトを構築します。

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
void construct(pointer ptr, _Other&&...   val);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
オブジェクトが構築される場所へのポインター。

*val*<br/>
構築されるオブジェクトが初期化される値。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、**new** ( ( `void` \*) `ptr` ) **Type** ( `val` ) と同じです。

### <a name="example"></a>例

```cpp
// allocator_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 6, kB = 7;
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The modified vector v1 is:
( 3 7 9 12 15 18 21 ).
```

## <a name="deallocate"></a>  allocator::deallocate

指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
記憶域から割り当てを解除される最初のオブジェクトへのポインター。

*count*<br/>
記憶域から割り当てを解除されるオブジェクトの数。

### <a name="remarks"></a>Remarks

メンバー関数は、型の count 個のオブジェクトの配列の記憶域を解放する`Type`から始まる*ptr*、呼び出して`operator delete(ptr)`します。 ポインター *ptr*が返されている前の呼び出しによって[割り当てる](#allocate)等しくを比較するアロケーター オブジェクトに **\*これ** 配列を割り当てる同じサイズと型のオブジェクトです。 `deallocate` は例外をスローしません。

### <a name="example"></a>例

メンバー関数の使用例については、「[allocator::allocate](#allocate)」を参照してください。

## <a name="destroy"></a>  allocator::destroy

オブジェクトが格納されたメモリの割り当てを解除せずに、オブジェクトのデストラクターを呼び出します。

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
破棄するオブジェクトのアドレスを指定するポインター。

### <a name="remarks"></a>Remarks

メンバー関数で指定されたオブジェクトの破棄*ptr*、デストラクターを呼び出すことによって`ptr->`**型**::**~ 型**します。

### <a name="example"></a>例

```cpp
// allocator_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 12, kB = -99;
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The modified vector v1 is:
( 2 4 6 8 10 -99 14 ).
```

## <a name="difference_type"></a>  allocator::difference_type

アロケーターによって管理されるオブジェクトの型に対するポインターの値の差を表すことができる符号付き整数型。

```cpp
typedef ptrdiff_t difference_type;
```

### <a name="remarks"></a>Remarks

符号付き整数型は、テンプレート クラス アロケーターのオブジェクトが割り当てることができるシーケンス内にある 2 つの要素のアドレスの違いを表すことのできるオブジェクトを記述します。

### <a name="example"></a>例

```cpp
// allocator_diff_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 0 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1PtrA, v1PtrB;
   const int kA = 4, kB =12;
   v1PtrA = v1Alloc.address( kA );
   v1PtrB = v1Alloc.address( kB );
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;

   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;
   cout << "The difference between the integer's addresses is: "
        << v1diff << "." << endl;
}
```

```Output
The original vector v1 is:
( 0 2 4 6 8 10 12 14 ).
Pointer v1PtrA addresses 4.
Pointer v1PtrB addresses 12.
The difference between the integer's addresses is: 8.
```

## <a name="max_size"></a>  allocator::max_size

空きメモリがすべて使用される前にクラス アロケーター オブジェクトによって割り当てることのできる、型 `Type` の要素の数を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

割り当てることができる要素の数。

### <a name="example"></a>例

```cpp
// allocator_max_size.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   vector <double> v2;
   vector <double> ::iterator v2Iter;
   vector <double> :: allocator_type v2Alloc;
   allocator<int>::size_type v1size;
   v1size = v1Alloc.max_size( );

   cout << "The number of integers that can be allocated before\n"
        << " the free memory in the vector v1 is used up is: "
        << v1size << "." << endl;

   int ii;
   for ( ii = 1 ; ii <= 7 ; ii++ )
   {
      v2.push_back( ii * 10.0 );
   }

   cout << "The original vector v2 is:\n ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )
      cout << *v2Iter << " ";
   cout << ")." << endl;
   allocator<double>::size_type v2size;
   v2size = v2Alloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v2 is used up is: "
        << v2size << "." << endl;
}
```

## <a name="op_eq"></a>  allocator::operator=

1 つのアロケーター オブジェクトを別のアロケーター オブジェクトに割り当てます。

```cpp
template <class Other>
allocator<Type>& operator=(const allocator<Other>& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
このような別のオブジェクトに割り当てられるアロケーター オブジェクト。

### <a name="return-value"></a>戻り値

アロケーター オブジェクトへの参照

### <a name="remarks"></a>Remarks

テンプレートの代入演算子は、何も行いません。 ただし、通常は、別のアロケーター オブジェクトに割り当てられたアロケーター オブジェクトは、それと等しいことを比較し、オブジェクトの割り当ての混在と、2 つのアロケーター オブジェクト間の解放を許可する必要があります。

### <a name="example"></a>例

```cpp
// allocator_op_assign.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( ) {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<Int> Alloc;
   allocator<Int> cAlloc ;
   cAlloc = Alloc;
}
```

## <a name="pointer"></a>  allocator::pointer

アロケーターによって管理されるオブジェクトの型に対するポインターを提供する型。

```cpp
typedef value_type *pointer;
```

### <a name="remarks"></a>Remarks

ポインター型オブジェクトを表します`ptr`により、式を指定できる **\*ptr**、任意のオブジェクトをテンプレート クラス アロケーターのオブジェクトを割り当てることができます。

### <a name="example"></a>例

```cpp
// allocator_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 12;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.
```

## <a name="rebind"></a>  allocator::rebind

1 つの型のオブジェクトのアロケーターを使用して別の型のオブジェクトのストレージの割り当てを可能にする構造体。
```cpp
struct rebind {    typedef allocator<_Other> other ;    };
```

### <a name="parameters"></a>パラメーター

*other*<br/>
メモリが割り当てられる要素の型。

### <a name="remarks"></a>Remarks

この構造体は、実装されているコンテナーの要素の型とは異なる型のメモリの割り当てに役立ちます。

メンバー テンプレート クラスは、型 other を定義します。 その唯一の目的は、所定の型名 **allocator**\< **Type**> で、型名 **allocator**\<_ **Other**> を提供することです。

たとえば、アロケーター オブジェクトは、指定された`al`型の`A`、型のオブジェクトを割り当てることができます`_Other`式を使用します。

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

または、次のように型を記述して、ポインター型を指定することができます。

```cpp
A::rebind<Other>::other::pointer
```

### <a name="example"></a>例

```cpp
// allocator_rebind.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

typedef vector<int>::allocator_type IntAlloc;
int main( )
{
   IntAlloc v1Iter;
   vector<int> v1;

   IntAlloc::rebind<char>::other::pointer pszC =
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);

   int * pInt = v1Iter.allocate(10);
}
```

## <a name="reference"></a>  allocator::reference

アロケーターによって管理されるオブジェクトの型に対する参照を提供する型。

```cpp
typedef value_type& reference;
```

### <a name="remarks"></a>Remarks

参照型は、テンプレート クラスのアロケーター オブジェクトを割り当てることができる任意のオブジェクトを指定できるオブジェクトを記述します。

### <a name="example"></a>例

```cpp
// allocator_reference.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::reference vref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vref << ",\n the first element in the vector." << endl;

   // nonconst references can have their elements modified
   vref = 150;
   cout << "The element referred to by vref after being modified is: "
        << vref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The element referred to by vref after being modified is: 150.
```

## <a name="size_type"></a>  allocator::size_type

テンプレート クラス アロケーターのオブジェクトが割り当てることができる、シーケンスの長さを表すことのできる符号なし整数型。

```cpp
typedef size_t size_type;
```

### <a name="example"></a>例

```cpp
// allocator_size_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   allocator<double>::size_type vsize;
   vsize = vAlloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v is used up is: "
        << vsize << "." << endl;
}
```

## <a name="value_type"></a>  allocator::value_type

アロケーターによって管理される型。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Type` のシノニムです。

### <a name="example"></a>例

```cpp
// allocator_value_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::value_type vecVal = 150.0;
*vfIter = vecVal;
   cout << "The value of the element addressed by vfIter is: "
        << *vfIter << ",\n the first element in the vector." << endl;

   cout << "The modified vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element addressed by vfIter is: 150,
the first element in the vector.
The modified vector v is:
( 150 200 300 400 500 600 700 ).
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
