---
title: アルゴリズム (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220154"
---
# <a name="algorithms-modern-c"></a>アルゴリズム (Modern C++)

最新の C++ プログラミングをお勧めのアルゴリズムを使用すること、 [C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)します。 次に重要な例を示します。

- **for_each**既定の走査アルゴリズムであります。 (また**変換**not インプレースのセマンティクスのためです)。

- **find_if**既定の検索アルゴリズムであります。

- **並べ替え**、 **lower_bound**、およびその他の既定の並べ替えと検索アルゴリズム。

Strict を使用して、比較子を記述する **<** 使用と*名前付きラムダ*することができます。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>ループ

可能であれば、使用範囲に基づく**の**ループまたはアルゴリズム呼び出し、またはその両方手の形で記述したループの代わりにします。 **コピー**、**変換**、 **count_if**、 **remove_if**、およびなど、それらの意図が明確なために、手書きのループよりはるかに優れているとバグのないコードを記述しやすくなります。 また、多くの C++ 標準ライブラリ アルゴリズムより効率的にする実装の最適化があります。

次のような従来の C++ を使用する代わりに、

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

次のような最新の C++ を使用してください。

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>範囲ベースの for ループ

範囲に基づく**の**ループは、c++ 11 言語の機能、C++ 標準ライブラリ アルゴリズムではありません。 しかし、ループに関するこの説明と併せて理解すると便利です。 範囲ベースの**の**ループはの拡張機能、**の**キーワードと値の範囲を反復処理するループを記述する便利で効率的な方法を提供します。 C++ 標準ライブラリ コンテナー、文字列、および配列は既製の範囲に基づく**の**ループします。 この新しいイテレーション構文をユーザー定義型に対して有効にするには、次のサポートを追加します。

- 反復子を構造体の先頭に返す `begin` メソッドと、反復子を構造体の末尾に返す `end` メソッド。

- これらのメソッドの反復子のサポート:**演算子**<strong>\*</strong>、**演算子! =**、および**operator++** (前置バージョン)。

これらのメソッドは、メンバー関数かスタンドアロン関数のいずれかです。

## <a name="random-numbers"></a>乱数

従来の CRT の `rand()` 関数に多くの欠陥があることは広く知られた事実であり、C++ コミュニティで長年にわたって議論されてきました。 最新の c++ では、これらの欠陥に対処する必要はありません — 独自一様に分布した乱数ジェネレーターを作成する必要はも —で示すように、迅速かつ簡単に作成するためのツールは、C++標準ライブラリで使用できるため、[\<ランダム >](../standard-library/random.md)します。

## <a name="see-also"></a>関連項目

[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
