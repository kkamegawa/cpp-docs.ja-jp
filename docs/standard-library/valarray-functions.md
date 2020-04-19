---
title: '&lt;valarray&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- valarray/std::abs
- valarray/std::acos
- valarray/std::asin
- valarray/std::atan
- valarray/std::atan2
- valarray/std::cos
- valarray/std::cosh
- valarray/std::exp
- valarray/std::log
- valarray/std::log10
- valarray/std::pow
- valarray/std::sin
- valarray/std::sinh
- valarray/std::sqrt
- valarray/std::swap
- valarray/std::tan
- valarray/std::tanh
ms.assetid: 109778fc-440e-4239-b23e-bafda2b165c2
helpviewer_keywords:
- std::abs [C++]
- std::acos [C++]
- std::asin [C++]
- std::atan [C++]
- std::atan2
- std::begin [C++]
- std::cos [C++]
- std::cosh [C++]
- std::end [C++]
- std::exp [C++]
- std::log [C++]
- std::log10
- std::pow [C++]
- std::sin [C++]
- std::sinh [C++]
- std::sqrt [C++]
- std::swap [C++]
- std::tan [C++]
- std::tanh [C++]
ms.openlocfilehash: 12275f93c751b4d9ffafcae62621b251a8bc9bfc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246687"
---
# <a name="ltvalarraygt-functions"></a>&lt;valarray&gt; 関数

## <a name="abs"></a> abs

入力 valarray の要素を演算し、入力 valarray の要素の絶対値と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> abs(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の絶対値と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_abs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 9 ), va2 ( 9 );
   for ( i = 0 ; i < 4 ; i++ )
      va1 [ i ] =  -i;
   for ( i = 4 ; i < 9 ; i++ )
      va1 [ i ] =  i;

   cout << "The initial valarray is: ";
      for (i = 0 ; i < 9 ; i++ )
         cout << va1 [ i ] << " ";
   cout << "." << endl;

   va2 = abs ( va1 );
   cout << "The absolute value of the initial valarray is: ";
      for (i = 0 ; i < 9 ; i++ )
         cout << va2 [ i ] << " ";
   cout << "." << endl;
}
```

```Output
The initial valarray is: 0 -1 -2 -3 4 5 6 7 8 .
The absolute value of the initial valarray is: 0 1 2 3 4 5 6 7 8 .
```

## <a name="acos"></a> acos

入力 valarray の要素を演算し、入力 valarray の要素のアークコサインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> acos(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のアークコサインと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

返される要素の単位はラジアンです。

戻り値は、コサイン値の入力との整合性がある 0 から +pi までの間の主値です。

### <a name="example"></a>例

```cpp
// valarray_acos.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  0.25 * i - 1;
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:";
   for (i = 0 ; i < 9 ; i++ )
      cout << " " << va1 [ i ];
   cout << endl;

   va2 = acos ( va1 );
   cout << "The arccosine of the initial valarray is:\n";
   for (i = 0 ; i < 9 ; i++ )
      cout << setw(10) << va2 [ i ]
         << "  radians, which is  "
         << setw(11) << (180/pi) * va2 [ i ]
         << "  degrees" << endl;
}
```

```Output
The initial valarray is: -1 -0.75 -0.5 -0.25 0 0.25 0.5 0.75 1
The arccosine of the initial valarray is:
   3.14159  radians, which is          180  degrees
   2.41886  radians, which is       138.59  degrees
    2.0944  radians, which is          120  degrees
   1.82348  radians, which is      104.478  degrees
    1.5708  radians, which is           90  degrees
   1.31812  radians, which is      75.5225  degrees
    1.0472  radians, which is           60  degrees
  0.722734  radians, which is      41.4096  degrees
         0  radians, which is            0  degrees
