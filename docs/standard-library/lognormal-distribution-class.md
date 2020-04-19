---
title: lognormal_distribution クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::lognormal_distribution
- random/std::lognormal_distribution::reset
- random/std::lognormal_distribution::m
- random/std::lognormal_distribution::s
- random/std::lognormal_distribution::param
- random/std::lognormal_distribution::min
- random/std::lognormal_distribution::max
- random/std::lognormal_distribution::operator()
- random/std::lognormal_distribution::param_type
- random/std::lognormal_distribution::param_type::m
- random/std::lognormal_distribution::param_type::s
- random/std::lognormal_distribution::param_type::operator==
- random/std::lognormal_distribution::param_type::operator!=
helpviewer_keywords:
- std::lognormal_distribution [C++]
- std::lognormal_distribution [C++], reset
- std::lognormal_distribution [C++], m
- std::lognormal_distribution [C++], s
- std::lognormal_distribution [C++], param
- std::lognormal_distribution [C++], min
- std::lognormal_distribution [C++], max
- std::lognormal_distribution [C++], param_type
- std::lognormal_distribution [C++], param_type
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
ms.openlocfilehash: bcf587c5029fdf0b61da45dbd4ee9250f4c3a43b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687788"
---
# <a name="lognormal_distribution-class"></a>lognormal_distribution クラス

対数正規分布を生成します。

## <a name="syntax"></a>構文

```cpp
template <class RealType = double>
class lognormal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;
   // constructor and reset functions
   explicit lognormal_distribution(result_type m = 0.0, result_type s = 1.0);
   explicit lognormal_distribution(const param_type& parm);
   void reset();
   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);
   // property functions
   result_type m() const;
   result_type s() const;
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

クラステンプレートは、ユーザー指定の整数型の値を生成する分布を表します。指定されていない場合は**double**型で、対数正規分布に従って分布されます。 次の表は、個々のメンバーに関する記事にリンクしています。

||||
|-|-|-|
|[lognormal_distribution](#lognormal_distribution)|`lognormal_distribution::m`|`lognormal_distribution::param`|
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[param_type](#param_type)|

プロパティ関数 `m()` および `s()` は、格納されている分布パラメーター *m* および *s* に対してそれぞれの値を返します。

プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。

`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。

`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。

分布クラスとそのメンバーについて詳しくは、「[\<random>](../standard-library/random.md)」をご覧ください。

LogNormal 分布の詳細については、Wolfram MathWorld の記事「[LogNormal Distribution](https://go.microsoft.com/fwlink/p/?linkid=400917)」をご覧ください。

## <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const double m, const double s, const int samples) {

    // uncomment to use a non-deterministic seed
    //    random_device gen;
    //    mt19937 gen(rd());
    mt19937 gen(1701);

    lognormal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.m() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.s() << endl;

    // generate the distribution as a histogram
    map<double, int> histogram;
    for (int i = 0; i < samples; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << samples << " samples:" << endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        cout << fixed << setw(11) << ++counter << ": "
            << setw(14) << setprecision(10) << elem.first << endl;
    }
    cout << endl;
}

int main()
{
    double m_dist = 1;
    double s_dist = 1;
    int samples = 10;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter a floating point value for the 'm' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 's' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'm' distribution parameter: 0
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: 0.3862809339
    2: 0.4128865601
    3: 0.4490576787
    4: 0.4862035428
    5: 0.5930607126
    6: 0.8190778771
    7: 0.8902379317
    8: 2.8332911667
    9: 5.1359445565
    10: 5.4406507912
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="lognormal_distribution"></a>  lognormal_distribution::lognormal_distribution

分布を作成します。

```cpp
explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);
explicit lognormal_distribution(const param_type& parm);
```

### <a name="parameters"></a>パラメーター

*m* \
`m` 分布パラメーター。

*s* \
`s` 分布パラメーター。

*parm* \
分布の作成に使用される `param_type` の構造体。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < s`

1 つ目のコンストラクターは、格納されている値 `m` と `s` にそれぞれ *m* と *s* の値を保持するオブジェクトを作成します。

2 番目のコンストラクターは、格納されているパラメーターが *parm* から初期化されるオブジェクトを作成します。 `param()` メンバー関数を呼び出すと、既存の分布の現在のパラメーターを取得および設定できます。

## <a name="param_type"></a>  lognormal_distribution::param_type

分布のパラメーターを格納します。

```cpp
struct param_type {
   typedef lognormal_distribution<result_type> distribution_type;
   param_type(result_type m = 0.0, result_type s = 1.0);
   result_type m() const;
   result_type s() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
};
```

### <a name="parameters"></a>パラメーター

*m* \
`m` 分布パラメーター。

*s* \
`s` 分布パラメーター。

*右*\
比較に使用される `param_type` 構造体。

### <a name="remarks"></a>Remarks

**前提条件:** `0.0 < s`

この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
