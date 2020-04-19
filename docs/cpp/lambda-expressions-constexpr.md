---
title: C++ では constexpr ラムダ式
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: d1bc60a6da813e54c857da38b0164f544216be00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368696"
---
# <a name="constexpr-lambda-expressions-in-c"></a>C++ では constexpr ラムダ式

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c++17](../build/reference/std-specify-language-standard-version.md))。ラムダ式として宣言することがあります**constexpr**または定数式の中でキャプチャまたは導入される各データ メンバーの初期化が許可されている場合、定数式で使用します。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

ラムダは暗黙的に**constexpr**その結果の要件を満たしている場合、 **constexpr**関数。

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

ラムダが暗黙的または明示的に場合**constexpr**、および関数ポインターに変換する、結果として得られる関数も**constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリの関数オブジェクト](../standard-library/function-objects-in-the-stl.md)<br/>
[関数呼び出し](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)