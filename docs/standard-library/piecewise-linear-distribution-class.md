---
title: "piecewise_linear_distribution クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- piecewise_linear_distribution
- std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution
- std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::reset
- std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::intervals
- std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::densities
- std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::param
- std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::min
- std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::max
- std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::operator()
- std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type
- std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::intervals
- std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::densities
- std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator==
- std::piecewise_linear_distribution::param_type::operator!=
- random/std::piecewise_linear_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- piecewise_linear_distribution class
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: d91ffbbc989babde5bb83f344ca2447cb018f16d
ms.lasthandoff: 02/24/2017

---
# <a name="piecewiselineardistribution-class"></a>piecewise_linear_distribution クラス
各間隔で確率が直線的に変化する可変幅間隔を持つ、区分線形分布を生成します。  
  
## <a name="syntax"></a>構文  
```  
template<class RealType = double>
class piecewise_linear_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   piecewise_linear_distribution();
   template <class InputIteratorI, class InputIteratorW>  
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
#### <a name="parameters"></a>パラメーター  
 `RealType`  
 結果を表す浮動小数点型。既定値は `double` です。 使用可能な型については、[\<random>](../standard-library/random.md) をご覧ください。  
  
## <a name="remarks"></a>コメント  
 このサンプリング分布は、各間隔で確率が直線的に変化する可変幅間隔を持っています。 他のサンプリング分布の詳細については、「[piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md)」および [discrete_distribution](../standard-library/discrete-distribution-class.md) に関する記事を参照してください。  
  
 次の表は、個々のメンバーに関する記事にリンクしています。  
  
||||  
|-|-|-|  
|[piecewise_linear_distribution::piecewise_linear_distribution](#piecewise_linear_distribution__piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|  
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[piecewise_linear_distribution::param_type](#piecewise_linear_distribution__param_type)|  
  
プロパティ関数 `intervals()` は、格納されている分布の区間セットを含む `vector<result_type>` を返します。  
  
プロパティ関数 `densities()` は、格納されている分布の区間セットを含む `vector<result_type>` を返します。これは、コンストラクター パラメーターに指定されている重みに従って計算されます。  
  
プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。  

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。  
  
`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。  
  
`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。
  
分布クラスとそのメンバーの詳細については、[\<random>](../standard-library/random.md) をご覧ください。  
  
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
  
    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15  
    vector<double> intervals{ 0, 1, 6, 15 };  
    // weights determine the densities used by the distribution  
    vector<double> weights{ 1, 5, 5, 10 };  
  
    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "intervals (index: interval):" << endl;  
    vector<double> i = distr.intervals();  
    int counter = 0;  
    for (const auto& n : i) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
    cout << "densities (index: density):" << endl;  
    vector<double> d = distr.densities();  
    counter = 0;  
    for (const auto& n : d) {  
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
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;  
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
max() == 15
intervals (index: interval):
          0:   0.0000000000          
          1:   1.0000000000          
          2:   6.0000000000          
          3:  15.0000000000
densities (index: density):
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<random>  
  
 **名前空間:** std  
  
##  <a name="a-namepiecewiselineardistributionpiecewiselineardistributiona--piecewiselineardistributionpiecewiselineardistribution"></a><a name="piecewise_linear_distribution__piecewise_linear_distribution"></a>  piecewise_linear_distribution::piecewise_linear_distribution  
 分布を作成します。  
  
```  
 
// default constructor  
piecewise_linear_distribution();

 
// constructs using a range of intervals, [firstI, lastI), with  
// matching weights starting at firstW  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

 
// constructs using an initializer list for range of intervals,  
// with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(initializer_list<RealType>  
intervals, UnaryOperation weightfunc);

 
// constructs using an initializer list for range of count intervals,  
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

 
// constructs from an existing param_type structure  
explicit piecewise_linear_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>パラメーター  
*firstI*  
ターゲット範囲内の先頭の要素を示す入力反復子。  
  
*lastI*  
ターゲット範囲内の末尾の要素を示す入力反復子。  
  
*firstW*  
重み範囲内の先頭の要素を示す入力反復子。  
  
*intervals*  
分布の区間を含む [initializer_list](../cpp/initializers.md)。  
  
*count*  
分布範囲内にある要素の数。  
  
*xmin*  
分布範囲内の最小値。  
  
*xmax*  
分布範囲内の最大値。 *xmin* より大きくなければなりません。  
  
*weightfunc*  
分布の確率関数を表すオブジェクト。 パラメーターと戻り値の両方が `double` に変換可能である必要があります。  
  
*parm*  
分布の作成に使用されるパラメーターの構造体。  
  
### <a name="remarks"></a>コメント  
既定のコンストラクターは、確率密度が 1 の、0 から 1 までの 1 つの区間を含むように、格納されているパラメーターを設定します。  
  
反復子の範囲コンストラクター  
  
```  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(
    InputIteratorI firstI, 
    InputIteratorI lastI,  
    InputIteratorW firstW);
```  
  
シーケンスにわたる反復子の区間 [ `firstI`, `lastI`) と、`firstW` で始まる対応する重みシーケンスを使用して分布オブジェクトを構築します。  
  
初期化子リスト コンストラクター  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    initializer_list<result_type> intervals,   
    UnaryOperation weightfunc);
```  
  
は、初期化子リスト `intervals` の区間と、関数 `weightfunc` から生成された重みを使用して分布オブジェクトを構築します。  
  
次のように定義されたコンストラクターは  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    size_t count, 
    result_type xmin, 
    result_type xmax,  
    UnaryOperation weightfunc);
```  
  
[ `xmin,xmax`] で一様に分布した `count` 個の区間を含み、各区間に関数 `weightfunc` に応じた重みを割り当てる分布オブジェクトを構築します。`weightfunc` は&1; つのパラメーターを受け入れて戻り値を持ち、いずれも `double` に変換可能である必要があります。 **前提条件:**`xmin < xmax`。  
  
次のように定義されたコンストラクターは  
```  
explicit piecewise_linear_distribution(const param_type& parm);
```  
格納されたパラメーター構造体として `parm` を使用する分布オブジェクトを作成します。  
  
##  <a name="a-namepiecewiselineardistributionparamtypea--piecewiselineardistributionparamtype"></a><a name="piecewise_linear_distribution__param_type"></a>  piecewise_linear_distribution::param_type  
分布のすべてのパラメーターを格納します。  
  
```  
struct param_type {  
   typedef piecewise_linear_distribution<result_type> distribution_type;  
   param_type();
   template <class IterI, class IterW>  
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>  
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;
     
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>パラメーター  
[piecewise_linear_distribution](#piecewise_linear_distribution__piecewise_linear_distribution) のコンストラクター パラメーターを参照してください。  
  
### <a name="remarks"></a>コメント  
 **前提条件:** `xmin < xmax`  
  
この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。  
  
## <a name="see-also"></a>関連項目  
 [\<random>](../standard-library/random.md)



