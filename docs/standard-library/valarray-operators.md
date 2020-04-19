---
title: '&lt;valarray&gt; 演算子'
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 231bad65e2af1ee2ab800890c83cc50e584a8c6a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246108"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray&gt; 演算子

## <a name="op_neq"></a> operator!=

サイズが等しい 2 つの valarray の対応する要素が等しくないか、またはある valarray のすべての要素が指定値と等しくないかをテストします。

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
要素が等しくないことをテストする 2 つの valarray のうち 1 つ目の valarray。

*そうです*\
要素が等しくないことをテストする 2 つの valarray のうち 2 つ目の valarray。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**: 対応する要素が等しくない場合。

- **false**: 対応する要素が等しい場合。

### <a name="remarks"></a>Remarks

1 つ目のテンプレート演算子は、クラスのオブジェクトを返します[valarray\<bool >](../standard-library/valarray-bool-class.md)、その各要素の`I`は`left[I] != right[I]`します。

2 番目のテンプレート演算子は、要素に格納`I``left[I] != right`します。

3 番目のテンプレート演算子は、要素に格納`I``left != right[I]`します。

### <a name="example"></a>例

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_mod"></a> operator %

サイズが等しい 2 つの valarray の対応する要素を除算した剰余か、valarray を指定値で除算した剰余、または指定値を valarray で除算した剰余を取得します。

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
被除数の役割を果たし、別の値または valarray で除算する値または valarray。

*そうです*\
除数の役割を果たし、別の値または valarray を除算する値または valarray。

### <a name="return-value"></a>戻り値

要素ごとの剰余要素が valarray の*左*で割った値*右*します。

### <a name="example"></a>例

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="op_amp"></a> 演算子&amp;

サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの **AND** を計算した結果を取得します。

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素をビットごとに `AND` で結合する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

*そうです*\
それぞれの要素をビットごとに `AND` で結合する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

### <a name="return-value"></a>戻り値

ビットごとの AND 演算の要素ごとの組み合わせ要素が valarray の*左*と*右*します。

### <a name="remarks"></a>Remarks

ビットごとの演算は、ビットを操作にのみ使用できます**char**と**int**データ型とバリアントできません**float**、**double**、 **longdouble**、 **void**、 **bool**またはその他より複雑なデータ型。

