---
title: binder1st クラス
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 15b704134d47b7bf7d8857bf380c756b0b03a1b0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688384"
---
# <a name="binder1st-class"></a>binder1st クラス

二項関数の最初の引数を指定された値にバインドすることによって、二項関数オブジェクトを単項関数オブジェクトに変換するコンストラクターを提供するクラステンプレート。 C++ 11 では、 [bind](functional-functions.md#bind)を優先し、c++ 17 では廃止されました。

## <a name="syntax"></a>構文

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>パラメーター

*binary_fn* \
単項関数オブジェクトに変換する二項関数オブジェクト。

*左*\
二項関数オブジェクトの最初の引数がバインドされている値。

*右*\
調整後の二項オブジェクトが 2 つ目の引数の固定値と比較する引数の値。

## <a name="return-value"></a>戻り値

二項関数オブジェクトの最初の引数を*左*の値にバインドした結果として生成される単項関数オブジェクト。

## <a name="remarks"></a>Remarks

クラステンプレートには `op` にバイナリ*関数オブジェクトの*コピーが格納され、`value` には*左*のコピーが格納されます。 @No__t_1 を返すように、メンバー関数 `operator()` を定義します。

*Binary_fn*が `Operation` 型のオブジェクトで `c` が定数である場合、`bind1st(binary_fn, c)` は `binder1st<Operation>(binary_fn, c)` と同じくらい便利です。 詳細については、「 [bind1st](../standard-library/functional-functions.md#bind1st)」を参照してください。

## <a name="example"></a>例

```cpp
// functional_binder1st.cpp
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
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
