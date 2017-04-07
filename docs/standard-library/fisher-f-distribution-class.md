---
title: "fisher_f_distribution クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fisher_f_distribution
- std::fisher_f_distribution
- random/std::fisher_f_distribution
- std::fisher_f_distribution::reset
- random/std::fisher_f_distribution::reset
- std::fisher_f_distribution::m
- random/std::fisher_f_distribution::m
- std::fisher_f_distribution::n
- random/std::fisher_f_distribution::n
- std::fisher_f_distribution::param
- random/std::fisher_f_distribution::param
- std::fisher_f_distribution::min
- random/std::fisher_f_distribution::min
- std::fisher_f_distribution::max
- random/std::fisher_f_distribution::max
- std::fisher_f_distribution::operator()
- random/std::fisher_f_distribution::operator()
- std::fisher_f_distribution::param_type
- random/std::fisher_f_distribution::param_type
- std::fisher_f_distribution::param_type::m
- random/std::fisher_f_distribution::param_type::m
- std::fisher_f_distribution::param_type::n
- random/std::fisher_f_distribution::param_type::n
- std::fisher_f_distribution::param_type::operator==
- random/std::fisher_f_distribution::param_type::operator==
- std::fisher_f_distribution::param_type::operator!=
- random/std::fisher_f_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- fisher_f_distribution class
ms.assetid: 9513b6ce-3309-4be1-829b-f504bca35bbf
caps.latest.revision: 17
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
ms.sourcegitcommit: f293f074f2b8e2334dc70fbebba8e6f4c17efecc
ms.openlocfilehash: 3a0fc233334909249f75978ba095cb3f31af90dc
ms.lasthandoff: 02/24/2017

---
# <a name="fisherfdistribution-class"></a>fisher_f_distribution クラス
フィッシャー分布を生成します。  
  
## <a name="syntax"></a>構文  
```  
template<class RealType = double>
class fisher_f_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  // constructor and reset functions  
   explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
   explicit fisher_f_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   result_type m() const;
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
#### <a name="parameters"></a>パラメーター  
*RealType*  
浮動小数点の結果の型は、既定では `double` です。 使用可能な型については、「[\<random>](../standard-library/random.md)」を参照してください。  
  
*URNG* Uniform Random Number Generator エンジン。 使用可能な型については、[\<random>](../standard-library/random.md) をご覧ください。  
  
## <a name="remarks"></a>コメント  
 このテンプレート クラスは、フィッシャーの F 分布に従って分布した、ユーザー指定の浮動小数点型の値または型 `double` の値 (指定がない場合) を生成する分布を表します。 次の表は、個々のメンバーに関する記事にリンクしています。  
  
||||  
|-|-|-|  
|[fisher_f_distribution::fisher_f_distribution](#fisher_f_distribution__fisher_f_distribution)|`fisher_f_distribution::m`|`fisher_f_distribution::param`|  
|`fisher_f_distribution::operator()`|`fisher_f_distribution::n`|[fisher_f_distribution::param_type](#fisher_f_distribution__param_type)|  
  
 プロパティ関数 `m()` および `n()` は、格納されている分布パラメーター `m` および `n` に対してそれぞれの値を返します。  
  
プロパティ メンバー `param()` は、格納されている分布パラメーター パッケージ `param_type` を設定または返します。  

メンバー関数の `min()` と `max()` はそれぞれ、考えられる結果の最小値と最大値を返します。  
  
`reset()` メンバー関数は、次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。  
  
`operator()` メンバー関数は、現在のパラメーター パッケージと指定したパラメーター パッケージのいずれかから、URNG エンジンに基づいて次に生成された値を返します。
  
 分布クラスとそのメンバーの詳細については、[\<random>](../standard-library/random.md) を参照してください。  
  
 F 分布の詳細については、Wolfram MathWorld の記事「[F-Distribution](http://go.microsoft.com/fwlink/LinkId=400899)」(F 分布) を参照してください。  
  
## <a name="example"></a>例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double m, const double n, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1701);  
  
    std::fisher_f_distribution<> distr(m, n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "m() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.m() << std::endl;  
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
    double m_dist = 1;  
    double n_dist = 1;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'m\' distribution parameter (must be greater than zero): ";  
    std::cin >> m_dist;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(m_dist, n_dist, samples);  
}  
  
```  
  
## <a name="output"></a>出力  
 最初の実行:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0204569549  
    2: 0.0221376644  
    3: 0.0297234962  
    4: 0.1600937252  
    5: 0.2775342196  
    6: 0.3950701700  
    7: 0.8363200295  
    8: 0.9512500702  
    9: 2.7844815974  
    10: 3.4320929653  
```  
  
 2 回目の実行:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 1.0000000000  
n() == 0.1000000000  
Distribution for 10 samples:  
    1: 0.0977725649  
    2: 0.5304122767  
    3: 4.9468518084  
    4: 25.1012074939  
    5: 48.8082121613  
    6: 401.8075539377  
    7: 8199.5947873699  
    8: 226492.6855335717  
    9: 2782062.6639740225  
    10: 20829747131.7185860000  
```  
  
 3 回目の実行:  
  
```  
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): .1  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
m() == 0.1000000000  
n() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0000000000  
    2: 0.0000000000  
    3: 0.0000000000  
    4: 0.0000000000  
    5: 0.0000000033  
    6: 0.0000073975  
    7: 0.0000703800  
    8: 0.0280427735  
    9: 0.2660239949  
    10: 3.4363333954  
```  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<random>  
  
 **名前空間:** std  
  
##  <a name="a-namefisherfdistributionfisherfdistributiona--fisherfdistributionfisherfdistribution"></a><a name="fisher_f_distribution__fisher_f_distribution"></a>  fisher_f_distribution::fisher_f_distribution  
 分布を作成します。  
  
```  
explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
explicit fisher_f_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>パラメーター  
*m*  
 `m` 分布パラメーター。  
  
*n*  
 `n` 分布パラメーター。  
  
*parm*  
 分布の作成に使用される `param_type` の構造体。  
  
### <a name="remarks"></a>コメント  
 **前提条件:** `0.0 < m` および `0.0 < n`  
  
 1 つ目のコンストラクターは、格納されている値 `m` と `n` にそれぞれ *m* と *n* の値を保持するオブジェクトを作成します。  
  
 2 つ目のコンストラクターは、格納パラメーターが *parm* から初期化されるオブジェクトを作成します。 `param()` メンバー関数を呼び出すと、既存の分布の現在のパラメーターを取得および設定できます。  
  
##  <a name="a-namefisherfdistributionparamtypea--fisherfdistributionparamtype"></a><a name="fisher_f_distribution__param_type"></a>  fisher_f_distribution::param_type  
 分布のパラメーターを格納します。  
  
```cpp  
struct param_type {  
   typedef fisher_f_distribution<result_type> distribution_type;  
   param_type(result_type m = 1.0, result_type n = 1.0);
   result_type m() const;
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
### <a name="parameters"></a>パラメーター  
*m*  
 `m` 分布パラメーター。  
  
*n*  
 `n` 分布パラメーター。  
  
*right*  
このオブジェクトと比較する `param_type` オブジェクト。  
  
### <a name="remarks"></a>コメント  
 **前提条件:** `0.0 < m` および `0.0 < n`  
  
 この構造体は、インスタンス化時に分布のクラス コンストラクターに渡したり、`param()` メンバー関数に渡して、既存の分布の格納されているパラメーターを設定したり、`operator()` に渡して、格納されているパラメーターの代わりに使用したりすることができます。  
  
## <a name="see-also"></a>関連項目  
 [\<random>](../standard-library/random.md)



