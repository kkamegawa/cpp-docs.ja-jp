---
title: basic_regex クラス
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 45776754bd0854aeb85382eda95891a6832ca09e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689962"
---
# <a name="basic_regex-class"></a>basic_regex クラス

正規表現をラップします。

## <a name="syntax"></a>構文

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>パラメーター

*Elem* \
一致させる要素の型。

*RXtraits* \
要素の特徴 (traits) クラス。

## <a name="remarks"></a>Remarks

クラステンプレートは、正規表現を保持するオブジェクトを表します。 このクラステンプレートのオブジェクトは、正規表現に一致するテキストを検索するために、適切なテキスト文字列引数と共にテンプレート関数[regex_match](../standard-library/regex-functions.md#regex_match)、 [regex_search](../standard-library/regex-functions.md#regex_search)、および[regex_replace](../standard-library/regex-functions.md#regex_replace)に渡すことができます。 このクラステンプレートの特殊化は2つあります。 **char**型の要素の型定義[regex](../standard-library/regex-typedefs.md#regex)と、 **wchar_t**型の要素の[wregex](../standard-library/regex-typedefs.md#wregex)です。

テンプレート引数*RXtraits*は、クラステンプレートがサポートする正規表現の構文のさまざまな重要なプロパティについて説明します。 これらの正規表現の特徴を指定するクラスは、 [Regex_traits class](../standard-library/regex-traits-class.md)型のオブジェクトと同じ外部インターフェイスを持つ必要があります。

一部の関数は、正規表現を定義するオペランド シーケンスを受け取ります。 その場合、オペランド シーケンスは次のような方法で指定できます。

`ptr`--`ptr` (null ポインターではない) で始まる null で終わるシーケンス ( **char**型の*Elem*の場合は C 文字列など)。終端の要素は `value_type()` 値であり、オペランドシーケンスの一部ではありません

`ptr`、`count` : `count` (null ポインター以外) で始まる `ptr` 個の要素のシーケンスとして。

`str` : `basic_string` オブジェクト `str` によって指定されたシーケンスとして。

`first`、`last` : `first` と `last` の 2 つの反復子で区切られた範囲 `[first, last)` 内の要素のシーケンスとして。

`right` : `basic_regex` オブジェクト `right` として。

これらのメンバー関数は、 *RXtraits*型で記述されているものに加えて、正規表現の解釈に関するさまざまなオプションを指定する `flags` 引数も受け取ります。

### <a name="members"></a>メンバー

|メンバー|既定値|
|-|-|
|public static const flag_type icase|regex_constants:: icase|
|public static const flag_type nosubs|regex_constants:: nosubs|
|public static const flag_type optimize|regex_constants:: optimize|
|public static const flag_type collate|regex_constants:: collate|
|public static const flag_type ECMAScript|regex_constants:: ECMAScript|
|public static const flag_type basic|regex_constants:: basic|
|public static const flag_type extended|regex_constants:: extended|
|public static const flag_type awk|regex_constants:: awk|
|public static const flag_type grep|regex_constants:: grep|
|public static const flag_type egrep|regex_constants:: egrep|
|プライベート RXtraits の特徴||

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_regex](#basic_regex)|正規表現オブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[flag_type](#flag_type)|構文オプション フラグの型です。|
|[locale_type](#locale_type)|格納されているロケール オブジェクトの型。|
|[value_type](#value_type)|要素型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[assign](#assign)|値を正規表現オブジェクトに代入します。|
|[flags](#flags)|構文のオプション フラグを返します。|
|[getloc](#getloc)|格納されているロケール オブジェクトを返します。|
|[imbue](#imbue)|格納されているロケール オブジェクトを変更します。|
|[mark_count](#mark_count)|一致した部分式の数を返します。|
|[swap](#swap)|2 つの正規表現オブジェクトを交換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|値を正規表現オブジェクトに代入します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<regex>

**名前空間:** std

## <a name="example"></a>例

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="assign"></a>  basic_regex::assign

値を正規表現オブジェクトに代入します。

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>パラメーター

*Sttraits* \
文字列ソースの特徴 (traits) クラス。

*Stalloc* \
文字列ソースのアロケーター クラス。

*初期化*\
範囲ソースの入力反復子の型。

*右*\
コピーする Regex ソース。

*ptr* \
コピーするシーケンスの先頭を指すポインター。

*フラグ*\
コピー中に追加する構文オプション フラグ。

*len/TD >* \
コピーするシーケンスの長さ。

*str* \
コピーする文字列。

*最初*の \
コピーするシーケンスの最初。

*最後*の \
コピーするシーケンスの最後。

*IList* \
コピーする initializer_list。

### <a name="remarks"></a>Remarks

いずれのメンバー関数も、`*this` が保持している正規表現を、オペランド シーケンスが保持している正規表現に置き換えて、`*this` を返します。

## <a name="basic_regex"></a>  basic_regex::basic_regex

正規表現オブジェクトを構築します。

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>パラメーター

*Sttraits* \
文字列ソースの特徴 (traits) クラス。

*Stalloc* \
文字列ソースのアロケーター クラス。

*初期化*\
範囲ソースの入力反復子の型。

*右*\
コピーする Regex ソース。

*ptr* \
コピーするシーケンスの先頭を指すポインター。

*フラグ*\
コピー中に追加する構文オプション フラグ。

*len/TD >* \
コピーするシーケンスの長さ。

*str* \
コピーする文字列。

*最初*の \
コピーするシーケンスの最初。

*最後*の \
コピーするシーケンスの最後。

*IList* \
コピーする initializer_list。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、既定で構築される、`RXtraits` 型のオブジェクトを格納します。

1 つ目のコンストラクターは、空の `basic_regex` オブジェクトを構築します。 それ以外のコンストラクターは、オペランド シーケンスで記述された正規表現を保持する `basic_regex` オブジェクトを構築します。

空の `basic_regex` オブジェクトは、 [regex_match](../standard-library/regex-functions.md#regex_match)、 [regex_search](../standard-library/regex-functions.md#regex_search)、または[regex_replace](../standard-library/regex-functions.md#regex_replace)に渡されたときにどの文字シーケンスとも一致しません。

## <a name="flag_type"></a>  basic_regex::flag_type

構文オプション フラグの型です。

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Remarks

この型は [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type)のシノニムです。

## <a name="flags"></a>  basic_regex::flags

構文のオプション フラグを返します。

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、[basic_regex::assign](#assign) メンバー関数のうち直前に呼び出された関数に渡された `flag_type` 引数の値を返します。これに当たる呼び出しが行われていなかった場合は、コンストラクターに渡した値が返されます。

## <a name="getloc"></a>  basic_regex::getloc

格納されているロケール オブジェクトを返します。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Remarks

メンバー関数は `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()` を返します。

## <a name="imbue"></a>  basic_regex::imbue

格納されているロケール オブジェクトを変更します。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>パラメーター

*loc* \
格納するロケール オブジェクト。

### <a name="remarks"></a>Remarks

メンバー関数は `*this` を空にして、`traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)` を返します。

## <a name="locale_type"></a>  basic_regex::locale_type

格納されているロケール オブジェクトの型。

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Remarks

この型は [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type)のシノニムです。

## <a name="mark_count"></a>  basic_regex::mark_count

一致した部分式の数を返します。

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Remarks

メンバー関数は、正規表現のキャプチャ グループの数を返します。

## <a name="op_eq"></a>  basic_regex::operator=

値を正規表現オブジェクトに代入します。

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>パラメーター

*Sttraits* \
文字列ソースの特徴 (traits) クラス。

*Stalloc* \
文字列ソースのアロケーター クラス。

*右*\
コピーする Regex ソース。

*str* \
コピーする文字列。

### <a name="remarks"></a>Remarks

それぞれの演算子が、 `*this` に保持されている正規表現を、オペランド シーケンスで記述された正規表現に置き換えてから、 `*this`を返します。

## <a name="swap"></a>  basic_regex::swap

2 つの正規表現オブジェクトを交換します。

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>パラメーター

*右*\
交換する正規表現オブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` と*right*の間で正規表現を交換します。 一定時間に実行し、例外をスローしません。

## <a name="value_type"></a>  basic_regex::value_type

要素型。

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレートパラメーター *Elem*のシノニムです。

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match) \
[regex_search](../standard-library/regex-functions.md#regex_search) \
[regex_replace](../standard-library/regex-functions.md#regex_replace) \
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits クラス](../standard-library/regex-traits-class.md)
