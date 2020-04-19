---
title: is_placeholder クラス
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 9fa7d4aaade6244fe26f89f3a667598d39471a47
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245148"
---
# <a name="isplaceholder-class"></a>is_placeholder クラス

型がプレースホルダーであるかどうかをテストします。

## <a name="syntax"></a>構文

struct is_placeholder { static const int value; };

## <a name="remarks"></a>Remarks

型 `Ty` がプレース ホルダーではない場合、定数値 `value` は 0 となります。それ以外の場合、値は、バインドされる関数呼び出しの引数の位置になります。 これを使用して、N 番目のプレースホルダー `_N` の値 `N` を決定します。

## <a name="example"></a>例

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
