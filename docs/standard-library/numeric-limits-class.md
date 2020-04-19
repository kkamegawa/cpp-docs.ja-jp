---
title: numeric_limits クラス
ms.date: 11/04/2016
f1_keywords:
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
helpviewer_keywords:
- std::numeric_limits [C++]
- std::numeric_limits [C++], denorm_min
- std::numeric_limits [C++], digits
- std::numeric_limits [C++], digits10
- std::numeric_limits [C++], epsilon
- std::numeric_limits [C++], has_denorm
- std::numeric_limits [C++], has_denorm_loss
- std::numeric_limits [C++], has_infinity
- std::numeric_limits [C++], has_quiet_NaN
- std::numeric_limits [C++], has_signaling_NaN
- std::numeric_limits [C++], infinity
- std::numeric_limits [C++], is_bounded
- std::numeric_limits [C++], is_exact
- std::numeric_limits [C++], is_iec559
- std::numeric_limits [C++], is_integer
- std::numeric_limits [C++], is_modulo
- std::numeric_limits [C++], is_signed
- std::numeric_limits [C++], is_specialized
- std::numeric_limits [C++], lowest
- std::numeric_limits [C++], max
- std::numeric_limits [C++], max_digits10
- std::numeric_limits [C++], max_exponent
- std::numeric_limits [C++], max_exponent10
- std::numeric_limits [C++], min
- std::numeric_limits [C++], min_exponent
- std::numeric_limits [C++], min_exponent10
- std::numeric_limits [C++], quiet_NaN
- std::numeric_limits [C++], radix
- std::numeric_limits [C++], round_error
- std::numeric_limits [C++], round_style
- std::numeric_limits [C++], signaling_NaN
- std::numeric_limits [C++], tinyness_before
- std::numeric_limits [C++], traps
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
ms.openlocfilehash: 5373bd6a99605f5a63fb6aa2ed6de50c12b1c8f1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876031"
---
# <a name="numeric_limits-class"></a>numeric_limits クラス

クラステンプレートでは、組み込みの数値型の算術プロパティについて説明します。

## <a name="syntax"></a>構文

```cpp
template <class Type>
    class numeric_limits
```

### <a name="parameters"></a>パラメーター

*[種類]* \
プロパティがテスト、照会、設定対象になる基本的な要素のデータ型。 *型*は、 **const**、 **volatile**、または**const volatile**として宣言することもできます。

## <a name="remarks"></a>解説

