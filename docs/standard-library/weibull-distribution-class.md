---
title: weibull_distribution クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::weibull_distribution
- random/std::weibull_distribution::reset
- random/std::weibull_distribution::a
- random/std::weibull_distribution::b
- random/std::weibull_distribution::param
- random/std::weibull_distribution::min
- random/std::weibull_distribution::max
- random/std::weibull_distribution::operator()
- random/std::weibull_distribution::param_type
- random/std::weibull_distribution::param_type::a
- random/std::weibull_distribution::param_type::b
- random/std::weibull_distribution::param_type::operator==
- random/std::weibull_distribution::param_type::operator!=
helpviewer_keywords:
- std::weibull_distribution [C++]
- std::weibull_distribution [C++], reset
- std::weibull_distribution [C++], a
- std::weibull_distribution [C++], b
- std::weibull_distribution [C++], param
- std::weibull_distribution [C++], min
- std::weibull_distribution [C++], max
- std::weibull_distribution [C++], param_type
- std::weibull_distribution [C++], param_type
ms.assetid: f20b49d3-1b9a-41af-8db4-baf800eaa02b
ms.openlocfilehash: 2c1e53c529be8c589f51b9011cee42e5f6f1165b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688512"
---
# <a name="weibull_distribution-class"></a>weibull_distribution クラス

ワイブル分布を生成します。

## <a name="syntax"></a>構文

```cpp
class weibull_distribution
   {
   public:
    // types
   typedef RealType result_type;
   struct param_type;

    // constructor and reset functions
   explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
   explicit weibull_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>パラメーター

*Realtype* \
浮動小数点演算の結果の型。既定値は**double**です。 使用可能な型については、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="remarks"></a>Remarks

クラステンプレートは、ワイブル分布に従って分布した、ユーザー指定の浮動小数点型の値、または none を指定した場合は**double**型の値を生成する分布を表します。 次の表は、個々のメンバーに関する記事にリンクしています。

||||
|-|-|-|
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|

プロパティ関数 `a()` と `b()` はそれぞれ、格納されている分布パラメーター *a* と *b* の値を返します。

プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。

`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。

`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。

分布クラスとそのメンバーについて詳しくは、「[\<random>](../standard-library/random.md)」をご覧ください。

Weibull 分布の詳細については、Wolfram MathWorld の記事「[Weibull Distribution (Weibull 分布)](http://mathworld.wolfram.com/WeibullDistribution.html)」を参照してください。

## <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::weibull_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'a' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

## <a name="output"></a>出力

最初の実行:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 1.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

2 回目の実行:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): .5
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 5.5
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 0.5000000000
b() == 5.5000000000
Distribution for 10 samples:
    1: 0.0482759823
    2: 0.0826617486
    3: 2.2835941207
    4: 2.3604817485
    5: 2.9417663742
    6: 2.9418471657
    7: 3.1685268104
    8: 11.5109922290
    9: 14.8543594043
    10: 24.7220241239
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="weibull_distribution"></a>  weibull_distribution::weibull_distribution

```cpp
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```

### <a name="parameters"></a>パラメーター

*\*
`a` 分布パラメーター。

*b* \
`b` 分布パラメーター。

*parm* \
分布の作成に使用される `param_type` の構造体。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < a` および `0.0 < b`

1 つ目のコンストラクターは、格納されている値 `a` と `b` にそれぞれ *a* と *b* の値を保持するオブジェクトを作成します。

2 番目のコンストラクターは、格納されているパラメーターが *parm* から初期化されるオブジェクトを作成します。 `param()` メンバー関数を呼び出すと、既存の分布の現在のパラメーターを取得および設定できます。

## <a name="param_type"></a>  weibull_distribution::param_type

分布のパラメーターを格納します。

```cpp
struct param_type {
   typedef weibull_distribution<result_type> distribution_type;
   param_type(result_type a = 1.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>パラメーター

*\*
`a` 分布パラメーター。

*b* \
`b` 分布パラメーター。

*右*\
このオブジェクトと比較する `param_type` オブジェクト。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < a` および `0.0 < b`

この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