ビット演算 `AND` は論理 `AND` と同じ真理値表を持ちますが、個々のビットのレベルでデータ型に適用されます。 [operator&&](#op_amp_amp) は要素レベルで適用され、すべての非ゼロ値を true と見なし、結果はブール値から成る valarray になります。 ビット演算`AND`[演算子 (& a)](#op_amp)、これに対し、0 または 1 のビットごとの演算の結果に応じて、以外の値を含む valarray になることができます。

### <a name="example"></a>例

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
```

## <a name="op_amp_amp"></a> 演算子&amp;&amp;

サイズが等しい 2 つの valarray の対応する要素間、または valarray と valarray の要素型の指定値との間で論理 **AND** を計算した結果を取得します。

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を論理 `AND` で結合する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と結合する要素型の指定値。

*そうです*\
それぞれの要素を論理 `AND` で結合する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と結合する要素型の指定値。

### <a name="return-value"></a>戻り値

Valarray の要素は、ブール型のの論理要素ごとの組み合わせ`AND`操作の*左*と*右*します。

### <a name="remarks"></a>Remarks

論理`ANDoperator&&`適用は要素レベルでのブール値を含む valarray とが true で、結果として、すべての非ゼロ値をカウントします。 ビットごとのバージョンの`AND`、[演算子 &、](#op_amp)、これに対し、0 または 1 のビットごとの演算の結果に応じて、以外の値を含む valarray になることができます。

### <a name="example"></a>例

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt"></a> 演算子&gt;

ある valarray の要素がサイズの等しい valarray の要素より大きいか、またはある valarray のすべての要素が指定値より大きいか、もしくは指定値未満であるかをテストします。

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を比較する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と比較する指定値。

*そうです*\
それぞれの要素を比較する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と比較する指定値。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**場合、*左*要素または値が、対応するよりも大きい*右*要素または値。

- **false**場合、*左*要素または値が、対応するよりも大きい*右*要素または値。

### <a name="remarks"></a>Remarks

2 つの valarray に含まれる要素数が異なる場合、結果は未定義です。

### <a name="example"></a>例

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_eq"></a> 演算子&gt;=

ある valarray の要素がサイズが等しい valarray の要素以上であるか、またはある valarray のすべての要素が valarray の要素型の指定値以上であるか、もしくは指定値以下であるかをテストします。

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を比較する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と比較する指定値。

*そうです*\
それぞれの要素を比較する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と比較する指定値。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**場合、*左*要素または値が、対応する以上*右*要素または値。

- **false**場合、*左*要素または値が、対応するよりも小さい*右*要素または値。

### <a name="remarks"></a>Remarks

2 つの valarray に含まれる要素数が異なる場合、結果は未定義です。

### <a name="example"></a>例

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_gt"></a> 演算子&gt;&gt;

valarray の各要素のビットを、指定された位置数だけ右にシフトさせるか、2 番目の valarray で指定された要素ごとの量だけ右にシフトさせます。

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
シフトする値、またはシフトする値を要素とする valarray。

*そうです*\
右シフトの量を示す値か、要素ごとの右シフトの量を示す要素から成る valarray。

### <a name="return-value"></a>戻り値

指定された量だけ右にシフトした要素から成る valarray。

### <a name="remarks"></a>Remarks

符号付きの数値の符号は保持されます。

### <a name="example"></a>例

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="op_lt"></a> 演算子&lt;

ある valarray の要素がサイズが等しい valarray の要素未満であるか、またはある valarray のすべての要素が valarray の要素型の指定値より大きいか、もしくは指定値未満であるかをテストします。

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を比較する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と比較する指定値。

*そうです*\
それぞれの要素を比較する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と比較する指定値。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**場合、*左*要素または値が、対応するよりも小さい*右*要素または値。

- **false**場合、*左*要素または値が、対応するよりも小さい*右*要素または値。

### <a name="remarks"></a>Remarks

2 つの valarray の要素数が異なる場合、結果は未定義です。

### <a name="example"></a>例

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_eq"></a> 演算子&lt;=

ある valarray の要素がサイズが等しい valarray の要素以下であるか、またはある valarray のすべての要素が valarray の要素型の指定値以上であるか、もしくは指定値以下であるかをテストします。

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を比較する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と比較する指定値。

*そうです*\
それぞれの要素を比較する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と比較する指定値。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**場合、*左*要素または値が、対応する小さい*右*要素または値。

- **false**場合、*左*要素または値が、対応するよりも大きい*右*要素または値。

### <a name="remarks"></a>Remarks

2 つの valarray の要素数が異なる場合、結果は未定義です。

### <a name="example"></a>例

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_lt"></a> 演算子&lt;&lt;

valarray の各要素のビットを、指定された位置数だけ左にシフトさせるか、2 番目の valarray で指定された要素ごとの量だけ左にシフトさせます。

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
シフトする値、またはシフトする値を要素とする valarray。

*そうです*\
左シフトの量を示す値か、要素ごとの左シフトの量を示す要素から成る valarray。

### <a name="return-value"></a>戻り値

指定された量だけ左にシフトした要素から成る valarray。

### <a name="remarks"></a>Remarks

符号付きの数値の符号は保持されます。

### <a name="example"></a>例

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="op_star"></a> 演算子 *

サイズが等しい 2 つの valarray の対応する要素間の要素ごとの積、または valarray と指定値との間の積を取得します。

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を乗算する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と乗算する指定値。

*そうです*\
それぞれの要素を乗算する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と乗算する指定値。

### <a name="return-value"></a>戻り値

要素ごとの積 valarray の*左*と*右*します。

### <a name="example"></a>例

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
```

## <a name="op_add"></a> operator +

サイズが等しい 2 つの valarray の対応する要素間の要素ごとの和、または valarray と指定値との間の和を取得します。

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を加算する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と加算する指定値。

*そうです*\
それぞれの要素を加算する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と加算する指定値。

### <a name="return-value"></a>戻り値

要素ごとの合計要素が valarray の*左*と*右*します。

### <a name="example"></a>例

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a> 演算子-

サイズが等しい 2 つの valarray の対応する要素間の要素ごとの差、または valarray と指定値との間の差を取得します。

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
被減数の役割を果たし、これから他の値または valarray を減算して差を求める値または valarray。

*そうです*\
減数の役割を果たし、他の値または valarray から減算して差を求める値または valarray。

### <a name="return-value"></a>戻り値

要素ごとの違いは、要素が valarray の*左*と*右*します。

### <a name="remarks"></a>Remarks

減算の説明で使われる算術用語:

差 = 被減数 - 減数

### <a name="example"></a>例

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="op_div"></a> 演算子/

サイズが等しい 2 つの valarray の対応する要素間の要素ごとの商、または valarray と指定値との間の商を取得します。

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
被除数の役割を果たし、別の値または valarray で除算して商を求める値または valarray。

*そうです*\
除数の役割を果たし、別の値または valarray を除算して商を求める値または valarray。

### <a name="return-value"></a>戻り値

要素ごとの商要素が valarray の*左*で割った値*右*します。

### <a name="remarks"></a>Remarks

除算の説明で使われる算術用語:

商 = 被除数 / 除数

### <a name="example"></a>例

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="op_eq_eq"></a> 演算子 = =

サイズが等しい 2 つの valarray の対応する要素が等しいか、またはある valarray のすべての要素が指定値と等しいかをテストします。

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
要素が等しいことをテストする 2 つの valarray のうち 1 つ目の valarray。

*そうです*\
要素が等しいことをテストする 2 つの valarray のうち 2 つ目の valarray。

### <a name="return-value"></a>戻り値

ブール値の valarray。ブール値は、それぞれ次のようになります。

- **true**: 対応する要素が等しい場合。

- **false**: 対応する要素が等しくない場合。

### <a name="remarks"></a>Remarks

1 つ目のテンプレート演算子は、クラスのオブジェクトを返します[valarray\<bool >](../standard-library/valarray-bool-class.md)、その各要素の`I`は`left[I] == right[I]`します。 2 番目のテンプレート演算子は、要素に格納`I``left[I] == right`します。 3 番目のテンプレート演算子は、要素に格納`I``left == right[I]`します。

### <a name="example"></a>例

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_xor"></a> 演算子 ^

サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの排他的 `OR` ( **XOR**) を計算した結果を取得します。

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素をビットごとに **XOR** で結合する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

*そうです*\
それぞれの要素をビットごとに **XOR** で結合する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

### <a name="return-value"></a>戻り値

ビットごとの要素ごとの組み合わせ要素が valarray **XOR**操作の*左*と*右*します。

### <a name="remarks"></a>Remarks

ビットごとの演算は、ビットを操作にのみ使用できます**char**と**int**データ型とバリアントできません**float**、**double**、 **long double**、 **void**、 **bool**またはその他より複雑なデータ型。

ビットごとの排他的`OR`( **XOR**) 次のセマンティクスがあります。ビット*b*1 と*b*2、 *b*1 **XOR** *b*2 は**true**場合ビットを 1 つが true であります。**false**両方のビットが false の場合、または両方のビットが true の場合。

### <a name="example"></a>例

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="op_or"></a> 演算子&#124;

サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの `OR` を計算した結果を取得します。

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素をビットごとに `OR` で結合する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

*そうです*\
それぞれの要素をビットごとに `OR` で結合する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素とビットごとに結合する要素型の指定値。

### <a name="return-value"></a>戻り値

ビットごとの要素ごとの組み合わせ要素が valarray`OR`操作の*左*と*右*します。

### <a name="remarks"></a>Remarks

ビットごとの演算は、ビットを操作にのみ使用できます**char**と**int**データ型とバリアントできません**float**、**double**、 **longdouble**、 **void**、 **bool**またはその他より複雑なデータ型。

ビットごとの OR は論理 `OR` と同じ真理値表を持ちますが、個々のビットのレベルでデータ型に適用されます。 ビット *b*1 と *b*2 について、最低 1 つのビットが true の場合、*b*1 `OR` *b*2 は **true** です。どちらのビットも false の場合は **false** になります。 論理 `OR`[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor) は要素レベルで適用され、すべての非ゼロ値を **true** と見なし、結果はブール値から成る valarray になります。 それに対して、ビットごとの OR `operator|` は、ビットごとの演算の結果に応じて、0 でも 1 でもない値を含む valarray になる場合があります。

### <a name="example"></a>例

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="op_lor"></a> 演算子&#124;&#124;

サイズが等しい 2 つの valarray の対応する要素間、または valarray と valarray の要素型の指定値との間で論理 `OR` を計算した結果を取得します。

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素を論理 `OR` で結合する 2 つの valarray のうち 1 つ目の valarray、または valarray の各要素と結合する要素型の指定値。

*そうです*\
それぞれの要素を論理 `OR` で結合する 2 つの valarray のうち 2 つ目の valarray、または valarray の各要素と結合する要素型の指定値。

### <a name="return-value"></a>戻り値

型の要素を持つ valarray **bool**要素ごとの論理 OR 演算の組み合わせと*左*と*右*します。

### <a name="remarks"></a>Remarks

論理`OR``operator||`としてすべての非ゼロ値のカウント、要素レベルで適用される**true**、され、結果はブール値の valarray。 それに対して、ビットごとのバージョンの `OR` である [operator&#124;](../standard-library/valarray-operators.md#op_or) は、ビットごとの演算の結果に応じて、0 でも 1 でもない値を含む valarray になる場合があります。

### <a name="example"></a>例

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
```
