---
title: sub_match クラス
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 776dfe67367b932435f76af94880111cad61341d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685843"
---
# <a name="sub_match-class"></a>sub_match クラス

サブマッチを記述します。

## <a name="syntax"></a>構文

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>パラメーター

*Bidit* \
サブマッチの反復子の型。

## <a name="remarks"></a>Remarks

クラステンプレートは、 [regex_match](../standard-library/regex-functions.md#regex_match)または[regex_search](../standard-library/regex-functions.md#regex_search)への呼び出しでキャプチャグループと一致した文字のシーケンスを指定するオブジェクトを表します。 [match_results Class](../standard-library/match-results-class.md) 型のオブジェクトは、検索に使用された正規表現内のキャプチャ グループごとに 1 つずつ、これらのオブジェクトの配列を保持します。

キャプチャ グループがオブジェクトのデータ メンバーと一致しなかった場合は、 `matched` が false を保持し、2 つの反復子の `first` と `second` (ベース `std::pair`から継承) が等しくなります。 キャプチャ グループが一致した場合は、 `matched` が true を保持し、反復子 `first` がキャプチャ グループと一致したターゲット シーケンスの最初の文字を指し、反復子 `second` がキャプチャ グループと一致したターゲット シーケンスの最後の文字の 1 つ先の位置を指します。 長さ 0 の一致の場合は、メンバー `matched` が true を保持し、2 つの反復子が等しくなり、両方が一致した位置を指します。

長さ 0 の一致は、キャプチャ グループが 1 つのアサーションのみまたは 0 回の繰り返しが許可される 1 つの繰り返しのみで構成されている場合に発生します。 (例:

"^" は、ターゲット シーケンス "a" と一致します。キャプチャ グループ 0 に対応する `sub_match` オブジェクトは、両方がシーケンスの最初の文字を指す反復子を保持します。

"b(a*)b" は、ターゲット シーケンス "bb" と一致します。キャプチャ グループ 1 に対応する `sub_match` オブジェクトは、両方がシーケンスの 2 つ目の文字を指す反復子を保持します。

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[difference_type](#difference_type)|反復子の型の相違点。|
|[Iterator](#iterator)|反復子の型。|
|[value_type](#value_type)|要素の型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[compare](#compare)|サブマッチをシーケンスと比較します。|
|[length](#length)|サブマッチの長さを返します。|
|[付ける](#matched)|一致が成功したかどうかを示します。|
|[str](#str)|サブマッチを文字列に変換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|サブマッチを文字列にキャストします。|

## <a name="example"></a>例

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<regex>

**名前空間:** std

## <a name="compare"></a>  sub_match::compare

サブマッチをシーケンスと比較します。

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>パラメーター

*右*\
比較するサブマッチ。

*str* \
比較対象の文字列。

*ptr* \
null で終わる比較対象のシーケンス。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、一致するシーケンス `[first, second)` と一致したシーケンス `[right.first, right.second)` とを比較します。 2 つ目のメンバー関数は、一致するシーケンス `[first, second)` と文字シーケンス `[right.begin(), right.end())` とを比較します。 3 つ目のメンバー関数は、一致するシーケンス `[first, second)` と文字シーケンス `[right, right + std::char_traits<value_type>::length(right))` とを比較します。

各関数から返される値は次のとおりです。

負の値。一致するシーケンス内の最初に異なる値が、オペランド シーケンス内の対応する要素よりも小さい場合 (`std::char_traits<value_type>::compare` で判断)、または両者のプレフィックスが共通していても、ターゲット シーケンスの方が長い場合は、負の値が返されます。

ゼロ。両者の要素がすべて等しく、長さも同じである場合は、ゼロが返されます。

正の値。それ以外の場合は、正の値が返されます。

## <a name="difference_type"></a>  sub_match::difference_type

反復子の型の相違点。

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

typedef は、 `iterator_traits<BidIt>::difference_type`のシノニムです。

## <a name="iterator"></a>  sub_match::iterator

反復子の型。

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Remarks

この typedef は、テンプレート型引数 `Bidit` のシノニムです。

## <a name="length"></a>  sub_match::length

サブマッチの長さを返します。

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Remarks

メンバー関数は、一致するシーケンスの長さを返します。または、一致するシーケンスが存在しない場合、0 を返します。

## <a name="matched"></a>  sub_match::matched

一致が成功したかどうかを示します。

```cpp
bool matched;
```

### <a name="remarks"></a>Remarks

メンバーは、`*this` に関連付けられたキャプチャグループが正規表現の一致の一部であった場合にのみ**true**を保持します。

## <a name="op_basic_string_lt_value_type_gt"></a>  sub_match::operator basic_string&lt;value_type&gt;

サブマッチを文字列にキャストします。

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Remarks

このメンバー演算子は、`str()` を返します。

## <a name="str"></a>  sub_match::str

サブマッチを文字列に変換します。

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、 `basic_string<value_type>(first, second)`を返します。

## <a name="value_type"></a>  sub_match::value_type

要素の型。

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Remarks

typedef は、 `iterator_traits<BidIt>::value_type`のシノニムです。

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
