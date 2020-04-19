---
title: modulus 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::modulus
helpviewer_keywords:
- modulus class
- modulus struct
ms.assetid: 86d342f7-b7b1-46a4-b0bb-6b7ae827369b
ms.openlocfilehash: 20f2070c5b835d67e06d64a0a1b05141f08cf373
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246803"
---
# <a name="modulus-struct"></a>modulus 構造体

引数に対して剰余演算 (`operator%`) を実行する定義済みの関数オブジェクト。

## <a name="syntax"></a>構文

```
template <class Type = void>
struct modulus : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator%
template <>
struct modulus<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) % std::forward<U>(Right));
};
```

### <a name="parameters"></a>パラメーター

*型*、 *T*、 *U*\
指定または推論された型のオペランドを受け取る `operator%` をサポートする任意の型。

*左*\
剰余演算の左オペランド。 特化されていないテンプレートは、型の左辺値参照引数を受け取る*型*します。 特殊化されたテンプレートはの完全転送を左辺値と右辺値参照引数の型を推論する*T*します。

*そうです*\
剰余演算の右オペランド。 特化されていないテンプレートは、型の左辺値参照引数を受け取る*型*します。 特殊化されたテンプレートはの完全転送を左辺値と右辺値参照引数の型を推論する*U*します。

## <a name="return-value"></a>戻り値

`Left % Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator%` によって返された型が含まれます。

## <a name="remarks"></a>Remarks

`modulus` ファンクターは、基本データ型の整数型、または `operator%` を実装しているユーザー定義型に制限されます。

## <a name="example"></a>例

```cpp
// functional_modulus.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <int> v1, v2, v3 ( 6 );
   vector <int>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 1 ; i <= 6 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int j;
   for ( j = 1 ; j <= 6 ; j++ )
   {
      v2.push_back( 3 * j );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise remainders of the elements of v1 & v2
   transform (v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      modulus<int>() );

   cout << "The element-wise remainders of the modular division\n are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 5 10 15 20 25 30 )
The vector v2 = ( 3 6 9 12 15 18 )
The element-wise remainders of the modular division
are: ( 2 4 6 8 10 12 )
```
