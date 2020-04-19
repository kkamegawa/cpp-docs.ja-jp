---
title: basic_string_view クラス
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 7a53a27e11088ab02f873613794d6799851ca373
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416181"
---
# <a name="basic_string_view-class"></a>basic_string_view クラス

クラステンプレート `basic_string_view<charT>` は C++ 17 で追加されました。このクラスは、関数がこれらの型をテンプレート化することなく、さまざまな関連のない文字列型を受け入れるための安全で効率的な方法として機能します。 クラスは、連続する文字データのシーケンスへの非所有ポインターと、シーケンス内の文字数を指定する長さを保持します。 シーケンスが null で終了したかどうかは想定されていません。

標準ライブラリでは、要素の型に基づいていくつかの特殊化が定義されています。

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

このドキュメントでは、"string_view" という用語は、一般にこれらの typedef を指します。

文字列データを読み取るために必要な最小限の共通インターフェイスについて説明する string_view です。 基になるデータへの const アクセスを提供します。コピーは行われません (`copy` 関数を除く)。 データには、任意の位置に null 値 (' \ 0 ') を含めることも、含まれないこともあります。 String_view には、オブジェクトの有効期間を制御することはできません。 基になる文字列データが有効であることを確認するのは、呼び出し元の責任です。

String_view 型のパラメーターを受け取る関数は、テンプレートに関数を作成したり、関数を文字列型の特定のサブセットに制約したりせずに、任意の文字列のような型を使用することができます。 唯一の要件は、文字列型から string_view への暗黙的な変換が存在することです。 すべての標準文字列型は、同じ要素型を含む string_view に暗黙的に変換できます。 つまり、`std::string` は `string_view` に変換可能ですが、`wstring_view`には変換できません。

次の例は、`wstring_view`型のパラメーターを受け取るテンプレート以外の関数 `f` を示しています。 `std::wstring`、`wchar_t*`、および `winrt::hstring`型の引数を使用して呼び出すことができます。

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>構文

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>パラメーター

