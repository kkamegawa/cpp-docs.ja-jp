---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 3f1fb202692d09fa87eb775677e46e1c3f36dbad
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688948"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

割り当てられた配列オブジェクトに格納されているシーケンスの iostreams 操作をサポートする複数のクラステンプレートを定義します。 このようなシーケンスは、クラステンプレート[basic_string](../standard-library/basic-string-class.md)のオブジェクトとの間で簡単に変換できます。

## <a name="syntax"></a>構文

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*left*|`sstream` オブジェクトへの参照。|
|*right*|`sstream` オブジェクトへの参照。|

## <a name="remarks"></a>Remarks

`char *` 型のオブジェクトでは、ストリーミングに [\<strstream >](../standard-library/strstream.md) の機能を使用することができます。 ただし、\<strstream > は非推奨とされ、\<sstream > の使用が推奨されます。

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|**Char**テンプレートパラメーターに特殊化された `basic_istringstream` 型を作成します。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|**Char**テンプレートパラメーターに特殊化された `basic_ostringstream` 型を作成します。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|**Char**テンプレートパラメーターに特殊化された `basic_stringbuf` 型を作成します。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|**Char**テンプレートパラメーターに特殊化された `basic_stringstream` 型を作成します。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|**Wchar_t**テンプレートパラメーターに特殊化された `basic_istringstream` 型を作成します。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|**Wchar_t**テンプレートパラメーターに特殊化された `basic_ostringstream` 型を作成します。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|**Wchar_t**テンプレートパラメーターに特殊化された `basic_stringbuf` 型を作成します。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|**Wchar_t**テンプレートパラメーターに特殊化された `basic_stringstream` 型を作成します。|

### <a name="manipulators"></a>マニピュレーター

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|2 つの `sstream` オブジェクト間で値を交換します。|

### <a name="classes"></a>クラス

|インスタンス|説明|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|文字の特徴がクラス `Tr` によって決まる型 `Elem` の要素の、配列オブジェクトに格納されている要素のシーケンスとの間での転送を制御するストリーム バッファーについて説明します。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|要素とエンコードされたオブジェクトの抽出を制御するオブジェクトについて説明します。これは、< [basic_stringbuf](../standard-library/basic-stringbuf-class.md)クラスのストリームバッファー、**Elem**、 **Tr**、`Alloc` >、および `Elem` 型の要素を使用して、文字特性がによって決まります。クラス `Tr`、および要素がクラス `Alloc` のアロケーターによって割り当てられている。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|要素とエンコードされたオブジェクトのストリームバッファーへの挿入を制御するオブジェクトを記述します。これは、要素とエンコードされたオブジェクトを `Elem` 型の要素と共に[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <**Elem**、 **Tr**、`Alloc` > のストリームバッファーに格納します。その文字特性は、クラス `Tr`、およびその要素がクラス `Alloc` のアロケーターによって割り当てられています。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを記述します。これは、 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)クラスのストリームバッファー、<**Elem**、 **Tr**、`Alloc` >、および型 `Elem` の要素を使用して、その文字特性がクラス `Tr` によって決定され、その要素は `Alloc` クラスのアロケーターによって割り当てられます。|

## <a name="requirements"></a>［要件］

- **ヘッダー:** \<sstream>

- **名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
