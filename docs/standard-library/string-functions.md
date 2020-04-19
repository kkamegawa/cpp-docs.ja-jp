---
title: '&lt;string&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 828aeb975178850f5c0a7ea3b7e982bbadd6e7c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455608"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 関数

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

入力ストリームから文字列を行単位で抽出します。

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>パラメーター

*is*\
文字列の抽出元となる入力ストリーム。

*引数*\
入力ストリームから抽出した文字の読み込み先となる文字列。

*delim*\
行の区切り記号。

### <a name="return-value"></a>戻り値

入力ストリーム*が*です。

### <a name="remarks"></a>Remarks

抽出文字をとして`(1)`マークされた関数シグネチャのペアは、 *delim*が見つかるまで*str*に格納*さ*れます。

`(2)`としてマークされた関数シグネチャのペアは、既定の行区切り記号として改行を使用し、 **getline**(`is`, `str`, `is`として動作します。 `widen`(' `\n`')) として動作します。

各ペアの 2 つ目の関数では、1 つ目の関数と同様に、[右辺値参照](../cpp/lvalues-and-rvalues-visual-cpp.md)がサポートされます。

抽出は、次のいずれかが発生したときに停止します。

- ファイルの終端で *、の内部*状態フラグがに`ios_base::eofbit`設定されている場合。

- 関数が `delim` と等しい要素を抽出した場合。このとき、抽出された要素が制御対象シーケンスに戻されたり、追加されたりすることはありません。

