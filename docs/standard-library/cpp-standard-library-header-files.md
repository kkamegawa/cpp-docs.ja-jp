---
title: C++標準ライブラリのヘッダーファイル
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305410"
---
# <a name="c-standard-library-header-files"></a>C++標準ライブラリのヘッダーファイル

C++標準ライブラリと拡張機能のヘッダーファイル (カテゴリ別)。

## <a name="headers-by-category"></a>カテゴリ別ヘッダー

::: moniker range=">=vs-2017"

| カテゴリ | ヘッダー |
| - | - |
| [アルゴリズム](../cpp/algorithms-modern-cpp.md) | [\<アルゴリズム >](algorithm.md)、 [\<cstdlib >](cstdlib.md)、 [\<数値 >](numeric.md) |
| アトミック操作 |  [\<atomic >](atomic.md)<sup>11</sup> |
| C ライブラリラッパー | [\<cassert >](cassert.md)、 [\<ccomplex >](ccomplex.md)<sup>11 a b</sup>、 [\<cctype >](cctype.md)、 [\<ccomplex >](cerrno.md)、 [\<cfenv >](cfenv.md)<sup>11</sup>、\<[ccomplex >](cfloat.md)、 [\<cinttypes >](cinttypes.md)<sup>11</sup>、\<[ciso646 >](ciso646.md)<sup>b</sup>、 [\<climits >](climits.md)、 [\<ccomplex >](clocale.md)、 [\<ccomplex >](cmath.md)、\<[ccomplex >](csetjmp.md)、 [\<csignal >](csignal.md)、 [\<cstdalign が >](cstdalign.md)<sup>11 a b</sup>、 [\<cstdarg >](cstdarg.md)、 [\<cstdbool >](cstdbool.md)<sup>11 a b</sup>、 [\<cstddef >](cstddef.md)、 [\<cstdint >](cstdint.md)<sup>11</sup>、\<[csignal >](cstdio.md)、 [\<cstdlib >](cstdlib.md)、 [\<cstring >](cstring.md)、 [\<ctgmath >](ctgmath.md)<sup>11 a b</sup>、\<[ctime >](ctime.md)、\<[cuchar >](cuchar.md)<sup>11</sup>、 [\<cwchar >](cwchar.md)、 [\<cwctype >](cwctype.md) |
| 概念 | \<の概念 ><sup>20</sup> |
| [コンテナー](../cpp/containers-modern-cpp.md) | |
| シーケンスコンテナー | [\<array >](array.md)<sup>11</sup>、 [\<deque >](deque.md)、 [\<forward_list](forward-list.md)><sup>11</sup>、 [\<list >](list.md)、 [\<vector >](vector.md) |
| 順序付けされた連想コンテナー| [\<map>](map.md)、[\<set>](set.md) |
| 順序なしの連想コンテナー | [\<unordered_map >](unordered-map.md)<sup>11</sup>、 [\<unordered_set >](unordered-set.md)<sup>11</sup> |
| コンテナーアダプター | [\<queue>](queue.md)、[\<stack>](stack.md) |
| コンテナービュー | \<スパン ><sup>20</sup> |
| [エラーと例外処理](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md)、 [\<例外 >](exception.md)、 [\<stdexcept >](stdexcept.md)、 [\<system_error](system-error.md)><sup>11</sup> |
| 一般的なユーティリティ | \<><sup>17</sup>、 [\<bitset >](bitset.md)、\<charconv ><sup>17</sup>、 [\<cstdlib >](cstdlib.md)、\<実行 ><sup>17</sup>、 [\<機能 >](functional.md)、\<[メモリ >](memory.md)、\<memory_resource ><sup>17</sup>、\<オプション ><sup>17</sup>、\<[比率 >](ratio.md)<sup>11</sup>、\<[scoped_allocator >](scoped-allocator.md)<sup>11</sup>、 [\<タプル >](tuple.md)<sup>11</sup> [\<type_traits >](type-traits.md)<sup>11</sup>、 [\<typeindex >](typeindex.md)<sup>11</sup>、 [\<ユーティリティ >](utility.md)、\<variant ><sup>17</sup> |
| [I/o と書式設定](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>、 [\<cstdio >](cstdio.md)、 [\<filesystem >](filesystem.md)<sup>17</sup>、 [\<fstream >](fstream.md)、\<[iomanip >](iomanip.md)、\<[ios >](ios.md)、 [\<iosfwd >](iosfwd.md)、\<[iostream >](iostream.md)、\<[istream >](istream.md)、 [\<ostream](ostream.md)>、\<[sstream](sstream.md)>、\<[streambuf >](streambuf.md)、\<[strstream >](strstream.md)<sup>c</sup>、\<syncstream ><sup>20</sup> |
| 反復子 | [\<iterator>](iterator.md) |
| 言語サポート | [\<cfloat >](cfloat.md)、 [\<climits >](climits.md)、 [\<codecvt >](codecvt.md)<sup>11 a</sup>、\<compare ><sup>20</sup>、\<contract ><sup>20</sup>、\<コルーチン ><sup>20</sup>、\<[cfloat >](csetjmp.md)、\<[cfloat >](csignal.md)、\<[cstdarg >](cstdarg.md)、\<[cstddef >](cstddef.md)、 [\<cstdint >](cstdint.md)<sup>11</sup>、\<[cstdlib >](cstdlib.md)、\<[exception >](exception.md)、 [\<initializer_list >](initializer-list.md)<sup>11</sup>、 [\<制限 >](limits.md)、 [\<new >](new.md)、\<[typeinfo >](typeinfo.md)、\<version ><sup>20</sup> |
| ローカリゼーション | [\<clocale >](clocale.md)、 [\<codecvt >](codecvt.md)<sup>11 a</sup>、 [\<cvt/wbuffer >](cvt-wbuffer.md)、 [\<cvt/wbuffer >](cvt-wstring.md)、 [\<locale >](locale.md) |
| 数値演算と数値 | \<ビット ><sup>20</sup>、 [\<cfenv >](cfenv.md)<sup>11</sup>、 [\<cmath >](cmath.md)、 [\<複雑な >](complex.md)、 [\<cstdlib >](cstdlib.md)、\<の[制限 >](limits.md)、 [\<数値 >](numeric.md)、 [\<ランダム >](random.md)<sup>11</sup>、\<[比率 >](ratio.md)<sup>11</sup>、 [\<valarray >](valarray.md) |
| [メモリ管理](../cpp/smart-pointers-modern-cpp.md) | [\<アロケーター >](allocators-header.md)、 [\<メモリ >](memory.md)、\<memory_resource ><sup>17</sup>、 [\<新しい >](new.md)、 [\<](scoped-allocator.md)scoped_allocator ><sup>11</sup> |
| マルチスレッド | [\<atomic >](atomic.md)<sup>11</sup>、 [\<condition_variable >](condition-variable.md)<sup>11</sup>、 [\<今後 >](future.md)<sup>11</sup>、 [\<mutex >](mutex.md)<sup>11</sup>、 [\<shared_mutex](shared-mutex.md)><sup>14</sup>、 [\<スレッド >](thread.md)<sup>11</sup> |
| 範囲 | \<範囲 ><sup>20</sup> |
| 正規表現 | [\<regex >](regex.md)<sup>11</sup> |
| 文字列と文字データ | [\<cctype >](cctype.md)、 [\<cstdlib >](cstdlib.md)、 [\<cstring >](cstring.md)、 [\<cuchar >](cuchar.md)<sup>11</sup>、 [\<cwchar >](cwchar.md)、 [\<cwctype >](cwctype.md)、 [\<regex >](regex.md)<sup>11</sup>、 [\<string >](string.md)、 [\<string_view](string-view.md)><sup>17</sup> |
| 時間 | [\<chrono >](chrono.md)<sup>11</sup>、 [\<ctime >](ctime.md) |

<sup>11</sup> c++ 11 標準で追加されました。
<sup>14</sup>は c++ 14 標準で追加されました。
<sup>17</sup>は c++ 17 標準で追加されました。
<sup>20</sup>は、ドラフト c++ 20 標準で追加されました。
C++ 17 標準で非推奨<sup>と</sup>されます。
<sup>b</sup>は、c++ 20 標準のドラフトで削除されました。
<sup>c</sup> c++ 98 標準では非推奨とされます。

::: moniker-end

::: moniker range="vs-2015"

|カテゴリ|ヘッダー|
|-|-|
|[アルゴリズム](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|C ライブラリラッパー|[\<cassert>](cassert.md)、[\<cctype>](cctype.md)、[\<cerrno>](cerrno.md)、[\<cfenv>](cfenv.md)、[\<cfloat>](cfloat.md)、[\<cinttypes>](cinttypes.md)、[\<ciso646>](ciso646.md)、[\<climits>](climits.md)、[\<clocale>](clocale.md)、[\<cmath>](cmath.md)、[\<csetjmp>](csetjmp.md)、[\<csignal>](csignal.md)、[\<cstdarg>](cstdarg.md)、[\<cstdbool>](cstdbool.md)、[\<cstddef>](cstddef.md)、[\<cstdint>](cstdint.md)、[\<cstdio>](cstdio.md)、[\<cstdlib>](cstdlib.md)、[\<cstring>](cstring.md)、[\<ctgmath>](ctgmath.md)、[\<ctime>](ctime.md)、[\<cwchar>](cwchar.md)、[\<cwctype>](cwctype.md)|
|[コンテナー](../cpp/containers-modern-cpp.md)||
|シーケンスコンテナー|[\<配列 >](array.md)、 [\<deque >](deque.md)、 [\<forward_list](forward-list.md)>、 [\<リスト >](list.md)、 [\<vector >](vector.md)|
|順序付けされた連想コンテナー| [\<map>](map.md)、[\<set>](set.md)|
|順序なしの連想コンテナー|[\<unordered_map >](unordered-map.md)、 [\<unordered_set >](unordered-set.md)|
|アダプターコンテナー|[\<queue>](queue.md)、[\<stack>](stack.md)|
|[エラーと例外処理](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<例外 >](exception.md)、 [\<stdexcept >](stdexcept.md)、 [\<system_error >](system-error.md)|
|[I/o と書式設定](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md)、[\<fstream>](fstream.md)、[\<iomanip>](iomanip.md)、[\<ios>](ios.md)、[\<iosfwd>](iosfwd.md)、[\<iostream>](iostream.md)、[\<istream>](istream.md)、[\<ostream>](ostream.md)、[\<sstream>](sstream.md)、[\<streambuf>](streambuf.md)、[\<strstream>](strstream.md)|
|反復子|[\<iterator>](iterator.md)|
|ローカリゼーション|[\<codecvt>](codecvt.md)、[\<cvt/wbuffer>](cvt-wbuffer.md)、[\<cvt/wstring>](cvt-wstring.md)、[\<locale>](locale.md)|
|数値演算と数値|[\<complex>](complex.md)、[\<limits>](limits.md)、[\<numeric>](numeric.md)、[\<random>](random.md)、[\<ratio>](ratio.md)、[\<valarray>](valarray.md)|
|[メモリ管理](../cpp/smart-pointers-modern-cpp.md)|[\<アロケーター >](allocators-header.md)、 [\<メモリ >](memory.md)、 [\<新しい >](new.md)、 [\<scoped_allocator >](scoped-allocator.md)|
|マルチスレッド|[\<atomic >](atomic.md)、 [\<condition_variable >](condition-variable.md)、 [\<将来の >](future.md)、 [\<ミューテックス >](mutex.md)、 [\<shared_mutex](shared-mutex.md)>、 [\<スレッド >](thread.md)|
|その他のユーティリティ|[\<bitset >](bitset.md)、 [\<chrono >](chrono.md)、 [\<機能 >](functional.md)、 [\<](initializer-list.md)initializer_list >、 [\<組 >](tuple.md)、 [\<type_traits](type-traits.md)>、\<[typeinfo >](typeinfo.md)、\<[typeindex >](typeindex.md)、 [\<ユーティリティ >](utility.md)|
|文字列と文字データ|[\<regex >](regex.md)、 [\<文字列 >](string.md)、 [\<](string-view.md) string_view >

::: moniker-end

## <a name="see-also"></a>参照

[ライブラリC++ヘッダーの使用](using-cpp-library-headers.md)\
[C++標準ライブラリ](cpp-standard-library-reference.md)