```

## <a name="asin"></a> asin

入力 valarray の要素を演算し、入力 valarray の要素のアークサインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> asin(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のアークサインと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

返される要素の単位はラジアンです。

戻り値は、プリンシパル間の値 + pi/2 から π/2 サインで一貫性のある値の入力。

### <a name="example"></a>例

```cpp
// valarray_asin.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  0.25 * i - 1;
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:";
   for (i = 0 ; i < 9 ; i++ )
      cout << " " << va1 [ i ];
   cout << endl;

   va2 = asin ( va1 );
   cout << "The arcsine of the initial valarray is:\n";
   for (i = 0 ; i < 9 ; i++ )
      cout << setw(10) << va2 [ i ]
           << "  radians, which is  "
           << setw(11) << (180/pi) * va2 [ i ]
           << "  degrees" << endl;
}
```

```Output
The initial valarray is: -1 -0.75 -0.5 -0.25 0 0.25 0.5 0.75 1
The arcsine of the initial valarray is:
   -1.5708  radians, which is          -90  degrees
 -0.848062  radians, which is     -48.5904  degrees
 -0.523599  radians, which is          -30  degrees
  -0.25268  radians, which is     -14.4775  degrees
         0  radians, which is            0  degrees
   0.25268  radians, which is      14.4775  degrees
  0.523599  radians, which is           30  degrees
  0.848062  radians, which is      48.5904  degrees
    1.5708  radians, which is           90  degrees
```

## <a name="atan"></a> atan

入力 valarray の要素を演算し、入力 valarray の要素のアークタンジェントの主値と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> atan(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のアークタンジェントと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

返される要素の単位はラジアンです。

戻り値は、プリンシパル間の値 + pi/2 から π/2 のタンジェントと整合性がある値の入力。

### <a name="example"></a>例

```cpp
// valarray_atan.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   va1 [ 0 ] = -100;
   for ( i = 1 ; i < 8 ; i++ )
      va1 [ i ] =  5 * ( 0.25 * i - 1 );
   va1 [ 8 ] = 100;
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is: ";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va1 [ i ] << " ";
   cout << "." << endl;

   va2 = atan ( va1 );
   cout << "The arcsine of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << setw(10) << va2 [ i ]
           << "  radians, which is  "
           << setw(11) << (180/pi) * va2 [ i ]
           << "  degrees" << endl;
   cout << endl;
}
```

```Output
The initial valarray is: -100 -3.75 -2.5 -1.25 0 1.25 2.5 3.75 100 .
The arcsine of the initial valarray is:
   -1.5608  radians, which is     -89.4271  degrees
  -1.31019  radians, which is     -75.0686  degrees
  -1.19029  radians, which is     -68.1986  degrees
 -0.896055  radians, which is     -51.3402  degrees
         0  radians, which is            0  degrees
  0.896055  radians, which is      51.3402  degrees
   1.19029  radians, which is      68.1986  degrees
   1.31019  radians, which is      75.0686  degrees
    1.5608  radians, which is      89.4271  degrees
