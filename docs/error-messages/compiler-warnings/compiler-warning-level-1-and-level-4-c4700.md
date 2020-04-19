---
title: コンパイラの警告 (レベル 1 およびレベル 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300298"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>コンパイラの警告 (レベル 1 およびレベル 4) C4700

> 初期化されていないローカル変数 '*名前*' を使用

ローカル変数*名前*されました*使用*からは、読み取り、値が割り当てられる前にします。 C および C++ では、ローカル変数は既定では初期化されていません。 初期化されていない変数は、任意の値を含めることができ、その使用は、未定義の動作につながります。 警告 C4700 はほぼ常に、プログラムで予期しない結果またはクラッシュを引き起こす可能性のあるバグを示します。

この問題を解決するには、宣言されるときに、ローカル変数を初期化または使用される前に値を代入できます。 関数は、参照パラメーターとして渡されるか、そのアドレスがポインター パラメーターとして渡された場合、変数を初期化するために使用できます。

## <a name="example"></a>例

この例では、初期化されますつながるガベージ値の種類を表示する前に変数 t、u、および v を使用する場合、C4700 が生成されます。 変数 x、y、および z を使用する前に初期化されるため、警告が発生しません。

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

、初期化されていないときにこのコードは、実行、t、u および v、s の出力は予測できません。

```Output
Value in s: 37816963
Value in w: 42
```
