---
title: complex クラス
ms.date: 03/27/2019
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
ms.openlocfilehash: 0c72726bfb92965a2152830d7ce77ae13f763d35
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257976"
---
# <a name="complex-class"></a>complex クラス

クラステンプレートは、`Type`型の2つのオブジェクトを格納するオブジェクトを記述します。1つは複素数の実数部、もう1つは虚数部を表すオブジェクトです。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>コメント

クラス `Type`のオブジェクト。

- 従来の動作で、パブリックな既定のコンストラクター、デストラクター、コピー コンストラクター、および代入演算子が用意されています。

- 整数または浮動小数点値を代入することも、従来の動作でこのような値に型キャストすることもできます。

- 従来の動作で、必要に応じて浮動小数点型に対して定義される算術演算子と数学関数を定義します。

特に、コピーによる構築と、代入に先行する既定の構築の間に、微妙な違いはありません。 `Type` クラスのオブジェクトに対する操作では、例外をスローすることはできません。

クラステンプレート complex の明示的な特殊化は、3つの浮動小数点型に存在します。 この実装では、`Type` の他の型の値は、実際の計算では**double**になり、`Type`型の格納されたオブジェクトに**double**型の結果が割り当てられます。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[complex](#complex)|指定された実数部または虚数部を使用して、または他の複素数のコピーとして複素数を構築します。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|複素数の実数部と虚数部を表すために使用するデータ型を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[imag](#imag)|複素数の虚数部を抽出します。|
|[real](#real)|複素数の実数部を抽出します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator*=](#op_star_eq)|ターゲットの複素数を係数で乗算します。係数は複素数、または複素数の実数部および虚数部と同じ型である場合があります。|
|[operator+=](#op_add_eq)|ターゲットの複素数に数値を加算します。加算される数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。|
|[operator-=](#operator-_eq)|ターゲットの複素数から数値を減算します。減算される数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。|
|[operator/=](#op_div_eq)|ターゲットの複素数を除数で除算します。除数は複素数、または複素数の実数部および虚数部と同じ型である場合があります。|
|[operator=](#op_eq)|ターゲットの複素数に数値を割り当てます。割り当てられる数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。|

## <a name="complex"></a>作業

指定された実数部または虚数部を使用して、または他の複素数のコピーとして複素数を構築します。

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>パラメーター

*_RealVal*\
構築される複素数の初期化に使用される実数部の値。

*_ImagVal*\
構築される複素数の初期化に使用される虚数部の値。

*Complexnum*\
構築される複素数の初期化に、その実数部と虚数部の値が使用される複素数。

### <a name="remarks"></a>コメント

最初のコンストラクターは、格納されている実数部を *\_RealVal*に、格納された虚数部を *\_imagval*に初期化します。 2番目のコンストラクターは、格納されている実数部を `complexNum.real()` に初期化し、格納されている虚数部を `complexNum.imag()`に初期化します。

この実装では、トランスレーターがメンバー テンプレート関数をサポートしない場合、次のテンプレートは、

```cpp
template <class Other>
complex(const complex<Other>& right);
```

コピー コンストラクターである

```cpp
complex(const complex& right);
```

に置き換えられます。

### <a name="example"></a>例

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of another complex number
    complex<double> c2( c1 );
    cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

    // Complex numbers can be initialized in polar form
    // but will be stored in Cartesian form
    complex<double> c3( polar( sqrt( (double)8 ) , pi / 4 ) );
    cout << "c3 = polar( sqrt( 8 ) , pi / 4 ) = " << c3 << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3 );
    double argc3 = arg( c3 );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>imag

複素数の虚数部を抽出します。

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>パラメーター

*右*\
虚数部が抽出される複素数。

### <a name="return-value"></a>戻り値

複素数の虚数部。

### <a name="remarks"></a>コメント

複素数*a + bi*の場合、虚数部またはコンポーネントは*Im (a + bi) = b*です。

### <a name="example"></a>例

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;

    complex<double> c1( 4.0 , 3.0 );
    cout << "The complex number c1 = " << c1 << endl;

    double dr1 = c1.real();
    cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

    double di1 = c1.imag();
    cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="op_star_eq"></a>operator * =

ターゲットの複素数を係数で乗算します。係数は複素数、または複素数の実数部および虚数部と同じ型である場合があります。

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
複素数、またはターゲットの複素数のパラメーターと同じ型の数値。

### <a name="return-value"></a>戻り値

パラメーターとして指定された数値で乗算された複素数。

### <a name="remarks"></a>コメント

データを特定の形式に変換せずに単純な算術演算を実行できるようにするために、演算はオーバーロードされます。

### <a name="example"></a>例

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main()
{
    using namespace std;
    double pi = 3.14159265359;

    // Example of the first member function
    // type complex<double> multiplied by type complex<double>
    complex<double> cl1( polar ( 3.0 , pi / 6 ) );
    complex<double> cr1( polar ( 2.0 , pi / 3 ) );
    cout << "The left-side complex number is cl1 = " << cl1 << endl;
    cout << "The right-side complex number is cr1 = " << cr1 << endl;

    complex<double> cs1 = cl1 * cr1;
    cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

    // This is equivalent to the following operation
    cl1 *= cr1;
    cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

    double abscl1 = abs ( cl1 );
    double argcl1 = arg ( cl1 );
    cout << "The modulus of cl1 is: " << abscl1 << endl;
    cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

    // Example of the second member function
    // type complex<double> multiplied by type double
    complex<double> cl2 ( polar ( 3.0 , pi / 6 ) );
    double cr2 = 5.0;
    cout << "The left-side complex number is cl2 = " << cl2 << endl;
    cout << "The right-side complex number is cr2 = " << cr2 << endl;

    complex<double> cs2 = cl2 * cr2;
    cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

    // This is equivalent to the following operation
    cl2 *= cr2;
    cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

    double abscl2 = abs ( cl2 );
    double argcl2 = arg ( cl2 );
    cout << "The modulus of cl2 is: " << abscl2 << endl;
    cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="op_add_eq"></a>演算子 + =

ターゲットの複素数に数値を加算します。加算される数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
複素数、またはターゲットの複素数のパラメーターと同じ型の数値。

### <a name="return-value"></a>戻り値

パラメーターとして指定された数値が加算された複素数。

### <a name="remarks"></a>コメント

データを特定の形式に変換せずに単純な算術演算を実行できるようにするために、演算はオーバーロードされます。

### <a name="example"></a>例

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="operator-_eq"></a>operator-=

ターゲットの複素数から数値を減算します。減算される数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>パラメーター

*Complexnum*\
ターゲットの複素数を除算する複素数。

*_RealPart*\
ターゲットの複素数を除算する実数。

### <a name="return-value"></a>戻り値

パラメーターとして指定された数値が減算された複素数。

### <a name="remarks"></a>コメント

データを特定の形式に変換せずに単純な算術演算を実行できるようにするために、演算はオーバーロードされます。

### <a name="example"></a>例

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex<double> cl2( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="op_div_eq"></a>operator/=

ターゲットの複素数を除数で除算します。除数は複素数、または複素数の実数部および虚数部と同じ型である場合があります。

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>パラメーター

*Complexnum*\
ターゲットの複素数を除算する複素数。

*_RealPart*\
ターゲットの複素数を除算する実数。

### <a name="return-value"></a>戻り値

パラメーターとして指定された数値で除算された複素数。

### <a name="remarks"></a>コメント

データを特定の形式に変換せずに単純な算術演算を実行できるようにするために、演算はオーバーロードされます。

### <a name="example"></a>例

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex<double> cl1( polar (3.0 , pi / 6 ) );
   complex<double> cr1( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex<double> cl2( polar(3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="op_eq"></a>operator =

ターゲットの複素数に数値を割り当てます。割り当てられる数値は複素数、またはターゲットの複素数の実数部および虚数部と同じ型である場合があります。

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>パラメーター

*右*\
複素数、またはターゲットの複素数のパラメーターと同じ型の数値。

### <a name="return-value"></a>戻り値

パラメーターとして指定された数値が割り当てられた複素数。

### <a name="remarks"></a>コメント

データを特定の形式に変換せずに単純な算術演算を実行できるようにするために、演算はオーバーロードされます。

### <a name="example"></a>例

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a>本当の

複素数の実数部を取得または設定します。

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>パラメーター

*右*\
実数値が抽出される複素数。

### <a name="return-value"></a>戻り値

複素数の実数部。

### <a name="remarks"></a>コメント

複素数*a + bi*の場合、実数部またはコンポーネントは*Re (a + bi) = a*です。

### <a name="example"></a>例

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex<double> c1( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real();
   cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

   double di1 = c1.imag();
   cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="value_type"></a>value_type

複素数の実数部と虚数部を表すために使用するデータ型を表す型。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>コメント

`value_type` は、class complex `Type` template パラメーターのシノニムです。

### <a name="example"></a>例

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    complex<double>::value_type a = 3, b = 4;

    complex<double> c1 ( a , b );
    cout << "Specifying initial real & imaginary parts"
        << "\nof type value_type: "
        << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>参照

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