*Chartype*\
String_view に格納されている文字の型。 標準C++ライブラリでは、このテンプレートの特殊化のために次の typedef が提供されています。
- **char**型の要素の[string_view](../standard-library/string-view-typedefs.md#string_view)
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)、 **wchar_t**
- **char16_t**の[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)
- **char32_t**の[u32string_view](../standard-library/string-view-typedefs.md#u32string_view) 。

*特徴*\
既定値は[char_traits](char-traits-struct.md)<*chartype*> です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_string_view](#basic_string_view)|空であるか、または他の文字列オブジェクトのデータの全部または一部、または C スタイルの文字配列を指す string_view を構築します。|

### <a name="typedefs"></a>Typedefs

|種類の名前。|説明|
|-|-|
|**const_iterator**|**Const**要素を読み取ることができるランダムアクセス反復子。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>メンバー演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|String_view または変換可能な文字列オブジェクトを別の string_view に割り当てます。|
|[operator\[\]](#op_at)|指定したインデックス位置にある要素を返します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[at](#at)|指定した位置にある要素に const_reference を返します。|
|[back](#back)|最後の要素に const_reference を返します。|
|[begin](#begin)|最初の要素を指す定数反復子を返します。 (string_views は変更できません)。|
|[cbegin](#cbegin)|[Begin](#begin)と同じです。|
|[cend](#cend)|最後の要素の1つ後ろを指す定数反復子を返します。|
|[copy](#copy)|ソース string_view 内のインデックス位置からターゲットの文字配列に、指定した文字数だけコピーします。 (推奨されません。 代わりに _Copy_s を使用してください。)|
|[_Copy_s](#_copy_s)|セキュリティで保護された CRT コピー関数。|
|[compare](#compare)|指定した string_view と string_view を比較して、等しいかどうか、または一方が他方よりも辞書式小さいかどうかを判断します。|
|[crbegin](#crbegin)|[Rbegin](#rbegin)と同じです。|
|[crend](#crend)|[Rend](#rend)と同じです。|
|[data](#data)|文字シーケンスに対して所有されていない生のポインターを返します。|
|[empty](#empty)|String_view に文字が含まれているかどうかをテストします。|
|[end](#end)|[Cend](#cend)と同じです。|
|[find](#find)|指定した文字シーケンスに一致する部分文字列の最初の出現を前方方向で検索します。|
|[find_first_not_of](#find_first_not_of)|指定した string_view または変換可能な文字列オブジェクトの要素ではない最初の文字を検索します。|
|[find_first_of](#find_first_of)|指定した string_view または変換可能な文字列オブジェクトの要素と一致する最初の文字を検索します。|
|[find_last_not_of](#find_last_not_of)|指定した string_view または変換可能な文字列オブジェクトの要素ではない最後の文字を検索します。|
|[find_last_of](#find_last_of)|指定した string_view または変換可能な文字列オブジェクトの要素である最後の文字を検索します。|
|[front](#front)|最初の要素に const_reference を返します。|
|[length](#length)|現在の要素数を返します。|
|[max_size](#max_size)|String_view に含めることができる最大文字数を返します。|
|[rbegin](#rbegin)|反転された string_view 内の最初の要素を指す定数反復子を返します。|
|[remove_prefix](#remove_prefix)|指定された数の要素でポインターを前方に移動します。|
|[remove_suffix](#remove_suffix)|返される要素の数を指定して、ビューのサイズを小さくします。|
|[rend](#rend)|反転された string_view 内の最後の要素の1つ後ろを指す定数反復子を返します。|
|[rfind](#rfind)|指定した文字シーケンスに一致する部分文字列が最初に見つかったときに、その string_view を逆方向に検索します。|
|[size](#size)|現在の要素数を返します。|
|[substr](#substr)|指定したインデックスを開始位置として、指定した長さの部分文字列を返します。|
|[スワップ](#swap)|2つの string_views の内容を交換します。|

## <a name="remarks"></a>コメント

関数が [max_size](#max_size) の要素よりも長いシーケンスを生成するように指示された場合、関数は [length_error](../standard-library/length-error-class.md) 型のオブジェクトをスローして長さエラーを報告します。

## <a name="requirements"></a>要件

[std: c++ 17](../build/reference/std-specify-language-standard-version.md)以降

**ヘッダー:** \<string_view >

**名前空間:** std

## <a name="at"></a>basic_string_view:: at

指定した0から始まるインデックス位置にある文字に const_reference を返します。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>パラメーター

*オフセット*\
参照される要素のインデックス。

### <a name="return-value"></a>戻り値

パラメーターインデックスによって指定された位置にある文字への const_reference。

### <a name="remarks"></a>コメント

最初の要素は0のインデックスを持ち、次の要素は正の整数で連続してインデックスが付けられます。これにより、長さ*n*の string_view には、n *-* 1 という数値でインデックス付けされた*n*番目の要素が含まれるようになります。 **で**は、[演算子\[\]](#op_at)とは異なり、無効なインデックスに対して例外がスローされます。 

一般に、`std::vector` や string_view**などのシーケンス**を使用しないことをお勧めします。 シーケンスに渡された無効なインデックスは、開発中に検出および修正する必要のある論理エラーです。 プログラムがインデックスが有効であることを確実に特定できない場合は、() でを呼び出さずにテストし、無頓着プログラミングに対する防御のために例外に依存する必要があります。

詳細については、「 [basic_string_view:: operator\[\]](#op_at) 」を参照してください。

### <a name="example"></a>例

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="back"></a>basic_string_view:: back

最後の要素に const_reference を返します。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>戻り値

String_view 内の最後の要素への const_reference。

### <a name="remarks"></a>コメント

String_view が空の場合、例外をスローします。

たとえば、`remove_suffix`を呼び出すことによって string_view が変更された後、この関数によって返される要素は、基になるデータの最後の要素ではなくなります。

### <a name="example"></a>例

C 文字列リテラルを使用して構築された string_view には終端の null は含まれないため、次の例では `back` は ' p ' を返し、' \ 0 ' は返しません。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

埋め込み null は、その他の文字として扱われます。

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>basic_string_view:: basic_string_view

String_view を構築します。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>パラメーター

*str*\
文字値へのポインター。

*len*\
ビューに含める文字数。

## <a name="remarks"></a>コメント

グラフ * パラメーターを持つコンストラクターでは、入力が null で終わることが想定されていますが、終端の null は string_view に含まれていません。

リテラルを使用して string_view を構築することもできます。 「 ["Sv" 演算子](string-view-operators.md#op_sv)」を参照してください。

## <a name="begin"></a>basic_string_view:: begin

[Cbegin](#cbegin)と同じです。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>戻り値
最初の要素をアドレス指定する const_iterator を返します。

## <a name="cbegin"></a>basic_string_view:: cbegin

範囲内の最初の要素を指す const_iterator を返します。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す**const**ランダムアクセス反復子。

## <a name="cend"></a>basic_string_view:: cend

範囲内の最後の要素の次の位置を指す const_iterator を返します。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>戻り値

範囲の末尾の次の位置を指し示す**const**ランダムアクセス反復子。

### <a name="remarks"></a>コメント

`cend` によって返された値は逆参照しないでください。

## <a name="compare"></a>basic_string_view:: compare

2つのオブジェクトが等しいかどうかを判断するために、指定した string_view (または変換可能な文字列型) を使用して大文字と小文字を区別する比較を実行します。 [\<の string_view > 演算子](string-view-operators.md)は、このメンバー関数を使用して比較を実行します。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>パラメーター

*strv*\
この string_view と比較する string_view。

*pos*\
この string_view の比較の開始位置を示すインデックス。

*num*\
この string_view から比較する最大文字数。

*num2*\
比較する*strv*の最大文字数。

*オフセット*\
比較を開始する*strv*のインデックス。

*ptr*\
この string_view と比較する C 文字列。

### <a name="return-value"></a>戻り値

この string_view が*strv*または*ptr*より小さい場合は、負の値です。2つの文字シーケンスが等しい場合は0。または、この string_view が*strv*または*ptr*より大きい場合は、正の値を指定します。

### <a name="remarks"></a>コメント

`compare` メンバー関数は、各文字シーケンスの全体または一部の比較を大文字と小文字を区別して実行します。 

### <a name="example"></a>例

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are" 
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are" 
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a) 
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="copy"></a>basic_string_view:: コピー

ソース string_view 内のインデックス位置からターゲットの文字配列に、指定した文字数だけコピーします。 代わりに、セキュリティで保護された関数[basic_string_view:: _Copy_s](#_copy_s)を使用することをお勧めします。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*ptr*\
要素のコピー先のターゲット文字配列。

*カウント*\
コピー元の string_view からコピーされる最大文字数。

*オフセット*\
コピーの作成元となるソース string_view 内の開始位置。

### <a name="return-value"></a>戻り値

実際にコピーされた文字数。

### <a name="remarks"></a>コメント

null 文字はコピーの末尾には追加されません。

## <a name="_copy_s"></a>basic_string_view:: _Copy_s

安全な CRT コピー関数を[コピー](#copy)の代わりに使用します。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>パラメーター

*dest*\
要素のコピー先のターゲット文字配列。

*dest_size*\
*Dest*のサイズ。

_*カウント*ソース文字列からコピーされる文字数の最大値。

*_Off*\
ソース文字列内のコピーの作成開始位置。

### <a name="return-value"></a>戻り値

実際にコピーされた文字数。

### <a name="remarks"></a>コメント

null 文字はコピーの末尾には追加されません。

詳細については、「 [c-runtime-ライブラリ/セキュリティ-機能-crt](../c-runtime-library/security-features-in-the-crt.md)」を参照してください。

## <a name="crbegin"></a>basic_string_view:: crbegin

反転された string_view 内の最初の要素を指す const_reverse_iterator を返します。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>戻り値

反転された string_view 内の最初の要素を指す const_reverse_iterator。 

## <a name="crend"></a>basic_string_view:: crend

[Rend](#rend)と同じです。 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>戻り値

反転された string_view の末尾を越える1つの const_reverse_iterator を返します。

## <a name="data"></a>basic_string_view::d ata

String_view の構築に使用されたオブジェクトの const 文字シーケンスへの、未処理の非所有ポインターを返します。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>戻り値

文字シーケンスの最初の要素への、const へのポインター。

### <a name="remarks"></a>コメント

ポインターは文字を変更できません。

String_view 文字のシーケンスは必ずしも null で終わるとは限りません。 Null 文字が追加されていないため、`data` の戻り値の型は有効な C 文字列ではありません。 Null 文字 ' \ 0 ' は string_view 型のオブジェクトでは特別な意味を持たず、他の文字と同様に string_view オブジェクトの一部である可能性があります。

## <a name="empty"></a>basic_string_view:: empty

String_view に文字が含まれているかどうかをテストします。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>戻り値

string_view オブジェクトに文字が含まれていない場合は**true** 。少なくとも1つの文字がある場合は**false** 。

### <a name="remarks"></a>コメント

このメンバー関数は、 [size](#size)() = = 0 に相当します。

## <a name="end"></a>basic_string_view:: end

最後の要素の1つ後ろを指すランダムアクセス const_iterator を返します。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>戻り値

最後の要素の1つ後ろを指すランダムアクセス const_iterator を返します。

### <a name="remarks"></a>コメント

`end` は、const_iterator が string_view の末尾に達したかどうかをテストするために使用されます。 `end` によって返された値は逆参照しないでください。

## <a name="find"></a>basic_string_view:: find

指定された文字シーケンスに一致する文字または部分文字列の最初の出現を前方方向に string_view 検索します。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*str*\
メンバー関数が検索する string_view。

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の開始位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
最初の文字から順に数えて、 *ptr*の文字数。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

## <a name="find_first_not_of"></a>basic_string_view:: find_first_not_of

指定した string_view または変換可能な文字列オブジェクトの要素ではない最初の文字を検索します。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*str*\
メンバー関数が検索する string_view。

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の開始位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
メンバー関数が検索する C 文字列で、最初の文字から順にカウントされる文字数。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

## <a name="find_first_of"></a>basic_string_view:: find_first_of

指定した string_view の任意の要素と一致する最初の文字を検索します。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の開始位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
メンバー関数が検索する C 文字列で、最初の文字から順にカウントされる文字数。

*str*\
メンバー関数が検索する string_view。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

## <a name="find_last_not_of"></a>basic_string_view:: find_last_not_of

指定した string_view の要素ではない最後の文字を検索します。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*str*\
メンバー関数が検索する string_view。

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の終了位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
*Ptr*内の最初の文字から順にカウントされる文字数。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `string_view::npos`。

## <a name="find_last_of"></a>basic_string_view:: find_last_of

指定した string_view の任意の要素と一致する最後の文字を検索します。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*str*\
メンバー関数が検索する string_view。

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の終了位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
メンバー関数が検索する C 文字列で、最初の文字から順にカウントされる文字数。

### <a name="return-value"></a>戻り値

成功した場合は検索する部分文字列の最後の文字のインデックス、それ以外の場合は `npos`。

## <a name="front"></a>basic_string_view:: front

最初の要素に const_reference を返します。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>戻り値

最初の要素に const_reference。

### <a name="remarks"></a>コメント

String_view が空の場合、例外をスローします。

## <a name="length"></a>basic_string_view:: length

現在の要素数を返します。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>コメント

このメンバー関数は [size](#size) と同じです。

## <a name="max_size"></a>basic_string_view:: max_size

String_view に含めることができる最大文字数を返します。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>戻り値

String_view に含めることができる最大文字数。

### <a name="remarks"></a>コメント

[Length_error](../standard-library/length-error-class.md)型の例外は、操作によって `max_size()`よりも長い長さの string_view が生成された場合にスローされます。

## <a name="op_eq"></a>basic_string_view:: operator =

String_view または変換可能な文字列オブジェクトを別の string_view に割り当てます。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>basic_string_view:: operator []

指定したインデックスを持つ文字への const_reference を提供します。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>パラメーター

*オフセット*\
参照される要素のインデックス。

### <a name="return-value"></a>戻り値

パラメーターインデックスによって指定された位置にある文字への const_reference。

### <a name="remarks"></a>コメント

最初の要素は0のインデックスを持ち、次の要素は正の整数で連続してインデックスが付けられます。これにより、長さ*n*の string_view には、 *n-1*という数値でインデックス付けされた*n*番目の要素が含まれるようになります。

`operator[]` は、string_view の要素に対する読み取りアクセスを提供[するために、のメンバー](#at)関数よりも高速です。

`operator[]` では、引数として渡されたインデックスが有効かどうかは確認されません。 無効なインデックスが `operator[]` に渡されると、未定義の動作が発生します。

基になる文字列データが所有オブジェクトによって変更または削除された場合、返される参照は無効になることがあります。

[\_反復子](../standard-library/iterator-debug-level.md)を使用してコンパイルするときに、\_レベルを1または2に設定\_デバッグすると、string_view の境界の外側にある要素にアクセスしようとすると、ランタイムエラーが発生します。 詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="rbegin"></a>basic_string_view:: rbegin

反転された string_view 内の最初の要素を指す定数反復子を返します。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>戻り値

反転された string_view 内の最初の要素を指すランダムアクセス反復子を返します。これは、対応する反転されていない string_view の最後の要素となるものです。

### <a name="remarks"></a>コメント

`rbegin` は、 [begin](#begin)が string_view で使用されるのと同様に、逆順の string_view と共に使用されます。 `rbegin` は、反復処理を逆に初期化するために使用できます。

## <a name="remove_prefix"></a>basic_string_view:: remove_prefix

指定された数の要素でポインターを前方に移動します。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>コメント

基になるデータを変更せずに残します。 String_view ポインターを n 個の要素順に移動し、プライベート `size` データメンバーを size-n に設定します。

## <a name="remove_suffix"></a>basic_string_view:: remove_suffix

返される要素の数を指定して、ビューのサイズを小さくします。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>コメント

基になるデータとポインターを変更せずに残します。 プライベート `size` データメンバーをサイズ-n に設定します。

## <a name="rend"></a>basic_string_view:: rend

反転された string_view 内の最後の要素の1つ後ろを指す定数反復子を返します。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>戻り値

反転された string_view 内の最後の要素の1つ後ろを指す、定数逆順ランダムアクセス反復子。

### <a name="remarks"></a>コメント

`rend` は、 [end](#end)が string_view で使用されるのと同様に、逆順の string_view と共に使用されます。 `rend` は、逆順反復子が string_view の末尾に達したかどうかをテストするために使用できます。 `rend` によって返された値は逆参照しないでください。

## <a name="rfind"></a>basic_string_view:: rfind

指定した文字シーケンスに一致する部分文字列の string_view を逆方向に検索します。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*Chval*\
メンバー関数が検索される文字値。

*オフセット*\
検索の開始位置を示すインデックス。

*ptr*\
メンバー関数の検索対象となる C 文字列。

*カウント*\
メンバー関数が検索する C 文字列で、最初の文字から順にカウントされる文字数。

*str*\
メンバー関数が検索する string_view。

### <a name="return-value"></a>戻り値

成功した場合は、部分文字列の最初の文字のインデックス。それ以外の場合は `npos`。

## <a name="size"></a>basic_string_view:: size

String_view 内の要素の数を返します。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>戻り値

String_view の長さ。

### <a name="remarks"></a>コメント

String_view では、`remove_prefix` や `remove_suffix`などの長さを変更できます。 これによって基になる文字列データが変更されることはないため、string_view のサイズは必ずしも基になるデータのサイズとは限りません。

## <a name="substr"></a>basic_string_view:: substr

指定した位置から、指定した文字数だけを表す string_view を返します。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>パラメーター

*オフセット*\
コピーの作成元の位置にある要素を検索するインデックス。既定値は0です。

*カウント*\
部分文字列に含める文字数 (存在する場合)。

### <a name="return-value"></a>戻り値

要素の指定したサブシーケンスを表す string_view オブジェクト。

## <a name="swap"></a>basic_string_view:: swap

2つの string_views を交換します。つまり、基になる文字列データへのポインターとサイズ値を交換します。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>パラメーター

*sv*\
ポインターとサイズの値をコピー先の string_view と交換するソース string_view。

## <a name="see-also"></a>参照

[\<string_view >](../standard-library/string-view.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
