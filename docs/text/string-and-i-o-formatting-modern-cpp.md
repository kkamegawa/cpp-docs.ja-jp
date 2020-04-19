---
title: 文字列および I/O の書式設定 (Modern C++)
description: 最新C++ので使用できる書式設定された文字列 i/o の選択肢。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: 7ea858a8a8126d3754783edee0dd3ea5409e5f73
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898826"
---
# <a name="string-and-io-formatting-modern-c"></a>文字列および I/O の書式設定 (Modern C++)

C++[\<iostream >](../standard-library/iostream.md)クラス、関数、および演算子は、書式設定された文字列 i/o をサポートしています。 たとえば、次のコードは、`cout` を設定して、16進数で出力するように整数を書式設定する方法を示しています。 1つ目は、フォーマット状態が `cout`に渡されると、変更されるまでその状態を維持するため、現在の状態を保存して、後でリセットします。 コードの1行にのみ適用されるわけではありません。

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

この方法はタイプセーフで拡張可能ですが、複雑で詳細な方法でもあります。

## <a name="alternative-format-options"></a>代替形式のオプション

別の方法として、ブーストC++ライブラリから `Boost.Format` を使用することもできます。これは非標準です。 ブーストライブラリは、[ブースト](https://www.boost.org/)web サイトからダウンロードできます。

`Boost.Format` には、次のような利点があります。

- Safe: タイプセーフであり、エラーの場合は例外をスローします。たとえば、項目数が少なすぎるか少なすぎることを示します。

- 拡張可能: ストリーム可能なすべての型を処理できます。

- 便利: 標準の POSIX と同様の書式指定文字列。

`Boost.Format` は、安全でC++拡張性のある[iostream >\<](../standard-library/iostream-programming.md)に基づいて構築されていますが、パフォーマンスに最適化されていません。 パフォーマンスの最適化が必要な場合は、高速で使いやすい C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)と[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)を検討してください。 ただし、これらは拡張可能であり、脆弱性から安全ではありません。 (セキュリティが強化されたバージョンがありますが、わずかながらパフォーマンスが低下します。 詳細については、「 [printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)と[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md))」を参照してください。

次のコードは、Boost の書式設定機能のいくつかを示します。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>参照

[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)
