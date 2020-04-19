---
title: Checked Iterators
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: f5a31843386d2246f5d74eae1f40b93f0ae35c90
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452139"
---
# <a name="checked-iterators"></a>Checked Iterators

チェックを行う反復子は、コンテナーの境界が上書きされないようにします。 チェックを行う反復子は、リリース ビルドおよびデバッグ ビルドの両方に適用されます。 デバッグ モードでのコンパイル時に debug 反復子を使用する方法の詳細については、「[debug 反復子のサポート](../standard-library/debug-iterator-support.md)」を参照してください。

## <a name="remarks"></a>Remarks

チェックを行う反復子によって生成される警告を無効にする方法の詳細については、「[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)」を参照してください。

[\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) プロセッサ マクロを使用して、チェックを行う反復子の機能の有効と無効を切り替えることができます。 レベルが1または2として定義されている場合、反復子の安全でない使用によってランタイムエラーが発生し、プログラムが終了します。 0 と定義されている場合、チェックを行う反復子は無効になります。 既定では、リリースビルドの場合は0、デバッグビルドの場合は2になります。

> [!IMPORTANT]
> 古いドキュメントやソース コードは、[_SECURE_SCL](../standard-library/secure-scl.md) マクロを参照している場合があります。 _SECURE_SCL を制御するには、レベルを使用します (_s) 詳細については、「[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)」を参照してください。

このレベルが1または2として定義されている場合、これらの反復子チェックが実行されます。 (_s)

- すべての標準反復子 (たとえば、[vector::iterator](../standard-library/vector-class.md#iterator)) がチェックされます。

- 出力反復子がチェックを行う反復子の場合、[std::copy](../standard-library/algorithm-functions.md#copy) などの標準ライブラリ関数の呼び出しの動作がチェックされます。

- 出力反復子がチェックを行わない反復子である場合、標準ライブラリ関数の呼び出しによってコンパイラの警告が表示されます。

- 次の関数は、コンテナーの境界の外側へのアクセスがある場合は、ランタイム エラーを生成します。

|||||
|-|-|-|-|
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[back](../standard-library/deque-class.md#back)|[front](../standard-library/deque-class.md#front)|
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[back](../standard-library/list-class.md#back)|[front](../standard-library/list-class.md#front)|[back](../standard-library/queue-class.md#back)|
|[front](../standard-library/queue-class.md#front)|[vector::operator\[\]](../standard-library/vector-class.md#op_at)|[back](../standard-library/vector-class.md#back)|[front](../standard-library/vector-class.md#front)|

デバッグレベルを0として定義する (_s):

- すべての標準的な反復子はチェックされません。 反復子はコンテナーの境界を越えて移動でき、未定義の動作につながります。

- 出力反復子がチェックを行う反復子である場合、`std::copy` などの標準ライブラリ関数の呼び出しによって動作がチェックされます。

- 出力反復子がチェックを行わない反復子である場合、標準ライブラリ関数の呼び出しによって動作がチェックされません。

コンテナーの境界を越えて移動しようとすると、チェックを行う反復子は、`invalid_parameter_handler` を呼び出す反復子を参照します。 `invalid_parameter_handler` の詳細については、「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」を参照してください。

チェックを行う反復子をサポートする反復子アダプターは、[checked_array_iterator クラス](../standard-library/checked-array-iterator-class.md)と [unchecked_array_iterator クラス](../standard-library/unchecked-array-iterator-class.md)です。

## <a name="example"></a>例

あるレベルを1または2に設定してコンパイルすると、特定のクラスのインデックス演算子を使用して、コンテナーの境界の外側にある要素にアクセスしようとすると、ランタイムエラーが発生します。

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

このプログラムは、"67" をポイントし、その後でエラーに関する追加情報を含むアサーション エラー ダイアログ ボックスを表示します。

## <a name="example"></a>例

同様に、[レベル] を1または2に設定してコンパイルする場合、コンテナーが空のときにコンテナークラスのまたは`front` `back`を使用して要素にアクセスしようとすると、ランタイムエラーが発生します。

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

このプログラムは、エラーに関する追加情報を含むアサーション エラー ダイアログ ボックスを表示します。

## <a name="example"></a>例

次のコードは、さまざまな反復子のユース ケースのシナリオを示しており、それぞれにコメントが付けられています。 既定では、デバッグビルドの場合は "2" に、リテールビルドの場合は0に設定されます。

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

`cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` を使用してこのコードをコンパイルするときに、コンパイラが警告を表示しますが、コンパイルはエラーなしで実行可能です。

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

コマンドラインで実行すると、実行可能ファイルがこの出力を生成します。

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[debug 反復子のサポート](../standard-library/debug-iterator-support.md)
