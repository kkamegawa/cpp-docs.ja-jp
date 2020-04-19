---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: eecd3efea6239c92a8bc81c0ed13a9563e5b87d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154296"
---
# <a name="func"></a>__func__

**(C++ 11)** 事前定義の識別子&#95; &#95;func&#95; &#95; 、外側の関数の非修飾かつ非装飾名を含む文字列として暗黙的に定義されます。 &#95;&#95;func&#95; &#95;が C++ 標準で必須し、は、Microsoft 拡張機能ではありません。

## <a name="syntax"></a>構文

```cpp
__func__
```

## <a name="return-value"></a>戻り値

Null で終わる const char 配列を返します文字の関数の名前を格納します。

## <a name="example"></a>例

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>必要条件

C++11