---
title: discrete_distribution クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: ce668ebfdafc4a53bfc71ecf1f2fa76abb1c7532
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454379"
---
# <a name="discretedistribution-class"></a>discrete_distribution クラス

均等幅の区間を含み、各区間に一様確率を含む整数の離散分布を生成します。

## <a name="syntax"></a>構文

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>パラメーター

*IntType*\
整数の結果型、既定値は**int**です。使用可能な型については、[\<random>](../standard-library/random.md) をご覧ください。

## <a name="remarks"></a>Remarks

この標本分布には均等幅の区間が含まれ、各区間には一様確率が含まれます。 他のサンプリング分布の詳細については、「[piecewise_linear_distribution クラス](../standard-library/piecewise-linear-distribution-class.md)」および「[piecewise_constant_distribution クラス](../standard-library/piecewise-constant-distribution-class.md)」をご覧ください。

次の表は、個々のメンバーに関する記事にリンクしています。

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

プロパティ関数 `vector<double> probabilities()` は、生成される整数ごとに個別の確率を返します。

分布クラスとそのメンバーについて詳しくは、「[\<random>](../standard-library/random.md)」をご覧ください。

## <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<random>

**名前空間:** std

## <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution

分布を作成します。

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>パラメーター

*firstW*\
分布の作成元となるリストの最初の反復子。

*lastW*\
分布の作成元となるリストの最後の反復子 (反復子は最後に空の要素を使用するため、非包含的)。

*weightlist*\
分布の作成元となる [initializer_list](../cpp/initializers.md)。

*数*\
分布範囲内にある要素の数。 `count==0` の場合は、既定のコンストラクターと同じです (常に 0 を生成します)。

*低画質*\
分布範囲内の最小値。

*高い*\
分布範囲内の最大値。

*weightfunc*\
分布の確率関数を表すオブジェクト。 パラメーターと戻り値の両方が**double**型に変換可能である必要があります。

*parm*\
分布の作成に使用される `param_type` の構造体。

### <a name="remarks"></a>Remarks

既定のコンストラクターは、格納された確率値が値 1 である 1 つの要素を持つオブジェクトを構築します。 この結果、常に 0 を生成する分布になります。

パラメーター *firstW* と *lastW* のある反復子範囲コンストラクターは、区間シーケンス [*firstW*, *lastW*) 全体にわたる反復子から取得された重み値を使って分布オブジェクトを作成します。

*Weightlist*パラメーターを持つ初期化子リストコンストラクターは、初期化子リスト*weightlist*の重みを持つ分布オブジェクトを構築します。

*count*、*low*、*high*、*weightfunc* パラメーターを持つコンストラクターは、以下のルールに基づいて初期化された分布オブジェクトを作成します。

- *count* < 1 の場合、**n** = 1 で、このような場合は既定のコンストラクターと同じで、常に 0 を生成します。
- *count* > 0 の場合、**n** = *count* です。 指定された**d** = (*高* - *低*)/ **n**が0より大きく、 **d**の uniform 部分範囲を使用して`weight[k] = weightfunc(x)`いる場合、各重みは次のように割り当てられます ( **x** = *low*  + )。 **k d**    d/2 (k = 0、...、n-1)。 +  * 

`param_type` パラメーター *parm* を持つコンストラクターは、格納されたパラメーター構造体として *parm* を使う分布オブジェクトを作成します。

## <a name="param_type"></a>  discrete_distribution::param_type

分布のすべてのパラメーターを格納します。

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>パラメーター

*firstW*\
分布の作成元となるリストの最初の反復子。

*lastW*\
分布の作成元となるリストの最後の反復子 (反復子は最後に空の要素を使用するため、非包含的)。

*weightlist*\
分布の作成元となる [initializer_list](../cpp/initializers.md)。

*数*\
分布範囲内にある要素の数。 *count* が 0 の場合は、既定のコンストラクターと同じです (常に 0 を生成します)。

*低画質*\
分布範囲内の最小値。

*高い*\
分布範囲内の最大値。

*weightfunc*\
分布の確率関数を表すオブジェクト。 パラメーターと戻り値の両方が**double**型に変換可能である必要があります。

*そうです*\
このオブジェクトと比較する `param_type` オブジェクト。

### <a name="remarks"></a>Remarks

このパラメーター パッケージを `operator()` に渡して、戻り値を生成できます。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
