---
title: 文字列および I/o に書式設定 (Modern C)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: c051a7d70042456d30bee0ebb2b362c5d05b8e37
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220505"
---
# <a name="string-and-io-formatting-modern-c"></a>文字列および I/O の書式設定 (Modern C++)

C++ [iostreams](../standard-library/iostream.md)の I/O の書式設定された文字列に対応します。 たとえば、次のコードは、整数を書式設定して 16 進数で出力するための cout を設定する方法を示します。まず現在の状態を保存し、後で再度設定します。これは、状態の書式設定が一度 cout に渡されると、1 行のコードの間だけでなく、変更されるまでその状態を保つためです。

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

これは、多くの場合、非常に面倒です。 別の方法として、非標準ですが、Boost C++ ライブラリの Boost.Format を使用できます。 任意の Boost ライブラリをダウンロードすることができます、 [Boost](http://www.boost.org/) web サイト。

Boost.Format の利点は以下のとおりです。

- 安全性:タイプ セーフで、エラーの例外をスロー-項目が多すぎるか少なすぎるの仕様など。

- 拡張。ストリーム配信できる任意の型に対して機能します。

- 便利です。標準 Posix と類似の書式指定文字列。

Boost.Format は C++ でビルドが[iostreams](../standard-library/iostream-programming.md)パフォーマンスが最適化されたは安全で拡張可能である、これらはありません。 パフォーマンスの最適化を必要とする場合は、C を検討してください[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)と[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)は高速で簡単に使用します。 ただし、それらは拡張可能でなく、また脆弱性から安全ではありません。 (セキュリティが強化されたバージョンがありますが、わずかながらパフォーマンスが低下します。 詳細については、次を参照してください。 [printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)と[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md))。

次のコードは、Boost の書式設定機能のいくつかを示します。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>関連項目

[C++ へようこそ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
