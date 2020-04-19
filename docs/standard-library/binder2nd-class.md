---
title: binder2nd クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 297f91dd9283b9f004247d2d1814b30a17e7ffa2
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890093"
---
# <a name="binder2nd-class"></a>binder2nd クラス

二項関数の2番目の引数を指定された値にバインドすることによって、二項関数オブジェクトを単項関数オブジェクトに変換するコンストラクターを提供するクラステンプレート。 C++ 11 では非推奨となりました。 C++ 17 では削除されています。

## <a name="syntax"></a>構文

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>パラメーター

*func*\
単項関数オブジェクトに変換する二項関数オブジェクト。

*右*\
二項関数オブジェクトの 2 つ目の引数がバインドされている値。

*左*\
調整後の二項オブジェクトが 2 つ目の引数の固定値と比較する引数の値。

## <a name="return-value"></a>戻り値

二項関数オブジェクトの2番目の引数を値*right*にバインドした結果として生成される単項関数オブジェクト。

## <a name="remarks"></a>Remarks

クラステンプレートは、バイナリ関数オブジェクト*func*のコピーを `op`に格納し、`value`の*右側*のコピーを格納します。 `op(left, value)`を返すように、メンバー関数 `operator()` を定義します。

*Func*が `Operation` 型のオブジェクトで、c が定数である場合、 [bind2nd](../standard-library/functional-functions.md#bind2nd)`(func, c)` は `binder2nd` クラス `binder2nd<Operation>(func, c)`コンストラクターに相当し、より便利です。

## <a name="example"></a>例

```cpp
// functional_binder2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
