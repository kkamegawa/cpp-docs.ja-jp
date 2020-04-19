---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 8955669f4bc6fd7b3b373751e0e5134205dd1657
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689791"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

順序付けされたオブジェクトのペア ( **double**型) を格納するオブジェクトについて説明します。最初のオブジェクトは複素数の実数部、2番目のオブジェクトは虚数部を表します。

## <a name="syntax"></a>構文

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>パラメーター

*Realval* \
構築される複素数の実数部の **double** 型の値。

*Imagval* \
構築される複素数の虚数部の **double** 型の値。

*Complexnum* \
**Float**型または**long double**型の複素数。この実数部と虚数部は、構築される**double**型の複素数を初期化するために使用されます。

## <a name="return-value"></a>戻り値

**double** 型の複素数。

## <a name="remarks"></a>Remarks

クラステンプレート complex を**double**型の複合クラスに明示的に特殊化することは、クラステンプレートが定義するコンストラクターでのみクラステンプレートとは異なります。 **Float**から**double**への変換は暗黙的に行うことができますが、 **long double**から**double**への変換は**明示的**にする必要があります。 **explicit** を使用すると、割り当て構文を使用した型変換による開始は禁止されます。

クラステンプレート `complex` の詳細については、「[複合クラス](../standard-library/complex-class.md)」を参照してください。 クラステンプレート `complex` のメンバーの一覧については、「」を参照してください。

## <a name="example"></a>例

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>［要件］

**ヘッダー**: \<complex>

**名前空間:** std

## <a name="see-also"></a>関連項目

[complex クラス](../standard-library/complex-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
