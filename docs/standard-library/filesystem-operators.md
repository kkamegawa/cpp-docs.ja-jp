---
title: '&lt;filesystem&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 819c91e707e50a190aa58eda62f8e07f3451b033
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240724"
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 演算子

演算子は、2 つのパスの構文を文字列として比較します。 使用して、 `equivalent` 2 つのパス (たとえば、相対パスと絶対パス) が同じファイルまたはディスク上のディレクトリを参照してくださいかどうかを判断する関数。

詳細については、「[ファイル システムのナビゲーション](../standard-library/file-system-navigation.md)」を参照してください。

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

left.native() == right.native() が返されます。

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

!(left == right) が返されます。

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

left.native() < right.native() が返されます。

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

!(right \< left) が返されます。

## <a name="operator"></a>operator>

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

right \< left が返されます。

## <a name="operator"></a>operator>=

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

!(left < right) が返されます。

## <a name="operator"></a>operator/

```cpp
path operator/(const path& left, const path& right);
```

この関数は、次のコードを実行します。

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>operator<<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

os << pval.string\<Elem, Traits>() が返されます。

## <a name="operator"></a>operator>>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

この関数は、次のコードを実行します。

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```
