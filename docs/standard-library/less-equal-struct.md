---
title: "less_equal 構造体 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::less_equal
- xfunctional/std::less_equal
- std.less_equal
- less_equal
dev_langs:
- C++
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 58e188cc830140ace78777a03959a7f4e170f328
ms.lasthandoff: 02/24/2017

---
# <a name="lessequal-struct"></a>less_equal 構造体
引数に対して "以下" 演算 (`operator<=`) を実行する二項述語。  
  
## <a name="syntax"></a>構文  
  
```
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```  
  
#### <a name="parameters"></a>パラメーター  
 `Type`、`T`、`U`  
 指定または推論された型のオペランドを受け取る `operator<=` をサポートする任意の型。  
  
 `Left`  
 以下演算の左オペランド。 特殊化されていないテンプレートでは、`Type` 型の左辺値参照引数を使用します。 特殊化されたテンプレートは、推論された型 `T` の左辺値および右辺値参照引数の完全転送を行います。  
  
 `Right`  
 以下演算の右オペランド。 特殊化されていないテンプレートでは、`Type` 型の左辺値参照引数を使用します。 特殊化されたテンプレートは、推論された型 `U` の左辺値および右辺値参照引数の完全転送を行います。  
  
## <a name="return-value"></a>戻り値  
 `Left``<=``Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator<=` によって返された型が含まれます。  
  
## <a name="remarks"></a>コメント  
 二項述語 `less_equal`< `Type`> は、型 `Type` の要素値のセットの、等価クラスへの厳密弱順序を提供します。ただし、その型がそのように順序付けられる標準的な数学的要件を満たす場合のみです。 任意のポインター型に対する特殊化によって、要素の完全な順序付けが生成されます。この場合、一意の値を持つすべての要素が、相互の値に基づいて並べ替えられます。  
  
## <a name="example"></a>例  
  
```cpp  
// functional_less_equal.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <cstdlib>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
   vector <int>::reverse_iterator rIter1;  
   unsigned int randomNumber;  
  
   int i;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      if ( rand_s( &randomNumber ) == 0 )  
      {  
         // Convert the random number to be between 1 - 50000  
         // This is done for readability purposes  
         randomNumber = ( unsigned int) ((double)randomNumber /   
            (double) UINT_MAX * 50000) + 1;  
  
         v1.push_back( randomNumber );  
      }  
   }  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      v1.push_back( 2836 );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use the binary predicate less_equal<int>( )  
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## <a name="sample-output"></a>出力例  
  
```
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<functional>  
  
 **名前空間:** std  
  
## <a name="see-also"></a>関連項目  
 [C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)



