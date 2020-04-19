---
title: '&lt;string_view&gt; 演算子'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 699b1f1bddeb71ecbf03297d162a7e45ebd39609
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127739"
---
# <a name="ltstring_viewgt-operators"></a>&lt;string_view&gt; 演算子

これらの演算子を使用すると、暗黙的な変換が提供される2つの string_view オブジェクト、string_view とその他の文字列オブジェクト ( [std:: string](basic-string-class.md)、 **char\*** など) を比較できます。 

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[オペレーター "" sv](#op_sv)|

## <a name="op_neq"></a>operator! =

演算子の左側のオブジェクトが右側のオブジェクトと等しくないかどうかを調べます。

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左側のオブジェクトが右側のオブジェクトと等しく辞書式ない場合は**true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

*Convertible_string_type*からもう一方の側の string_view への暗黙的な変換が存在する必要があります。 

比較は、文字シーケンスのペアの辞書式の比較に基づいています。 同じ数の要素を持ち、要素がすべて等しい場合、2つのオブジェクトは等しくなります。 それ以外の場合は等しくありません。

## <a name="op_eq_eq"></a>operator = =

演算子の左辺のオブジェクトが右辺のオブジェクトと等しいかどうかを調べます。

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左側のオブジェクトが右側のオブジェクトと辞書式等しい場合は**true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

*Convertible_string_type*からもう一方の側の string_view への暗黙的な変換が存在する必要があります。 

比較は、文字シーケンスのペアの辞書式の比較に基づいています。 同じ数の要素を持ち、要素がすべて等しい場合、2つのオブジェクトは等しくなります。


## <a name="op_lt"></a> 演算子&lt;

演算子の左側のオブジェクトが右側のオブジェクトより小さいかどうかをテストし sidestring_view
```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左側のオブジェクトが右側のオブジェクトよりも辞書式小さい場合は**true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

*Convertible_string_type*からもう一方の側の string_view への暗黙的な変換が存在する必要があります。 

比較は、文字シーケンスのペアの辞書式の比較に基づいています。 最初の等しくない文字ペアが見つかった場合は、その比較の結果が返されます。 等しくない文字が見つからなくても、1つのシーケンスが短い場合は、短いシーケンスが長い方よりも小さくなります。 言い換えると、"cat" は "猫" よりも小さくなります。

### <a name="example"></a>例

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="op_lt_eq"></a>演算子&lt;=

演算子の左側のオブジェクトが右側のオブジェクト以下かどうかを調べます。

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左側のオブジェクトが右側のオブジェクト以下である場合は**true**を辞書式します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

「 [Operator&lt;](#op_lt)」を参照してください。

## <a name="op_lt_lt"></a>演算子&lt;&lt;

String_view を出力ストリームに書き込みます。

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>パラメーター

*Ostr*\
書き込み先の出力ストリーム。

*Str*\
出力ストリームに入力する string_view。

### <a name="return-value"></a>戻り値

書き込み先の出力ストリーム。

### <a name="remarks"></a>解説

この演算子を使用して、string_view の内容を出力ストリームに挿入します。たとえば、 [std:: cout](iostream.md#cout)を使用します。

## <a name="op_gt"></a> 演算子&gt;

演算子の左側のオブジェクトが右側のオブジェクトより大きいかどうかを調べます。

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺のオブジェクトが右辺の string_view オブジェクトよりも大きい場合は**true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

「 [Operator&lt;](#op_lt)」を参照してください。

## <a name="op_gt_eq"></a>演算子&gt;=

演算子の左側のオブジェクトが右側のオブジェクト以上であるかどうかを調べます。

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

*右*\
比較する `basic_string_view` 変換可能な文字列型または型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左側のオブジェクトが右側のオブジェクト以上で辞書式場合は**true**を指定します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

「 [Operator&lt;](#op_lt)」を参照してください。

## <a name="op_sv"></a>演算子 "" sv (string_view リテラル)

文字列リテラルから string_view を構築します。 名前空間 `std::literals::string_view_literals`が必要です。 

### <a name="example"></a>例

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>参照

[\<string_view >](../standard-library/string-view.md)