ヘッダーは、型**wchar_t**、 **bool**、 **char**、 **signed char**、 **unsigned char**、 **short**、 **unsigned short**、 **int**、 **unsigned int** **、long、** **unsigned long**、 **float**、 **double**、 **long double**、 **long long**、 **unsigned long long**、 **char16_t**、および**char32_t**の型の明示的な特殊化を定義します。 これらの明示的な特殊化では、メンバー [numeric_limits:: is_specialized](#is_specialized)は**true**で、関連するすべてのメンバーには意味のある値があります。 プログラムによって、その他の明示的な特殊化を行えます。 クラスのほとんどのメンバー関数は、 **float**の実装の可能性を記述またはテストします。

任意の特殊化の場合、メンバーに有効な値が含まれません。 意味のある値を持たないメンバーオブジェクトは 0 (または**false**) を格納し、意味のある値を返さないメンバー関数は `Type(0)`を返します。

## <a name="static-functions-and-constants"></a>静的な関数と定数

|||
|-|-|
|[denorm_min](#denorm_min)|0 以外の最小の非正規化値を返します。|
|[数字](#digits)|型が精度を失うことなく表現できる基数桁数を返します。|
|[digits10](#digits10)|型が精度を失うことなく表現できる小数点数桁数を返します。|
|[epsilon](#epsilon)|1 と、データ型が表すことのできる 1 より大きい最小値との差を返します。|
|[has_denorm](#has_denorm)|型が非正規化値を許可するかどうかをテストします。|
|[has_denorm_loss](#has_denorm_loss)|精度の損失が、不正確な結果ではなく、非正規化の損失として検出されるかどうかをテストします。|
|[has_infinity](#has_infinity)|型が正の無限大を表すことができるかどうかをテストします。|
|[has_quiet_NaN](#has_quiet_nan)|型が非シグナル化である非表示の非数 (NAN) の表現を持っているかどうかをテストします。|
|[has_signaling_NaN](#has_signaling_nan)|型がシグナルを発生する非数 (NAN) を表せるかどうかをテストします。|
|[infinity](#infinity)|型の正の無限大の表現 (使用可能な場合)。|
|[is_bounded](#is_bounded)|型が表すことができる値のセットが有限かどうかをテストします。|
|[is_exact](#is_exact)|型で実行される計算に丸め誤差がないかどうかをテストします。|
|[is_iec559](#is_iec559)|型が IEC 559 標準に準拠しているかどうかをテストします。|
|[is_integer](#is_integer)|型が整数を表せるかどうかをテストします。|
|[is_modulo](#is_modulo)|型が剰余を表せるかどうかをテストします。|
|[is_signed](#is_signed)|型が符号付きを表せるかどうかをテストします。|
|[is_specialized](#is_specialized)|クラステンプレート `numeric_limits`で型に明示的な特殊化が定義されているかどうかをテストします。|
|[lowest](#lowest)|負の最小有限値を返します。|
|[max](#max)|型の最大の有限値を返します。|
|[max_digits10](#max_digits10)|その型の 2 つの値が別個の異なる 10 進表現であることを確証するために必要な 10 進桁数を返します。|
|[max_exponent](#max_exponent)|基数を累乗した場合に、浮動小数点型が有限値として表すことができる正の整数の最大指数を返します。|
|[max_exponent10](#max_exponent10)|10 の基数を累乗した場合に、浮動小数点型が有限値として表すことができる正の整数の最大指数を返します。|
|[min](#min)|型の最小の正規化値を返します。|
|[min_exponent](#min_exponent)|基数の底を累乗した場合に、浮動小数点型が有限値として表すことができる負の整数の最大指数を返します。|
|[min_exponent10](#min_exponent10)|10 の基数を累乗した場合に、浮動小数点型が有限値として表すことができる負の整数の最大指数を返します。|
|[quiet_NaN](#quiet_nan)|型の静かな非数表現 (NAN) を返します。|
|[radix](#radix)|型の表現に使用される、基数と呼ばれる整数の底を返します。|
|[round_error](#round_error)|型の丸め誤差の最大値を返します。|
|[round_style](#round_style)|実装において、浮動小数点値を整数値に丸め処理を行うために選択可能なさまざまな方式を記述した値を返します。|
|[signaling_NaN](#signaling_nan)|型のシグナリング非数 (NAN) の表現を返します。|
|[tinyness_before](#tinyness_before)|型が、値を丸める前に正規化された値として表現するには小さすぎることを確認できるかどうかをテストします。|
|[traps](#traps)|型において算術例外に関するレポートをトラップするように実装されているかどうかをテストします。|

### <a name="denorm_min"></a>denorm_min

0 以外の最小の非正規化値を返します。

```cpp
static constexpr Type denorm_min() throw();
```

#### <a name="return-value"></a>戻り値

0 以外の最小の非正規化値。

#### <a name="remarks"></a>解説

**long double**は、 C++コンパイラの**double**と同じです。

関数は、型の最小値を返します。これは、 [has_denorm](#has_denorm)が `denorm_present`と等しくない場合の[最小](#min)値と同じです。

#### <a name="example"></a>例

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value" << endl
        << "for float objects is: "
        << numeric_limits<float>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for double objects is: "
        << numeric_limits<double>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::denorm_min( ) << endl;

   // A smaller value will round to zero
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;
}
```

```Output
The smallest nonzero denormalized value
for float objects is: 1.4013e-045
The smallest nonzero denormalized value
for double objects is: 4.94066e-324
The smallest nonzero denormalized value
for long double objects is: 4.94066e-324
0
0
0
```

### <a name="digits"></a>続く

型が精度を失うことなく表現できる基数桁数を返します。

```cpp
static constexpr int digits = 0;
```

#### <a name="return-value"></a>戻り値

型が精度を失うことなく表現できる基数桁数。

#### <a name="remarks"></a>解説

メンバーは、型が変更なしで表すことができる基数桁数を格納します。これは、定義済みの整数型の任意の符号ビット以外のビット数、または定義済みの浮動小数点型の仮数部桁数になります。

#### <a name="example"></a>例

```cpp
// numeric_limits_digits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits <<endl;
   cout << numeric_limits<double>::digits <<endl;
   cout << numeric_limits<long double>::digits <<endl;
   cout << numeric_limits<int>::digits <<endl;
   cout << numeric_limits<__int64>::digits <<endl;
}
```

```Output
24
53
53
31
63
```

### <a name="digits10"></a>digits10

型が精度を失うことなく表現できる小数点数桁数を返します。

```cpp
static constexpr int digits10 = 0;
```

#### <a name="return-value"></a>戻り値

型が精度を失うことなく表現できる小数点数桁数。

#### <a name="example"></a>例

```cpp
// numeric_limits_digits10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits10 <<endl;
   cout << numeric_limits<double>::digits10 <<endl;
   cout << numeric_limits<long double>::digits10 <<endl;
   cout << numeric_limits<int>::digits10 <<endl;
   cout << numeric_limits<__int64>::digits10 <<endl;
   float f = (float)99999999;
   cout.precision ( 10 );
   cout << "The float is; " << f << endl;
}
```

```Output
6
15
15
9
18
The float is; 100000000
```

### <a name="epsilon"></a>epsilon

関数は、1 と、データ型が表現可能な 1 より大きい最小値との間の差を返します。

```cpp
static constexpr Type epsilon() throw();
```

#### <a name="return-value"></a>戻り値

1 と、データ型が表現可能な 1 より大きい最小値との間の差。

#### <a name="remarks"></a>解説

値は、**float** 型の場合は FLT_EPSILON です。 型の `epsilon` は、*N* + `epsilon`N +  が表現可能になるように、正の浮動小数点数 *N* の最小値になります。

#### <a name="example"></a>例

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for float objects is: "
        << numeric_limits<float>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for double objects is: "
        << numeric_limits<double>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::epsilon( ) << endl;
}
```

```Output
The difference between 1 and the smallest value greater than 1
for float objects is: 1.19209e-007
The difference between 1 and the smallest value greater than 1
for double objects is: 2.22045e-016
The difference between 1 and the smallest value greater than 1
for long double objects is: 2.22045e-016
```

### <a name="has_denorm"></a>has_denorm

型が非正規化値を許可するかどうかをテストします。

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

#### <a name="return-value"></a>戻り値

**const**`float_denorm_style` 型の列挙値で、型が非正規化値を許可するかどうかを示します。

#### <a name="remarks"></a>解説

メンバーは、正規化されていない値を持つ浮動小数点型の `denorm_present` を格納します。指数部は実質的に可変数です。

#### <a name="example"></a>例

```cpp
// numeric_limits_has_denorm.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects allow denormalized values: "
        << numeric_limits<float>::has_denorm
        << endl;
   cout << "Whether double objects allow denormalized values: "
        << numeric_limits<double>::has_denorm
        << endl;
   cout << "Whether long int objects allow denormalized values: "
        << numeric_limits<long int>::has_denorm
        << endl;
}
```

```Output
Whether float objects allow denormalized values: 1
Whether double objects allow denormalized values: 1
Whether long int objects allow denormalized values: 0
```

### <a name="has_denorm_loss"></a>has_denorm_loss

精度の損失が、不正確な結果ではなく、非正規化の損失として検出されるかどうかをテストします。

```cpp
static constexpr bool has_denorm_loss = false;
```

#### <a name="return-value"></a>戻り値

精度の損失が非正規化の損失として検出される場合は **true**、そうでない場合は **false**。

#### <a name="remarks"></a>解説

メンバーは、非正規化された結果となるか (正規化値として表現するには小さすぎる)、あるいは不正確である (指数の範囲と精度の制約を受けない結果とは異なる) ため、値の精度が損失されたかどうかを判別する型の場合は true を格納します。これは、一部の結果に影響を与える可能性がある、IEC 559 浮動小数点表現でのオプションです。

#### <a name="example"></a>例

```cpp
// numeric_limits_has_denorm_loss.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects can detect denormalized loss: "
        << numeric_limits<float>::has_denorm_loss
        << endl;
   cout << "Whether double objects can detect denormalized loss: "
        << numeric_limits<double>::has_denorm_loss
        << endl;
   cout << "Whether long int objects can detect denormalized loss: "
        << numeric_limits<long int>::has_denorm_loss
        << endl;
}
```

```Output
Whether float objects can detect denormalized loss: 1
Whether double objects can detect denormalized loss: 1
Whether long int objects can detect denormalized loss: 0
```

### <a name="has_infinity"></a>has_infinity

型が正の無限大を表すことができるかどうかをテストします。

```cpp
static constexpr bool has_infinity = false;
```

#### <a name="return-value"></a>戻り値

型が正の無限大を表すことができる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

メンバーは、**is_iec559** が [true](#is_iec559) の場合は **true** を返します。

#### <a name="example"></a>例

```cpp
// numeric_limits_has_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have infinity: "
        << numeric_limits<float>::has_infinity
        << endl;
   cout << "Whether double objects have infinity: "
        << numeric_limits<double>::has_infinity
        << endl;
   cout << "Whether long int objects have infinity: "
        << numeric_limits<long int>::has_infinity
        << endl;
}
```

```Output
Whether float objects have infinity: 1
Whether double objects have infinity: 1
Whether long int objects have infinity: 0
```

### <a name="has_quiet_nan"></a>has_quiet_NaN

型が静かな (シグナルを発生させない) 非数 (NaN) を表せるかどうかをテストします。

```cpp
static constexpr bool has_quiet_NaN = false;
```

#### <a name="return-value"></a>戻り値

**type** が静かな NaN を表せる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

静かな NaN は、式でのその存在についてのシグナルを発生させない非数のエンコードです。 戻り値は、**is_iec559** が true の場合は [true](#is_iec559) です。

#### <a name="example"></a>例

```cpp
// numeric_limits_has_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have quiet_NaN: "
        << numeric_limits<float>::has_quiet_NaN
        << endl;
   cout << "Whether double objects have quiet_NaN: "
        << numeric_limits<double>::has_quiet_NaN
        << endl;
   cout << "Whether long int objects have quiet_NaN: "
        << numeric_limits<long int>::has_quiet_NaN
        << endl;
}
```

```Output
Whether float objects have quiet_NaN: 1
Whether double objects have quiet_NaN: 1
Whether long int objects have quiet_NaN: 0
```

### <a name="has_signaling_nan"></a>has_signaling_NaN

型がシグナルを発生する非数 (NAN) を表せるかどうかをテストします。

```cpp
static constexpr bool has_signaling_NaN = false;
```

#### <a name="return-value"></a>戻り値

型がシグナルを発生する NAN を表せる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

シグナルを発生する NaN は、式でのその存在についてのシグナルを発生させる非数のエンコードです。 戻り値は、**is_iec559** が true の場合は [true](#is_iec559) です。

#### <a name="example"></a>例

```cpp
// numeric_limits_has_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signaling_NaN: "
        << numeric_limits<float>::has_signaling_NaN
        << endl;
   cout << "Whether double objects have a signaling_NaN: "
        << numeric_limits<double>::has_signaling_NaN
        << endl;
   cout << "Whether long int objects have a signaling_NaN: "
        << numeric_limits<long int>::has_signaling_NaN
        << endl;
}
```

```Output
Whether float objects have a signaling_NaN: 1
Whether double objects have a signaling_NaN: 1
Whether long int objects have a signaling_NaN: 0
```

### <a name="infinity"></a>~

型の正の無限大の表現 (使用可能な場合)。

```cpp
static constexpr Type infinity() throw();
```

#### <a name="return-value"></a>戻り値

型の正の無限大の表現 (使用可能な場合)。

#### <a name="remarks"></a>解説

[has_infinity](#has_infinity) が **true** である場合にのみ、戻り値に意味があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::has_infinity <<endl;
   cout << numeric_limits<double>::has_infinity<<endl;
   cout << numeric_limits<long double>::has_infinity <<endl;
   cout << numeric_limits<int>::has_infinity <<endl;
   cout << numeric_limits<__int64>::has_infinity <<endl;

   cout << "The representation of infinity for type float is: "
        << numeric_limits<float>::infinity( ) <<endl;
   cout << "The representation of infinity for type double is: "
        << numeric_limits<double>::infinity( ) <<endl;
   cout << "The representation of infinity for type long double is: "
        << numeric_limits<long double>::infinity( ) <<endl;
}
```

```Output
1
1
1
0
0
The representation of infinity for type float is: inf
The representation of infinity for type double is: inf
The representation of infinity for type long double is: inf
```

### <a name="is_bounded"></a>is_bounded

型が表すことができる値のセットが有限かどうかをテストします。

```cpp
static constexpr bool is_bounded = false;
```

#### <a name="return-value"></a>戻り値

型が表すことができる値のセットが範囲指定されている場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

定義済みのすべての型が表すことができる値のセットは範囲指定されており、**true** を返します。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_bounded.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have bounded set "
        << "of representable values: "
        << numeric_limits<float>::is_bounded
        << endl;
   cout << "Whether double objects have bounded set "
        << "of representable values: "
        << numeric_limits<double>::is_bounded
        << endl;
   cout << "Whether long int objects have bounded set "
        << "of representable values: "
        << numeric_limits<long int>::is_bounded
        << endl;
   cout << "Whether unsigned char objects have bounded set "
        << "of representable values: "
        << numeric_limits<unsigned char>::is_bounded
        << endl;
}
```

```Output
Whether float objects have bounded set of representable values: 1
Whether double objects have bounded set of representable values: 1
Whether long int objects have bounded set of representable values: 1
Whether unsigned char objects have bounded set of representable values: 1
```

### <a name="is_exact"></a>is_exact

型で実行される計算に丸め誤差がないかどうかをテストします。

```cpp
static constexpr bool is_exact = false;
```

#### <a name="return-value"></a>戻り値

計算に丸め誤差がない場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

定義済みのすべての整数型には値の正確な表現があり、**false** を返します。 固定小数点表現または有理表現も正確であると見なされますが、浮動小数点表現は正確ではありません。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_exact.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<float>::is_exact
        << endl;
   cout << "Whether double objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<double>::is_exact
        << endl;
   cout << "Whether long int objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<long int>::is_exact
        << endl;
   cout << "Whether unsigned char objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<unsigned char>::is_exact
        << endl;
}
```

```Output
Whether float objects have calculations free of rounding errors: 0
Whether double objects have calculations free of rounding errors: 0
Whether long int objects have calculations free of rounding errors: 1
Whether unsigned char objects have calculations free of rounding errors: 1
```

### <a name="is_iec559"></a>is_iec559

型が IEC 559 標準に準拠しているかどうかをテストします。

```cpp
static constexpr bool is_iec559 = false;
```

#### <a name="return-value"></a>戻り値

型が IEC 559 標準に準拠している場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

IEC 559 は、浮動小数点値に関する国際標準であり、米国では IEEE 754 とも呼ばれます。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_iec559.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects conform to iec559 standards: "
        << numeric_limits<float>::is_iec559
        << endl;
   cout << "Whether double objects conform to iec559 standards: "
        << numeric_limits<double>::is_iec559
        << endl;
   cout << "Whether int objects conform to iec559 standards: "
        << numeric_limits<int>::is_iec559
        << endl;
   cout << "Whether unsigned char objects conform to iec559 standards: "
        << numeric_limits<unsigned char>::is_iec559
        << endl;
}
```

```Output
Whether float objects conform to iec559 standards: 1
Whether double objects conform to iec559 standards: 1
Whether int objects conform to iec559 standards: 0
Whether unsigned char objects conform to iec559 standards: 0
```

### <a name="is_integer"></a>is_integer

型が整数を表せるかどうかをテストします。

```cpp
static constexpr bool is_integer = false;
```

#### <a name="return-value"></a>戻り値

型が整数を表せる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

定義済みのすべて整数型は、整数を表せます。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_integer.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an integral representation: "
        << numeric_limits<float>::is_integer
        << endl;
   cout << "Whether double objects have an integral representation: "
        << numeric_limits<double>::is_integer
        << endl;
   cout << "Whether int objects have an integral representation: "
        << numeric_limits<int>::is_integer
        << endl;
   cout << "Whether unsigned char objects have an integral representation: "
        << numeric_limits<unsigned char>::is_integer
        << endl;
}
```

```Output
Whether float objects have an integral representation: 0
Whether double objects have an integral representation: 0
Whether int objects have an integral representation: 1
Whether unsigned char objects have an integral representation: 1
```

### <a name="is_modulo"></a>is_modulo

**type** が剰余を表せるかどうかをテストします。

```cpp
static constexpr bool is_modulo = false;
```

#### <a name="return-value"></a>戻り値

型が剰余を表せる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

剰余表現は、すべての結果がいくつかの値を法とする剰余を結果とする表現です。 定義済みのすべての符号なし整数型は剰余を表せます。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_modulo.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a modulo representation: "
        << numeric_limits<float>::is_modulo
        << endl;
   cout << "Whether double objects have a modulo representation: "
        << numeric_limits<double>::is_modulo
        << endl;
   cout << "Whether signed char objects have a modulo representation: "
        << numeric_limits<signed char>::is_modulo
        << endl;
   cout << "Whether unsigned char objects have a modulo representation: "
        << numeric_limits<unsigned char>::is_modulo
        << endl;
}
```

```Output
Whether float objects have a modulo representation: 0
Whether double objects have a modulo representation: 0
Whether signed char objects have a modulo representation: 1
Whether unsigned char objects have a modulo representation: 1
```

### <a name="is_signed"></a>is_signed

型が符号付きを表せるかどうかをテストします。

```cpp
static constexpr bool is_signed = false;
```

#### <a name="return-value"></a>戻り値

型が符号付きを表せる場合は **true**、それ以外の場合は **false**。

#### <a name="remarks"></a>解説

メンバーは、符号付きを表せる型の場合は true を格納します。これは、定義済みのすべての浮動小数点型および符号付き整数型の場合に該当します。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_signaled.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signed representation: "
        << numeric_limits<float>::is_signed
        << endl;
   cout << "Whether double objects have a signed representation: "
        << numeric_limits<double>::is_signed
        << endl;
   cout << "Whether signed char objects have a signed representation: "
        << numeric_limits<signed char>::is_signed
        << endl;
   cout << "Whether unsigned char objects have a signed representation: "
        << numeric_limits<unsigned char>::is_signed
        << endl;
}
```

```Output
Whether float objects have a signed representation: 1
Whether double objects have a signed representation: 1
Whether signed char objects have a signed representation: 1
Whether unsigned char objects have a signed representation: 0
```

### <a name="is_specialized"></a>is_specialized

クラステンプレート `numeric_limits`で型に明示的な特殊化が定義されているかどうかをテストします。

```cpp
static constexpr bool is_specialized = false;
```

#### <a name="return-value"></a>戻り値

型にクラステンプレートで明示的な特殊化が定義されている場合は**true** 。それ以外の場合は**false** 。

#### <a name="remarks"></a>解説

ポインター以外のすべてのスカラー型には、クラステンプレート `numeric_limits`に対して明示的な特殊化が定義されています。

#### <a name="example"></a>例

```cpp
// numeric_limits_is_specialized.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float>::is_specialized
        << endl;
   cout << "Whether float* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float*>::is_specialized
        << endl;
   cout << "Whether int objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int>::is_specialized
        << endl;
   cout << "Whether int* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int*>::is_specialized
        << endl;
}
```

```Output
Whether float objects have an explicit specialization in the class: 1
Whether float* objects have an explicit specialization in the class: 0
Whether int objects have an explicit specialization in the class: 1
Whether int* objects have an explicit specialization in the class: 0
```

### <a name="lowest"></a>降順

負の最小有限値を返します。

```cpp
static constexpr Type lowest() throw();
```

#### <a name="return-value"></a>戻り値

負の最小有限値を返します。

#### <a name="remarks"></a>解説

型に対して最も負の有限値を返します (通常、整数型の場合は `min()`、浮動小数点型の場合は `-max()`)。 `is_bounded` が**true**の場合、戻り値は意味があります。

### <a name="max"></a>制限

型の最大の有限値を返します。

```cpp
static constexpr Type max() throw();
```

#### <a name="return-value"></a>戻り値

型の最大の有限値。

#### <a name="remarks"></a>解説

最大有限値は、 **INT**型の場合は INT_MAX、 **float**型の場合は FLT_MAX です。 [is_bounded](#is_bounded) が **true** である場合、戻り値に意味があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_max.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main() {
   cout << "The maximum value for type float is:  "
        << numeric_limits<float>::max( )
        << endl;
   cout << "The maximum value for type double is:  "
        << numeric_limits<double>::max( )
        << endl;
   cout << "The maximum value for type int is:  "
        << numeric_limits<int>::max( )
        << endl;
   cout << "The maximum value for type short int is:  "
        << numeric_limits<short int>::max( )
        << endl;
}
```

### <a name="max_digits10"></a>max_digits10

その型の別個の 2 つの値が別個の 10 進表現であることを確証するために必要な 10 進桁数を返します。

```cpp
static constexpr int max_digits10 = 0;
```

#### <a name="return-value"></a>戻り値

その型の別個の 2 つの値が別個の 10 進表現であることを確証するために必要な 10 進桁数を返します。

#### <a name="remarks"></a>解説

このメンバーは、その型の別個の 2 つの値が別個の 10 進表現であることを確証するために必要な 10 進桁数を格納します。

### <a name="max_exponent"></a>max_exponent

基数を累乗した場合に、浮動小数点型が有限値として表すことができる正の整数の最大指数を返します。

```cpp
static constexpr int max_exponent = 0;
```

#### <a name="return-value"></a>戻り値

型が表すことができる、整数基数に基づく最大指数。

#### <a name="remarks"></a>解説

メンバー関数の戻り値は、浮動小数点型に対してのみ意味があります。 `max_exponent` は、**float** 型の場合は値 FLT_MAX_EXP です。

#### <a name="example"></a>例

```cpp
// numeric_limits_max_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum radix-based exponent for type float is:  "
        << numeric_limits<float>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type double is:  "
        << numeric_limits<double>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type long double is:  "
        << numeric_limits<long double>::max_exponent
        << endl;
}
```

```Output
The maximum radix-based exponent for type float is:  128
The maximum radix-based exponent for type double is:  1024
The maximum radix-based exponent for type long double is:  1024
```

### <a name="max_exponent10"></a>max_exponent10

10 の基数を累乗した場合に、浮動小数点型が有限値として表すことができる正の整数の最大指数を返します。

```cpp
static constexpr int max_exponent10 = 0;
```

#### <a name="return-value"></a>戻り値

型が表すことができる、10 の基数に基づく整数の最大指数。

#### <a name="remarks"></a>解説

メンバー関数の戻り値は、浮動小数点型に対してのみ意味があります。 `max_exponent` は、**float** 型の場合は値 FLT_MAX_10 です。

#### <a name="example"></a>例

```cpp
// numeric_limits_max_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum base 10 exponent for type float is:  "
           << numeric_limits<float>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type double is:  "
           << numeric_limits<double>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type long double is:  "
           << numeric_limits<long double>::max_exponent10
           << endl;
}
```

```Output
The maximum base 10 exponent for type float is:  38
The maximum base 10 exponent for type double is:  308
The maximum base 10 exponent for type long double is:  308
```

### <a name="min"></a>」

型の最小の正規化値を返します。

```cpp
static constexpr Type min() throw();
```

#### <a name="return-value"></a>戻り値

型の最小の正規化値。

#### <a name="remarks"></a>解説

最小正規化値は、 **INT**型の場合は INT_MIN、 **float**型の場合は FLT_MIN です。 [Is_bounded](#is_bounded)が**true**の場合、または[is_signed](#is_signed)が**false**の場合、戻り値は意味があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum value for type float is:  "
        << numeric_limits<float>::min( )
        << endl;
   cout << "The minimum value for type double is:  "
        << numeric_limits<double>::min( )
        << endl;
   cout << "The minimum value for type int is:  "
        << numeric_limits<int>::min( )
        << endl;
   cout << "The minimum value for type short int is:  "
        << numeric_limits<short int>::min( )
        << endl;
}
```

```Output
The minimum value for type float is:  1.17549e-038
The minimum value for type double is:  2.22507e-308
The minimum value for type int is:  -2147483648
The minimum value for type short int is:  -32768
```

### <a name="min_exponent"></a>min_exponent

基数の底を累乗した場合に、浮動小数点型が有限値として表すことができる負の整数の最大指数を返します。

```cpp
static constexpr int min_exponent = 0;
```

#### <a name="return-value"></a>戻り値

型が表すことができる、整数基数に基づく最小指数。

#### <a name="remarks"></a>解説

メンバー関数は、浮動小数点型に対してのみ意味があります。 `min_exponent` は、**float** 型の場合は値 FLT_MIN_EXP です。

#### <a name="example"></a>例

```cpp
// numeric_limits_min_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum radix-based exponent for type float is:  "
        << numeric_limits<float>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type double is:  "
        << numeric_limits<double>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type long double is:  "
         << numeric_limits<long double>::min_exponent
        << endl;
}
```

```Output
The minimum radix-based exponent for type float is:  -125
The minimum radix-based exponent for type double is:  -1021
The minimum radix-based exponent for type long double is:  -1021
```

### <a name="min_exponent10"></a>min_exponent10

10 の基数を累乗した場合に、浮動小数点型が有限値として表すことができる負の整数の最大指数を返します。

```cpp
static constexpr int min_exponent10 = 0;
```

#### <a name="return-value"></a>戻り値

型が表すことができる、10 の基数に基づく整数の最小指数。

#### <a name="remarks"></a>解説

メンバー関数は、浮動小数点型に対してのみ意味があります。 `min_exponent10` は、**float** 型の場合は値 FLT_MIN_10_EXP です。

#### <a name="example"></a>例

```cpp
// numeric_limits_min_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum base 10 exponent for type float is:  "
        << numeric_limits<float>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type double is:  "
        << numeric_limits<double>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type long double is:  "
        << numeric_limits<long double>::min_exponent10
        << endl;
}
```

```Output
The minimum base 10 exponent for type float is:  -37
The minimum base 10 exponent for type double is:  -307
The minimum base 10 exponent for type long double is:  -307
```

### <a name="quiet_nan"></a>quiet_NaN

型の静かな非数表現 (NAN) を返します。

```cpp
static constexpr Type quiet_NaN() throw();
```

#### <a name="return-value"></a>戻り値

型の静かな NAN。

#### <a name="remarks"></a>解説

[has_quiet_NaN](#has_quiet_nan) が **true** である場合にのみ、戻り値に意味があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The quiet NaN for type float is:  "
        << numeric_limits<float>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type int is:  "
        << numeric_limits<int>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type long double is:  "
        << numeric_limits<long double>::quiet_NaN( )
        << endl;
}
```

```Output
The quiet NaN for type float is:  1.#QNAN
The quiet NaN for type int is:  0
The quiet NaN for type long double is:  1.#QNAN
```

### <a name="radix"></a>ベース

型の表現に使用される、基数と呼ばれる整数の底を返します。

```cpp
static constexpr int radix = 0;
```

#### <a name="return-value"></a>戻り値

型の表現の整数の底。

#### <a name="remarks"></a>解説

底は、定義済みの整数型の場合は 2 であり、指数を累乗する際に使用されます。または、定義済みの浮動小数点型の場合は FLT_RADIX です。

#### <a name="example"></a>例

```cpp
// numeric_limits_radix.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The base for type float is:  "
        << numeric_limits<float>::radix
        << endl;
   cout << "The base for type int is:  "
        << numeric_limits<int>::radix
        << endl;
   cout << "The base for type long double is:  "
        << numeric_limits<long double>::radix
        << endl;
}
```

```Output
The base for type float is:  2
The base for type int is:  2
The base for type long double is:  2
```

### <a name="round_error"></a>round_error

型の丸め誤差の最大値を返します。

```cpp
static constexpr Type round_error() throw();
```

#### <a name="return-value"></a>戻り値

型の丸め誤差の最大値。

#### <a name="example"></a>例

```cpp
// numeric_limits_round_error.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum rounding error for type float is:  "
        << numeric_limits<float>::round_error( )
        << endl;
   cout << "The maximum rounding error for type int is:  "
        << numeric_limits<int>::round_error( )
        << endl;
   cout << "The maximum rounding error for type long double is:  "
        << numeric_limits<long double>::round_error( )
        << endl;
}
```

```Output
The maximum rounding error for type float is:  0.5
The maximum rounding error for type int is:  0
The maximum rounding error for type long double is:  0.5
```

### <a name="round_style"></a>round_style

実装において、浮動小数点値を整数値に丸め処理を行うために選択可能なさまざまな方式を記述した値を返します。

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

#### <a name="return-value"></a>戻り値

丸め処理スタイルを記述した、`float_round_style` 列挙型からの値。

#### <a name="remarks"></a>解説

メンバーは、実装において、浮動小数点値を整数値に丸め処理を行うために選択可能なさまざまな方式を記述した値を格納します。

丸め処理スタイルはこの実装でハードコーディングされています。このため、プログラムが別の丸め処理モードを開始しても、値が変わることはありません。

#### <a name="example"></a>例

```cpp
// numeric_limits_round_style.cpp
// compile with: /EHsc
#include <iostream>
#include <float.h>
#include <limits>

using namespace std;

int main( )
{
   cout << "The rounding style for a double type is: "
        << numeric_limits<double>::round_style << endl;
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );
   cout << "The rounding style for a double type is now: "
        << numeric_limits<double>::round_style << endl;
   cout << "The rounding style for an int type is: "
        << numeric_limits<int>::round_style << endl;
}
```

```Output
The rounding style for a double type is: 1
The rounding style for a double type is now: 1
The rounding style for an int type is: 0
```

### <a name="signaling_nan"></a>signaling_NaN

型のシグナリング非数 (NAN) の表現を返します。

```cpp
static constexpr Type signaling_NaN() throw();
```

#### <a name="return-value"></a>戻り値

型のシグナリング NAN の表現。

#### <a name="remarks"></a>解説

[has_signaling_NaN](#has_signaling_nan) が **true** である場合にのみ、戻り値に意味があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The signaling NaN for type float is:  "
        << numeric_limits<float>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type int is:  "
        << numeric_limits<int>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type long double is:  "
        << numeric_limits<long double>::signaling_NaN( )
        << endl;
}
```

### <a name="tinyness_before"></a>tinyness_before

型が、値を丸める前に正規化された値として表現するには小さすぎることを確認できるかどうかをテストします。

```cpp
static constexpr bool tinyness_before = false;
```

#### <a name="return-value"></a>戻り値

型が丸めの前に小さい値を検出できる場合は**true** 。できない場合は**false** 。

#### <a name="remarks"></a>解説

小さい値を検出できる型は、IEC 559 の浮動小数点表現にオプションとして含まれており、これを実装するといくつかの結果に影響を与える可能性があります。

#### <a name="example"></a>例

```cpp
// numeric_limits_tinyness_before.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types can detect tinyness before rounding: "
        << numeric_limits<float>::tinyness_before
        << endl;
   cout << "Whether double types can detect tinyness before rounding: "
        << numeric_limits<double>::tinyness_before
        << endl;
   cout << "Whether long int types can detect tinyness before rounding: "
        << numeric_limits<long int>::tinyness_before
        << endl;
   cout << "Whether unsigned char types can detect tinyness before rounding: "
        << numeric_limits<unsigned char>::tinyness_before
        << endl;
}
```

```Output
Whether float types can detect tinyness before rounding: 1
Whether double types can detect tinyness before rounding: 1
Whether long int types can detect tinyness before rounding: 0
Whether unsigned char types can detect tinyness before rounding: 0
```

### <a name="traps"></a>落とし穴

型において算術例外に関するレポートをトラップするように実装されているかどうかをテストします。

```cpp
static constexpr bool traps = false;
```

#### <a name="return-value"></a>戻り値

型においてトラップが実装されている場合は **true**、実装されていない場合は **false**。

#### <a name="example"></a>例

```cpp
// numeric_limits_traps.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types have implemented trapping: "
        << numeric_limits<float>::traps
        << endl;
   cout << "Whether double types have implemented trapping: "
        << numeric_limits<double>::traps
        << endl;
   cout << "Whether long int types have implemented trapping: "
        << numeric_limits<long int>::traps
        << endl;
   cout << "Whether unsigned char types have implemented trapping: "
        << numeric_limits<unsigned char>::traps
        << endl;
}
```

```Output
Whether float types have implemented trapping: 1
Whether double types have implemented trapping: 1
Whether long int types have implemented trapping: 0
Whether unsigned char types have implemented trapping: 0
```