```

## <a name="atan2"></a> atan2

valarray の定数と要素の組み合わせによって指定されたデカルト成分のアークタンジェントと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> atan2(const valarray<Type>& left, const valarray<Type>& right);

template <class Type>
valarray<Type> atan2(const valarray<Type> left, const Type& right);

template <class Type>
valarray<Type> atan2(const Type& left, const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
定数の数値データ型、またはアークタンジェント引数の y 座標の値を提供する要素から成る入力 valarray。

*そうです*\
定数の数値データ型、またはアークタンジェント引数の x 座標の値を提供する要素から成る入力 valarray。

### <a name="return-value"></a>戻り値

要素 `I` が以下のアークタンジェントに等しい valarray。

- 最初のテンプレート関数の場合は、`left` [ *I* ] / *_Righ*t [ *I* ]。

- 2 番目のテンプレート関数の場合は、`left` [ *I* ] / `right`。

- 3 番目のテンプレート関数の場合は、`left` / `right` [ *I* ]。

### <a name="remarks"></a>Remarks

返される要素の単位はラジアンです。

この関数は、コンポーネントが標準のタンジェント関数によって失われることを指定する引数の符号に関する情報を保持し、作業領域のこの知識により、戻り値の間の一意の角度を割り当てられる + pi し、-π をします。

場合*左*と*右*さまざまな要素数が、結果は未定義です。

### <a name="example"></a>例

```cpp
// valarray_atan2.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1y ( 1 , 4 ), va1x ( 1 , 4 );
   va1x [ 1 ] = -1;
   va1x [ 2 ] = -1;
   va1y [ 2 ] = -1;
   va1y [ 3 ] = -1;
   valarray<double> va2 ( 4 );

   cout << "The initial valarray for the x coordinate is: ( ";
   for ( i = 0 ; i < 4 ; i++ )
      cout << va1x [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial valarray for the y coordinate is: ( ";
   for ( i = 0 ; i < 4 ; i++ )
      cout << va1y [ i ] << " ";
   cout << ")." << endl;

   va2 = atan2 ( va1y , va1x );
   cout << "The atan2 ( y / x ) of the initial valarrays is:\n";
   for ( i = 0 ; i < 4 ; i++ )
      cout << setw( 10 ) << va2 [ i ]
           << "  radians, which is  "
           << setw( 11 ) << ( 180/pi ) * va2 [ i ]
           << "degrees" << endl;
   cout << endl;
}
```

```Output
The initial valarray for the x coordinate is: ( 1 -1 -1 1 ).
The initial valarray for the y coordinate is: ( 1 1 -1 -1 ).
The atan2 ( y / x ) of the initial valarrays is:
  0.785398  radians, which is           45degrees
   2.35619  radians, which is          135degrees
  -2.35619  radians, which is         -135degrees
 -0.785398  radians, which is          -45degrees
```

## <a name="begin"></a> 開始

```cpp
template <class T> unspecified 1 begin(valarray<T>& v);
template <class T> unspecified 2 begin(const valarray<T>& v);
```

## <a name="cos"></a> cos

入力 valarray の要素を演算し、入力 valarray の要素のコサインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> cos(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の絶対値と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_cos.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  ( pi ) * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << setw( 10 ) << va1 [ i ]
      << "  radians, which is  "
      << setw( 5 ) << ( 180/pi ) * va1 [ i ]
      << "  degrees" << endl;
   cout << endl;

   va2 = cos ( va1 );
   cout << "The cosine of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
  -3.14159  radians, which is   -180  degrees
  -2.35619  radians, which is   -135  degrees
   -1.5708  radians, which is    -90  degrees
 -0.785398  radians, which is    -45  degrees
         0  radians, which is      0  degrees
  0.785398  radians, which is     45  degrees
    1.5708  radians, which is     90  degrees
   2.35619  radians, which is    135  degrees
   3.14159  radians, which is    180  degrees

The cosine of the initial valarray is:
-1
-0.707107
-1.03412e-013
0.707107
1
0.707107
-1.03412e-013
-0.707107
-1
```

## <a name="cosh"></a> cosh

入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック コサインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> cosh(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のハイパーボリック コサインと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

指数関数によってハイパーボリック コサインを定義する恒等式:

cosh ( *z* ) = ( exp ( *z* ) + exp ( - *z* ) ) / 2

### <a name="example"></a>例

```cpp
// valarray_cosh.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  pi * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for (i = 0 ; i < 9 ; i++ )
      cout << setw( 10 ) << va1 [ i ]
      << "  radians, which is  "
      << setw( 5 ) << ( 180/pi ) * va1 [ i ]
      << "  degrees" << endl;
   cout << endl;

   va2 = cosh ( va1 );
   cout << "The hyperbolic cosine of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
  -3.14159  radians, which is   -180  degrees
  -2.35619  radians, which is   -135  degrees
   -1.5708  radians, which is    -90  degrees
 -0.785398  radians, which is    -45  degrees
         0  radians, which is      0  degrees
  0.785398  radians, which is     45  degrees
    1.5708  radians, which is     90  degrees
   2.35619  radians, which is    135  degrees
   3.14159  radians, which is    180  degrees

The hyperbolic cosine of the initial valarray is:
11.592
5.32275
2.50918
1.32461
1
1.32461
2.50918
5.32275
11.592
```

## <a name="end"></a> 終わり

```cpp
template <class T> unspecified 1 end(valarray<T>& v);
template <class T> unspecified 2 end(const valarray<T>& v);
```

## <a name="exp"></a> exp 関数

入力 valarray の要素を演算し、入力 valarray の要素の自然指数と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> exp(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の自然指数と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_exp.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  10 * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "Initial valarray:";
   for ( i = 0 ; i < 9 ; i++ )
      cout << " " << va1 [ i ];
   cout << endl;

   va2 = exp ( va1 );
   cout << "The natural exponential of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
Initial valarray: -10 -7.5 -5 -2.5 0 2.5 5 7.5 10
The natural exponential of the initial valarray is:
4.53999e-005
0.000553084
0.00673795
0.082085
1
12.1825
148.413
1808.04
22026.5
```

## <a name="log"></a> ログ

入力 valarray の要素を演算し、入力 valarray の要素の自然対数と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> log(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の絶対値と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_log.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   int i;

   valarray<double> va1 ( 9 );
   for (i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  10 * i;
   valarray<double> va2 ( 9 );

   cout << "Initial valarray:";
   for ( i = 0 ; i < 9 ; i++ )
      cout << " " << va1 [ i ];
   cout << endl;

   va2 = log ( va1 );
   cout << "The natural logarithm of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
Initial valarray: 0 10 20 30 40 50 60 70 80
The natural logarithm of the initial valarray is:
-inf
2.30259
2.99573
3.4012
3.68888
3.91202
4.09434
4.2485
4.38203
```

## <a name="log10"></a> log10

入力 valarray の要素を演算し、入力 valarray の要素の常用対数 (底が 10 の対数) と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> log10(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の常用対数と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_log10.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   int i;

   valarray<double> va1 ( 11 );
   for ( i = 0 ; i < 11 ; i++ )
      va1 [ i ] =  10 * i;
   valarray<double> va2 ( 9 );

   cout << "Initial valarray:";
   for (i = 0 ; i < 11 ; i++ )
      cout << " " << va1 [ i ];
   cout << endl;

   va2 = log10 ( va1 );
   cout << "The common logarithm of the initial valarray is:\n";
   for (i = 0 ; i < 11 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
Initial valarray: 0 10 20 30 40 50 60 70 80 90 100
The common logarithm of the initial valarray is:
-inf
1
1.30103
1.47712
1.60206
1.69897
1.77815
1.8451
1.90309
1.95424
2
```

## <a name="pow"></a> えい

入力 valarray と定数の要素を演算し、入力 valarray の要素によって指定されている底と等しい要素を持つ valarray か、入力 valarray か定数の要素で指定された値だけ定数を指数乗したものと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type>
pow(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
pow(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
pow(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
各要素を累乗する底を指定する要素から成る入力 valarray。

*そうです*\
各要素を累乗する指数を指定する要素から成る入力 valarray。

### <a name="return-value"></a>戻り値

要素 `I` が以下に等しい valarray。

- 最初のテンプレート関数の場合、`left` [ *I* ] の `right` [ *I* ] 乗。

- 2 番目のテンプレート関数の場合、`left` [ *I* ] の `right` 乗。

- 3 番目のテンプレート関数の場合、`left` の `right` [ *I* ] 乗。

### <a name="remarks"></a>Remarks

場合*左*と*右*さまざまな要素数が、結果は未定義です。

### <a name="example"></a>例

```cpp
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> vabase ( 6 );
   for ( i = 0 ; i < 6 ; i++ )
      vabase [ i ] =  i/2;
   valarray<double> vaexp ( 6 );
   for ( i = 0 ; i < 6 ; i++ )
      vaexp [ i ] =  2 * i;

   valarray<double> va2 ( 6 );

   cout << "The initial valarray for the base is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vabase [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial valarray for the exponent is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaexp[ i ] << " ";
   cout << ")." << endl;

   va2 = pow ( vabase , vaexp );
   cout << "The power of (n/2) * exp (2n) for n = 0 to n = 5 is: \n";
      for ( i = 0 ; i < 6 ; i++ )
         cout <<  "n = " << i << "\tgives " << va2 [ i ] << endl;
}
```

```Output
The initial valarray for the base is: ( 0 0 1 1 2 2 ).
The initial valarray for the exponent is: ( 0 2 4 6 8 10 ).
The power of (n/2) * exp (2n) for n = 0 to n = 5 is:
n = 0   gives 1
n = 1   gives 0
n = 2   gives 1
n = 3   gives 1
n = 4   gives 256
n = 5   gives 1024
```

## <a name="sin"></a> sin 関数

入力 valarray の要素を演算し、入力 valarray の要素のサインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> sin(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のサインと等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_sin.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  pi * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << setw(10) << va1 [ i ]
      << "   radians, which is   "
      << setw(5) << ( 180/pi ) * va1 [ i ]
      << "   degrees" << endl;
   cout << endl;

   va2 = sin ( va1 );
   cout << "The sine of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
  -3.14159   radians, which is    -180   degrees
  -2.35619   radians, which is    -135   degrees
   -1.5708   radians, which is     -90   degrees
 -0.785398   radians, which is     -45   degrees
         0   radians, which is       0   degrees
  0.785398   radians, which is      45   degrees
    1.5708   radians, which is      90   degrees
   2.35619   radians, which is     135   degrees
   3.14159   radians, which is     180   degrees

The sine of the initial valarray is:
2.06823e-013
-0.707107
-1
-0.707107
0
0.707107
1
0.707107
-2.06823e-013
```

## <a name="sinh"></a> sinh

入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック サインと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> sinh(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のハイパーボリック サインと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

指数関数によってハイパーボリック サインを定義する恒等式:

sinh ( *z* ) = ( exp ( *z* ) - exp ( - *z* ) ) / 2

### <a name="example"></a>例

```cpp
// valarray_sinh.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for (i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  pi * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for (i = 0 ; i < 9 ; i++ )
      cout << setw( 10 ) << va1 [ i ]
      << "   radians, which is   "
      << setw( 5 ) << ( 180/pi ) * va1 [ i ]
      << "  degrees" << endl;
   cout << endl;

   va2 = sinh ( va1 );
   cout << "The hyperbolic sine of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
  -3.14159   radians, which is    -180  degrees
  -2.35619   radians, which is    -135  degrees
   -1.5708   radians, which is     -90  degrees
 -0.785398   radians, which is     -45  degrees
         0   radians, which is       0  degrees
  0.785398   radians, which is      45  degrees
    1.5708   radians, which is      90  degrees
   2.35619   radians, which is     135  degrees
   3.14159   radians, which is     180  degrees

The hyperbolic sine of the initial valarray is:
-11.5487
-5.22797
-2.3013
-0.868671
0
0.868671
2.3013
5.22797
11.5487
```

## <a name="sqrt"></a> sqrt

入力 valarray の要素を演算し、入力 valarray の要素の平方根と等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> sqrt(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素の平方根と等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_sqrt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <cmath>

int main( )
{
   using namespace std;
   int i;

   valarray<double> va1 ( 6 );
   for ( i = 0 ; i < 5 ; i++ )
      va1 [ i ] = i * i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   valarray<double> va2 = sqrt ( va1 );
   cout << "The square root of the initial valarray is: ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 0 1 4 9 16 ).
The square root of the initial valarray is: ( 0 1 2 3 4 ).
```

## <a name="swap"></a> スワップ

2 つの valarray の要素を交換します。

```cpp
template <class Type>
void swap(
    valarray<Type>& left,
    valarray<Type>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`valarray` 型のオブジェクト。

*そうです*\
`valarray` 型のオブジェクト。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`left.swap(right)` を実行します。

## <a name="tan"></a> tan

入力 valarray の要素を演算し、入力 valarray の要素のタンジェントと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> tan(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のタンジェントと等しい要素を持つ valarray。

### <a name="example"></a>例

```cpp
// valarray_tan.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  ( pi/2 ) * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << setw( 10 ) << va1 [ i ]
      << "     radians, which is   "
      << setw( 5 ) << ( 180/pi ) * va1 [ i ]
      << "   degrees" << endl;
   cout << endl;

   va2 = tan ( va1 );
   cout << "The tangent of the initial valarray is:\n ";
   for ( i = 0 ; i < 9 ; i++ )
      cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
   -1.5708     radians, which is     -90   degrees
   -1.1781     radians, which is   -67.5   degrees
 -0.785398     radians, which is     -45   degrees
 -0.392699     radians, which is   -22.5   degrees
         0     radians, which is       0   degrees
  0.392699     radians, which is    22.5   degrees
  0.785398     radians, which is      45   degrees
    1.1781     radians, which is    67.5   degrees
    1.5708     radians, which is      90   degrees

The tangent of the initial valarray is:
 9.6701e+012
-2.41421
-1
-0.414214
0
0.414214
1
2.41421
-9.6701e+012
```

## <a name="tanh"></a> tanh

入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック タンジェントと等しい要素を持つ valarray を返します。

```cpp
template <class Type>
valarray<Type> tanh(const valarray<Type>& left);
```

### <a name="parameters"></a>パラメーター

*左*\
要素がこのメンバー関数の演算の対象となる入力 valarray。

### <a name="return-value"></a>戻り値

入力 valarray の要素のハイパーボリック コサインと等しい要素を持つ valarray。

### <a name="remarks"></a>Remarks

指数関数によってハイパーボリック タンジェントを定義する恒等式:

tanh ( *z* ) = sinh ( *z* ) / cosh ( *z* ) = ( exp ( *z* ) - exp ( - *z* ) ) / ( exp ( *z* ) + exp ( - *z* ) )

### <a name="example"></a>例

```cpp
// valarray_tanh.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>
#include <iomanip>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;
   int i;

   valarray<double> va1 ( 9 );
   for ( i = 0 ; i < 9 ; i++ )
      va1 [ i ] =  pi * ( 0.25 * i - 1 );
   valarray<double> va2 ( 9 );

   cout << "The initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
      cout << setw( 10 ) << va1 [ i ]
      << "   radians, which is     "
                    << setw( 5 ) << ( 180/pi ) * va1 [ i ]
                    << "  degrees" << endl;
   cout << endl;

   va2 = tanh ( va1 );
   cout << "The hyperbolic tangent of the initial valarray is:\n";
   for ( i = 0 ; i < 9 ; i++ )
     cout << va2 [ i ] << endl;
}
```

```Output
The initial valarray is:
  -3.14159   radians, which is      -180  degrees
  -2.35619   radians, which is      -135  degrees
   -1.5708   radians, which is       -90  degrees
 -0.785398   radians, which is       -45  degrees
         0   radians, which is         0  degrees
  0.785398   radians, which is        45  degrees
    1.5708   radians, which is        90  degrees
   2.35619   radians, which is       135  degrees
   3.14159   radians, which is       180  degrees

The hyperbolic tangent of the initial valarray is:
-0.996272
-0.982193
-0.917152
-0.655794
0
0.655794
0.917152
0.982193
0.996272
```
