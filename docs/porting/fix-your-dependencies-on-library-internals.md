---
title: ライブラリ内部の依存C++関係を修正する
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: 5486cd65a34e3ef69f3b2e948ba0ad020e68b326
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627013"
---
# <a name="fix-your-dependencies-on-c-library-internals"></a>ライブラリ内部の依存C++関係を修正する

Microsoft では、標準ライブラリ、ほとんどの C ランタイム ライブラリ、および多くのバージョンの Visual Studio の他の Microsoft ライブラリ用のソース コードを公開しています。 その目的は、ユーザーがライブラリの動作を理解できるようにすることと、コードをデバッグすることです。 ライブラリのソース コードを公開する 1 つの副次作用は、いくつかの内部値、データ構造、および関数が、ライブラリ インターフェイスの一部でない場合でも公開されることです。 通常、これらには、2 つのアンダースコア、または後ろに大文字が続くアンダースコアで始まる名前があり、この名前は C++ 標準で実装用に予約されます。 これらの値、構造、および関数は実装の詳細であり、ライブラリの経時的な変化に伴い、変更される可能性があるため、これらに依存しないことを強くお勧めします。 依存すると、コードが移植できなくなり、コードを新しいバージョンのライブラリに移行しようとしたときに問題が発生する危険性があります。

ほとんどの場合、各リリースの Visual Studio の新機能または重大な変更に関するドキュメントでは、ライブラリ内部の変更は示されません。 結局は、これらの実装の詳細による影響を受けないことになっています。 ただし、ライブラリ内で表示できる一部のコードを使用したいという非常に強い衝動にかられる場合があります。 このトピックでは、依存していた可能性のある CRT または標準ライブラリ内部の依存関係について説明します。また、コードを更新し、これらの依存関係を削除して、コードの移植性を高めたり、新しいバージョンのライブラリに移行できるようにしたりする方法についても説明します。

## <a name="_hash_seq"></a>_Hash_seq

いくつかの文字列型で `std::hash` を実装するために使用される、内部ハッシュ関数 `std::_Hash_seq(const unsigned char *, size_t)` は、最近のバージョンの標準ライブラリでは表示されていました。 この関数は、文字シーケンスで [FNV-1a ハッシュ]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function)を実装していました。

この依存関係を削除するためのいくつかのオプションがあります。

- `basic_string` と同じハッシュ コード構造を使用して、`const char *` シーケンスを順不同のコンテナーに挿入する予定の場合は、そのハッシュ コードを移植可能な方法で返す、`std::string_view` を取る `std::hash` テンプレート オーバーロードを使用して行うことができます。 文字列ライブラリ コードは今後、FNV-1a ハッシュの使用に依存する可能性もあれば、依存しない可能性もあります。したがって、これが特定のハッシュ アルゴリズムに依存しないようにするための最良の方法です。

- 任意のメモリに FNV-1a ハッシュを生成する予定の場合は、Microsoft がこのためのコードを作成しました。このコードは、GitHub の [VCSamples]( https://github.com/Microsoft/vcsamples) リポジトリ内のスタンドアロン ヘッダー ファイル [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq) ([MIT ライセンス](https://github.com/Microsoft/VCSamples/blob/master/license.txt)認可済み) から入手できます。 便利なコピーも含まれています。 このコードをヘッダー ファイルにコピーし、影響を受けるコードにヘッダーを追加してから `_Hash_seq` を検索して `fnv1a_hash_bytes` で置き換えることができます。 `_Hash_seq` の内部実装と同じ動作が得られます。

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>関連項目

[以前のバージョンのビジュアルからのプロジェクトのアップグレードC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[アップグレードに関する潜在的な問題 (Visual C++) の概要](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Universal CRT へのコードのアップグレード](upgrade-your-code-to-the-universal-crt.md)