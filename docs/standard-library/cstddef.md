---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 87d268977ee46112fedce517e66a9e68071863db
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457570"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

C 標準ライブラリヘッダー \<stddef.h > をインクルードし、関連`std`する名前を名前空間に追加します。 このヘッダーをインクルードすると、C 標準ライブラリヘッダーの外部リンケージを使用して宣言され`std`た名前が、名前空間で宣言されます。

> [!NOTE]
> \<cstddef > には**byte**型が含まれており、 **wchar_t**型は含まれません。

## <a name="syntax"></a>構文

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>名前空間とマクロ

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>パラメーター

*ptrdiff_t*\
配列オブジェクトの2つの添字の差を保持できる、実装定義の符号付き整数型。

*size_t*\
任意のオブジェクトのサイズ (バイト単位) を格納するのに十分な大きさの実装定義の符号なし整数型。

*max_align_t*\
すべてのスカラー型のアラインメント要件が少なくとも優れており、すべてのコンテキストでアラインメント要件がサポートされている POD 型。

*nullptr_t*\
**Nullptr**式の型のシノニム。 **Nullptr**アドレスは取得できませんが、左辺値である別の*nullptr_t*オブジェクトのアドレスを取得できます。

## <a name="byte-class"></a>byte クラス

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
