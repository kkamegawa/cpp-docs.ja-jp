---
title: 範囲ベースの for ステートメント (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 1cbdb4e1636f471c26f6742b9e8686a332ed845f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244145"
---
# <a name="range-based-for-statement-c"></a>範囲ベースの for ステートメント (C++)

`statement` 内の各要素に対して `expression` を繰り返し順番に実行します。

## <a name="syntax"></a>構文

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Remarks

範囲ベースを使用して、**for**ステートメントは、「範囲」を反復処理できるものとして定義されているを実行する必要があるループを構築-たとえば、 `std::vector`、またはその他の C++ 標準ライブラリ シーケンスの範囲内`begin()`と`end()`します。 宣言されている名前、`for-range-declaration`部分は、ローカル、**for**ステートメントで再宣言することはできませんと`expression`または`statement`します。 なお、[auto](../cpp/auto-cpp.md)キーワードをお勧め、`for-range-declaration`ステートメントの部分。

**Visual Studio 2017: 新機能**範囲ベースの for ループでは、begin() および end() が同じ型のオブジェクトを返す必要はなくなりました。 これにより、end() が、Ranges-V3 範囲で定義されている範囲で使用されるような sentinel オブジェクトを返すことができます。 詳細については、「[Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)」 (範囲ベースの for loop の汎用化) と「[range-v3 library on GitHub](https://github.com/ericniebler/range-v3)」 (GitHub 上の range-v3 ライブラリ) を参照してください。

このコードは範囲ベースの使用方法を示します**for**配列とベクターを反復処理するループ。

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

出力を次に示します。

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

範囲に基づく**for**とループが終了しますでこれらのいずれかの`statement`が実行される: を[break](../cpp/break-statement-cpp.md)、[return](../cpp/return-statement-cpp.md)、または[goto](../cpp/goto-statement-cpp.md)にラベルが範囲ベースの外部ステートメント**for**ループします。 [continue](../cpp/continue-statement-cpp.md)ステートメントの範囲に基づく**for**ループは、現在のイテレーションのみを終了します。

留意してこれらの事実について範囲に基づく**for**:

- 自動的に配列を認識します。

- `.begin()` と `.end()` を持つコンテナーを認識します。

- それ以外については `begin()` および `end()` の引数依存の参照を使用します。

## <a name="see-also"></a>関連項目

[auto](../cpp/auto-cpp.md)<br/>
[繰り返しステートメント](../cpp/iteration-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[while ステートメント (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while ステートメント (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for ステートメント (C++)](../cpp/for-statement-cpp.md)