---
title: '&lt;ostream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687228"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedef

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

**Char で**特殊化された basic_ostream から型を作成し、 **char**に特化した `char_traits` ます。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ostream](../standard-library/basic-ostream-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="wostream"></a>  wostream

Wchar_t に特**化した**basic_ostream から、 **wchar_t**で特殊化された `char_traits` の型を作成します。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ostream](../standard-library/basic-ostream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="see-also"></a>関連項目

[\<ostream>](../standard-library/ostream.md)
