---
title: divides 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::divides
helpviewer_keywords:
- divides struct
- divides class
ms.assetid: b9cf8e9c-6981-43a6-a6a3-8f761987dd7a
ms.openlocfilehash: 6c7297fa7c31470591b473ab5eadcde54e8c3b34
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244144"
---
# <a name="divides-struct"></a>divides 構造体

引数に対して除算演算 (`operator/`) を実行する定義済みの関数オブジェクト。

## <a name="syntax"></a>構文

```cpp
template <class Type = void>
struct divides : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator/
template <>
struct divides<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left)*/ std::forward<U>(Right));
};
```

### <a name="parameters"></a>パラメーター

*型*、 *T*、 *U*\
指定または推論された型のオペランドを受け取る `operator/` をサポートする型。

*左*\
除算演算の左オペランド。 特化されていないテンプレートは、型の左辺値参照引数を受け取る*型*します。 特殊化されたテンプレートはの完全転送を左辺値と右辺値参照引数の型を推論する*T*します。

*そうです*\
除算演算の右オペランド。 特化されていないテンプレートは、型の左辺値参照引数を受け取る*型*します。 特殊化されたテンプレートはの完全転送を左辺値と右辺値参照引数の型を推論する*U*します。

## <a name="return-value"></a>戻り値

`Left / Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator/` によって返された型が含まれます。

## <a name="example"></a>例

```cpp
// functional_divides.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 (6);
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i++ )
   {
      v1.push_back( 7.0 * i );
   }

   int j;
   for ( j = 1 ; j <= 6 ; j++ )
   {
      v2.push_back( 2.0 * j);
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise quotients of the elements of v1 & v2
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),
      divides<double>( ) );

   cout << "The element-wise quotients are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( 0 7 14 21 28 35 )
The vector v2 = ( 2 4 6 8 10 12 )
The element-wise quotients are: ( 0 1.75 2.33333 2.625 2.8 2.91667 )
```