- 関数が[max_size](../standard-library/basic-string-class.md#max_size)要素`str.`を抽出した後 *、の内部*状態フラグがに`ios_base::failbit`設定されます。

- 前に示した以外のエラーが発生した場合、内部状態フラグ*は*に設定されます。`ios_base::badbit`

内部状態フラグについては、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

関数が要素を抽出しなかった場合 *、の内部*状態フラグはに`ios_base::failbit`設定されます。 いずれの場合も`getline` 、*は*を返します。

例外がスローされた場合、*は*になり、 *str*は有効な状態のままになります。

### <a name="example"></a>例

次のコードは、2 つのモードの `getline()` を示しています。1 つ目は既定の区切り文字 (改行文字)、2 つ目は区切り文字として空白文字を使用しています。 また、while ループの終了を制御するために、ファイル終端文字 (Ctrl + Z キー) を使用しています。 この文字により、内部状態フラグ `cin` が `eofbit` に設定されます。2 つ目の while ループを正常に動作させるには、このフラグを [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) でクリアする必要があります。

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a>  stod

文字シーケンスを**倍精度浮動小数点**型に変換します。

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|

### <a name="return-value"></a>戻り値

**Double**値。

### <a name="remarks"></a>Remarks

関数は、を`strtod( str.c_str(), _Eptr)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**double**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stof"></a>  stof

文字シーケンスを float に変換します。

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|

### <a name="return-value"></a>戻り値

浮動小数点数値。

### <a name="remarks"></a>Remarks

関数は、を`strtof( str.c_str(), _Eptr)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**float**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stoi"></a>  stoi

文字シーケンスを integer に変換します。

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>戻り値

整数値。

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|値が返されるときに、最初の未変換文字のインデックスが格納されます。|
|*base*|使用する基数。|

### <a name="remarks"></a>Remarks

関数`stoi`は、 *str*内の文字のシーケンスを**int**型の値に変換し、その値を返します。 たとえば、文字シーケンス "10" を渡した場合、`stoi` によって返される値は整数 10 です。

1 バイト文字に対しては、`stoi` は `strtol` の形式で呼び出された場合の `strtol( str.c_str(), _Eptr, idx)` と同様に動作します。`_Eptr` は関数の内部オブジェクトです。ワイド文字に対しては、類似した `wcstol` の形式で呼び出された場合の `wcstol(Str.c_str(), _Eptr, idx)` と同様に動作します。 詳細については、「[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)」を参照してください。

の`str.c_str() == *_Eptr`場合`stoi` 、型`invalid_argument`のオブジェクトをスローします。 このような呼び出しによっ`errno`てが設定される場合、または戻り値を**int**型のオブジェクトとして表すことが`out_of_range`できない場合は、型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr - str.c_str()`関数`*idx`はをに格納します。

## <a name="stol"></a>  stol

文字シーケンスを**long**に変換します。

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|
|*base*|使用する基数。|

### <a name="return-value"></a>戻り値

長整数値。

### <a name="remarks"></a>Remarks

関数は、を`strtol( str.c_str(), _Eptr, idx)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**long**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stold"></a>  stold

文字シーケンスを**long double**に変換します。

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|

### <a name="return-value"></a>戻り値

**Long double**値。

### <a name="remarks"></a>Remarks

関数は、を`strtold( str.c_str(), _Eptr)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**long double**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stoll"></a>  stoll

文字シーケンスを**long 型**に変換します。

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|
|*base*|使用する基数。|

### <a name="return-value"></a>戻り値

**Long 型**の値。

### <a name="remarks"></a>Remarks

関数は、を`strtoll( str.c_str(), _Eptr, idx)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**long long**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stoul"></a>  stoul

文字シーケンスを unsigned long に変換します。

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|
|*base*|使用する基数。|

### <a name="return-value"></a>戻り値

unsigned long 整数値。

### <a name="remarks"></a>Remarks

関数は、を`strtoul( str.c_str(), _Eptr, idx)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**unsigned long**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="stoull"></a>  stoull

文字シーケンスを**unsigned long long 型**に変換します。

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*str*|変換する文字シーケンス。|
|*idx*|最初の未変換文字のインデックス値。|
|*base*|使用する基数。|

### <a name="return-value"></a>戻り値

**Unsigned long long 型**の値です。

### <a name="remarks"></a>Remarks

関数は、を`strtoull( str.c_str(), _Eptr, idx)`呼び出した場合`_Eptr`と同様に、str `val`内の要素のシーケンスを**unsigned long**型の値に変換します。は関数の内部オブジェクトです。 ` str.c_str() == *_Eptr` の場合、`invalid_argument` 型のオブジェクトをスローします。 このような呼び出しによって `errno` が設定される場合、`out_of_range` 型のオブジェクトをスローします。 それ以外の場合、 *idx*が null ポインターでない場合、 `*_Eptr -  str.c_str()`関数`*idx`はを`val`格納し、を返します。

## <a name="swap"></a>  swap

2 つの文字列の、文字の配列を交換します。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左側*\
もう一方の文字列と要素を交換する 1 つの文字列。

*そうです*\
最初の文字列と要素を交換するもう一方の文字列。

### <a name="remarks"></a>Remarks

このテンプレート関数は、特化されたメンバー関数を*左から*実行します。[スワップ](../standard-library/basic-string-class.md#swap)(*right*) 文字列の場合は、複雑さが一定であることを保証します。

### <a name="example"></a>例

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a>  to_string

値を `string` に変換します。

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Val*|変換する値。|

### <a name="return-value"></a>戻り値

値を表す `string` 値。

### <a name="remarks"></a>Remarks

関数は、を呼び出し`sprintf(Buf, Fmt, Val)`た場合と同様に、関数内部の`Buf`配列オブジェクトに格納されている要素の`Fmt`シーケンスに*Val*を変換します。ここで、は

- `"%d"`の`Val`型が**int**の場合

- `"%u"`の`Val`型が**unsigned int**の場合

- `"%ld"`の`Val`型が**long**の場合

- `"%lu"`に`Val` **unsigned long**型がある場合

- `"%lld"`が`Val` **long long**型の場合

- `"%llu"`に`Val` **unsigned long long**型がある場合

- `"%f"`の`Val`型が**float**または**double**の場合

- `"%Lf"`が`Val` **long double**型の場合

`string(Buf)` が返されます。

## <a name="to_wstring"></a>  to_wstring

値をワイド文字列に変換します。

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|`Val`|変換する値。|

### <a name="return-value"></a>戻り値

値を表すワイド文字列。

### <a name="remarks"></a>Remarks

関数は `Val` を呼び出すように、`Buf` を関数内部の配列オブジェクト `swprintf(Buf, Len, Fmt, Val)` に格納された要素シーケンスに変換します。ここで、`Fmt` は

- `L"%d"`の`Val`型が**int**の場合

- `L"%u"`の`Val`型が**unsigned int**の場合

- `L"%ld"`の`Val`型が**long**の場合

- `L"%lu"`に`Val` **unsigned long**型がある場合

- `L"%lld"`が`Val` **long long**型の場合

- `L"%llu"`に`Val` **unsigned long long**型がある場合

- `L"%f"`の`Val`型が**float**または**double**の場合

- `L"%Lf"`が`Val` **long double**型の場合

`wstring(Buf)` が返されます。

## <a name="see-also"></a>関連項目

[\<string>](../standard-library/string.md)
