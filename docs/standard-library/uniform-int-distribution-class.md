---
title: uniform_int_distribution クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_int_distribution [C++]
- std::uniform_int_distribution [C++], reset
- std::uniform_int_distribution [C++], a
- std::uniform_int_distribution [C++], b
- std::uniform_int_distribution [C++], param
- std::uniform_int_distribution [C++], min
- std::uniform_int_distribution [C++], max
- std::uniform_int_distribution [C++], param_type
- std::uniform_int_distribution [C++], param_type
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
ms.openlocfilehash: 7e24c320e909bb2d0471acdd275f89c43d3e44de
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684511"
---
# <a name="uniform_int_distribution-class"></a>uniform_int_distribution クラス

すべて含まれる出力の範囲内で、一様の (すべての値は同様の可能性があります) 整数の分布を生成します。

## <a name="syntax"></a>構文

```cpp
template<class IntType = int>
   class uniform_int_distribution {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
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

*Inttype* \
整数の結果型、既定値は**int**です。使用できる型については、「 [\<random >](../standard-library/random.md)」を参照してください。

## <a name="remarks"></a>Remarks

クラステンプレートは、すべての値が均等になるように、分布を使用してユーザー指定の整数型の値を生成する包括的包含分布を記述します。 次の表は、個々のメンバーに関する記事にリンクしています。

||||
|-|-|-|
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|

プロパティ メンバー `a()` は、現在格納されている分布の最小限度値を返し、`b()` は、現在格納されている最大限度値を返します。 この分布クラスの場合、これらの最小値と最大値は、一般的なプロパティ関数 `min()` と `max()` で返される値と同じです。

プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。

`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。

`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。

分布クラスとそのメンバーについて詳しくは、「[\<random>](../standard-library/random.md)」をご覧ください。

## <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int a, const int b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_int_distribution<> distr(a, b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int a_dist = 1;
    int b_dist = 10;

    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter an integer value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="uniform_int_distribution"></a>  uniform_int_distribution::uniform_int_distribution

分布を作成します。

```cpp
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```

### <a name="parameters"></a>パラメーター

*\*
乱数値の下限 (包含的)。

*b* \
乱数値の上限 (包含的)。

*parm* \
分布の作成に使用される `param_type` の構造体。

### <a name="remarks"></a>Remarks

**前提条件:** `a ≤ b`

1つ目のコンストラクターは、値*を*保持し、格納さ*れて*いる*b*値が値*b*を保持するオブジェクトを構築します。

2 番目のコンストラクターは、格納されているパラメーターが *parm* から初期化されるオブジェクトを作成します。 `param()` メンバー関数を呼び出すと、既存の分布の現在のパラメーターを取得および設定できます。

## <a name="param_type"></a>  uniform_int_distribution::param_type

分布のパラメーターを格納します。

```cpp
struct param_type {
   typedef uniform_int_distribution<result_type> distribution_type;
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>パラメーター

*\*
乱数値の下限 (包含的)。

*b* \
乱数値の上限 (包含的)。

*右*\
このオブジェクトと比較する `param_type` オブジェクト。

### <a name="remarks"></a>Remarks

**前提条件:** `a ≤ b`

この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
