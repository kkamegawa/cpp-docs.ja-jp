---
title: C++ 標準ライブラリの概要
ms.date: 11/04/2016
helpviewer_keywords:
- headers, C++ library
- C++ Standard Library
- libraries, Standard C++
- C++ Standard Library, headers
ms.assetid: 7acb83a4-da73-4ad3-bc30-a71289db7f60
ms.openlocfilehash: 7b1e5226db751605d5352b1c5195759c34d080f5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452451"
---
# <a name="c-standard-library-overview"></a>C++ 標準ライブラリの概要

すべての C++ ライブラリのエンティティは 1 つ以上の標準ヘッダーで宣言または定義されます。 この実装には、 \< C++標準では必要ない\<2 つの追加ヘッダー hash_map > と hash_set > が含まれています。 この実装がサポートするヘッダーの完全な一覧については、「[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)」をご覧ください。

C++ ライブラリのフリースタンディング実装では、これらのヘッダーの一部のみが提供されます。

|||
|-|-|
|[\<cstddef>](../standard-library/cstddef.md)|[\<<cstdlib>](../standard-library/cstdlib.md) (少なくとも関数 `abort`、`atexit`、`exit` を宣言する)|
|[\<exception>](../standard-library/exception.md)|[\<limits>](../standard-library/limits.md)|
|[\<new>](../standard-library/new.md)|[\<cstdarg>](../standard-library/cstdarg.md)|

C++ のライブラリのヘッダーには 2 つの広範な再分割があります。

- [iostreams](../standard-library/iostreams-conventions.md) の規則。

- [C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)の規則。

このセクションでは、以下のセクションについて説明します。

- [C++ ライブラリ ヘッダーの使用](../standard-library/using-cpp-library-headers.md)

- [C++ ライブラリの規則](../standard-library/cpp-library-conventions.md)

- [iostreams の規則](../standard-library/iostreams-conventions.md)

- [C++ プログラムの起動と終了](../standard-library/cpp-program-startup-and-termination.md)

- [安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)

- [Checked Iterators](../standard-library/checked-iterators.md)

- [反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)

- [C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)

- [C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)

- [stdext 名前空間](../standard-library/stdext-namespace.md)

- [正規表現 (C++)](../standard-library/regular-expressions-cpp.md)

Visual C++ ランタイム ライブラリの詳細については、「[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
