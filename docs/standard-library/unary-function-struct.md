---
title: unary_function 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::unary
helpviewer_keywords:
- unary_function class
ms.assetid: 04c2fbdc-c1f6-48ed-b6cc-292a6d484627
ms.openlocfilehash: deb142bb263af51bee515e445ea705bf248461b5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243483"
---
# <a name="unaryfunction-struct"></a>unary_function 構造体

派生クラスによって継承される可能性がある型を定義し、単項関数オブジェクトを提供する空の基底構造体。

## <a name="syntax"></a>構文

```cpp
struct unary_function
{
   typedef Arg argument_type;
   typedef Result result_type;
};
```

## <a name="remarks"></a>Remarks

このテンプレート構造体は、**result_type**`operator()`( **constargument_type&** ) **const** 形式のメンバー関数を定義するクラスの基底になります。

派生した単項関数すべてで、単一の引数型を **argument_type**、戻り値の型を **result_type** として参照できます。

## <a name="example"></a>例

```cpp
// functional_unary_function.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan10: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 10);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greaterthan10());
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
```
