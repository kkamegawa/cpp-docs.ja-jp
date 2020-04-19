---
title: '&lt;istream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689480"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

**Char**に特化された型 `basic_iostream`。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_iostream](../standard-library/basic-iostream-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="istream"></a>  istream

**Char**に特化された型 `basic_istream`。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_istream](../standard-library/basic-istream-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="wiostream"></a>  wiostream

**Wchar_t**に特化された型 `basic_iostream`。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_iostream](../standard-library/basic-iostream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="wistream"></a>  wistream

**Wchar_t**に特化された型 `basic_istream`。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_istream](../standard-library/basic-istream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="see-also"></a>関連項目

[\<istream>](../standard-library/istream.md)
