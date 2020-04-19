---
title: chi_squared_distribution クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::chi_squared_distribution
- random/std::chi_squared_distribution::reset
- random/std::chi_squared_distribution::n
- random/std::chi_squared_distribution::param
- random/std::chi_squared_distribution::min
- random/std::chi_squared_distribution::max
- random/std::chi_squared_distribution::operator()
- random/std::chi_squared_distribution::param_type
- random/std::chi_squared_distribution::param_type::n
- random/std::chi_squared_distribution::param_type::operator==
- random/std::chi_squared_distribution::param_type::operator!=
helpviewer_keywords:
- std::chi_squared_distribution [C++]
- std::chi_squared_distribution [C++], reset
- std::chi_squared_distribution [C++], n
- std::chi_squared_distribution [C++], param
- std::chi_squared_distribution [C++], min
- std::chi_squared_distribution [C++], max
- std::chi_squared_distribution [C++], param_type
- std::chi_squared_distribution [C++], param_type
ms.assetid: 9b603fbe-cafd-4a92-b8c5-a434d60b8122
ms.openlocfilehash: f7f6f038c0e8bc922874388065ce06d76854bc1b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688303"
---
# <a name="chi_squared_distribution-class"></a>chi_squared_distribution クラス

カイ 2 乗分布を生成します。

## <a name="syntax"></a>構文

```cpp
template<class RealType = double>
class chi_squared_distribution {
public:
    // types
    typedef RealType result_type;
    struct param_type;

    // constructor and reset functions
    explicit chi_squared_distribution(RealType n = 1);
    explicit chi_squared_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    RealType n() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>パラメーター

*Realtype* \
浮動小数点演算の結果の型。既定値は**double**です。 使用可能な型については、「[\<random>](../standard-library/random.md)」を参照してください。

*Urng* \
均一乱数ジェネレーターエンジン。 使用可能な型については、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="remarks"></a>Remarks

クラステンプレートは、カイ2乗分布に従って分布した、ユーザー指定の浮動小数点型の値、または none を指定した場合は**double**型の値を生成する分布を表します。 次の表は、個々のメンバーに関する記事にリンクしています。

||||
|-|-|-|
|[chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)|`chi_squared_distribution::n`|`chi_squared_distribution::param`|
|`chi_squared_distribution::operator()`||[param_type](#param_type)|

プロパティ関数 `n()` は、格納されている分布パラメーター `n` の値を返します。

プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。

`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。

`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。

分布クラスとそのメンバーについて詳しくは、「[\<random>](../standard-library/random.md)」をご覧ください。

カイ 2 乗分布の詳細については、Wolfram MathWorld の記事「[Chi-Squared Distribution (カイ 2 乗分布)](https://go.microsoft.com/fwlink/p/?linkid=400528)」を参照してください。

## <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::chi_squared_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

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
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

最初の実行:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .5
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.5000000000
Distribution for 10 samples:
    1: 0.0007625595
    2: 0.0016895062
    3: 0.0058683478
    4: 0.0189647765
    5: 0.0556619371
    6: 0.1448191353
    7: 0.1448245325
    8: 0.1903494379
    9: 0.9267525768
    10: 1.5429743723
```

2 回目の実行:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .3333
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.3333000000
Distribution for 10 samples:
    1: 0.0000148725
    2: 0.0000490528
    3: 0.0003175988
    4: 0.0018454535
    5: 0.0092808795
    6: 0.0389540735
    7: 0.0389562514
    8: 0.0587028468
    9: 0.6183666639
    10: 1.3552086624
```

3 回目の実行:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1000
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 1000.0000000000
Distribution for 10 samples:
    1: 958.5284624473
    2: 958.7882787809
    3: 963.0667684792
    4: 987.9638091514
    5: 1016.2433493745
    6: 1021.9337111110
    7: 1021.9723046240
    8: 1035.7622110505
    9: 1043.8725156645
    10: 1054.7051509381
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="chi_squared_distribution"></a>  chi_squared_distribution::chi_squared_distribution

分布を作成します。

```cpp
explicit chi_squared_distribution(result_type n = 1.0);
explicit chi_squared_distribution(const param_type& parm);
```

### <a name="parameters"></a>パラメーター

*n*\
`n` 分布パラメーター。

*parm* \
分布の作成に使用されるパラメーターの構造体。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < n`

1 番目のコンストラクターは、格納されている `n` の値が *n* の値を保持するオブジェクトを作成します。

2 番目のコンストラクターは、格納されているパラメーターが *parm* から初期化されるオブジェクトを作成します。 `param()` メンバー関数を呼び出すと、既存の分布の現在のパラメーターを取得および設定できます。

## <a name="param_type"></a>  chi_squared_distribution::param_type

分布のパラメーターを格納します。

```cpp
struct param_type {
   typedef chi_squared_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>パラメーター

*n*\
`n` 分布パラメーター。

*右*\
このオブジェクトと比較する `param_type` オブジェクト。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < n`

この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
