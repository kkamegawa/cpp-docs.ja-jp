---
title: basic_istream クラス
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 68c7f7ffa9c32c16654e57c8249348d74cc83a5b
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778516"
---
# <a name="basic_istream-class"></a>basic_istream クラス

`Char_T` 型の要素を含むストリーム バッファーからの要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを表します。この型は [char_type](../standard-library/basic-ios-class.md#char_type) とも呼ばれ、その文字特性は、[traits_type](../standard-library/basic-ios-class.md#traits_type) とも呼ばれるクラス *Tr* によって決定されます。

## <a name="syntax"></a>構文

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Remarks

[operator>>](#op_gt_gt) をオーバーロードするメンバー関数のほとんどは、書式設定された入力関数です。 これらは以下のパターンに従います。

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

その他のメンバー関数の多くは、書式が設定されていない入力関数です。 これらは以下のパターンに従います。

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

どちらの関数グループも、要素の抽出中にファイルの終わりに到達した場合に[`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` を呼び出します。

クラス `basic_istream<Char_T, Tr>` 格納されているオブジェクト。

- クラス[`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` の仮想パブリック基本オブジェクト。

- 最後の書式設定されていない入力操作の抽出カウント (前のコードで `count` と呼ばれます)。

## <a name="example"></a>例

入力ストリームの詳細は、[basic_ifstream クラス](../standard-library/basic-ifstream-class.md)の例を参照してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_istream](#basic_istream)|`basic_istream` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[gcount](#gcount)|書式設定されていない最後の入力中に読まれた文字数を返します。|
|[get](#get)|入力ストリームから 1 つ以上の文字を読み取ります。|
|[getline](#getline)|入力ストリームから行を読み取ります。|
|[ignore](#ignore)|複数の要素を、現在読み取った位置からスキップさせます。|
|[peek](#peek)|読み取る次の文字を返します。|
|[putback](#putback)|ストリームに指定された文字を配置します。|
|[read](#read)|指定された数の文字をストリームから読み取り、配列に保存します。|
|[readsome](#readsome)|バッファーからのみ読み取ります。|
|[seekg](#seekg)|ストリームでの読み取り位置を移動させます。|
|[sentry](#sentry)|この入れ子になったクラスは、オブジェクトの宣言が書式設定された入力関数と書式設定されていない入力関数を構築するオブジェクトについて記述します。|
|[swap](#swap)|この `basic_istream` オブジェクトを、指定した `basic_istream` オブジェクト パラメーターと交換します。|
|[sync](#sync)|ストリームの関連付けられた入力デバイスをストリームのバッファーと同期します。|
|[tellg](#tellg)|ストリーム内の現在の読み取り位置を報告します。|
|[unget](#unget)|最後に読み取った文字をストリームに戻します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator>>](#op_gt_gt)|入力ストリームで関数を呼び出すか、または入力ストリームから書式設定されたデータを読み取ります。|
|[operator=](#op_eq)|演算子の右辺の `basic_istream` をこのオブジェクトに代入します。 これは、コピーを残さない `rvalue` 参照を含む移動代入です。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<istream>

**名前空間:** std

## <a name="basic_istream"></a>  basic_istream::basic_istream

`basic_istream` 型のオブジェクトを構築します。

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>パラメーター

*strbuf* \
[basic_streambuf](../standard-library/basic-streambuf-class.md) 型のオブジェクト。

*_Isstd* \
標準ストリームの場合は**true**です。それ以外の場合は**false**。

*右*\
コピーする `basic_istream` オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、 [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` を呼び出すことによって、基本クラスを初期化します。 ゼロも抽出カウントに格納されます。 この抽出数の詳細については、「 [Basic_istream クラス](../standard-library/basic-istream-class.md)の概要」の「解説」を参照してください。

2 番目のコンストラクターが `move(right)` を呼び出して基底クラスを初期化します。 また、抽出カウントに `right.gcount()` を格納し、* right * * の抽出カウントに0を格納します。

### <a name="example"></a>例

入力ストリームの詳細は、[basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) の例を参照してください。

## <a name="gcount"></a>  basic_istream::gcount

書式設定されていない最後の入力中に読まれた文字数を返します。

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>戻り値

抽出カウント。

### <a name="remarks"></a>Remarks

書式設定されていない文字を読み取るには、[basic_istream::get](#get) を使用します。

### <a name="example"></a>例

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="get"></a>  basic_istream::get

入力ストリームから 1 つ以上の文字を読み取ります。

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>パラメーター

*カウント*\
*strbuf* から読み取る文字の数。

*区切り記号*\
*カウント*の前に見つかった場合は、読み取りを終了する必要がある文字。

*str* \
書き込み先の文字列。

*Ch* \
取得する文字。

*strbuf* \
書き込み先のバッファー。

### <a name="return-value"></a>戻り値

get のパラメーターなしの形式は、整数またはファイルの終わりとして読み取られる要素を返します。 残りの形式はストリーム (* `this`) を返します。

### <a name="remarks"></a>Remarks

最初の書式設定されていない入力関数は、可能であれば `rdbuf->sbumpc` を返すことで、要素を抽出します。 それ以外の場合は `traits_type::`[ `eof`](../standard-library/char-traits-struct.md#eof)を返します。 関数が要素を抽出しなかった場合は、 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。

2 番目の関数は、同じ方法で [int_type](../standard-library/basic-ios-class.md#int_type) 要素 `meta` を抽出します。 @No__t_0 が `traits_type::eof` と比較される場合、関数は `setstate(failbit)` を呼び出します。 それ以外の場合は、`traits_type::`[ `to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` を*Ch*に格納します。 この関数は __* this__を返します。

3番目の関数は、`get(str, count, widen('\n'))` を返します。

4番目の関数は、`count - 1` 要素までを抽出し、 *str*から始まる配列に格納します。 これは格納する抽出した要素の後に常に `char_type` を格納します。 テストの順に抽出は停止します。

- ファイルの終わり。

- 関数が*区切り記号*と等しい要素を抽出した後。 この場合、要素は被制御シーケンスに戻されます。

- 関数が `count - 1` 要素を抽出した後。

関数が要素を抽出しなかった場合、`setstate(failbit)`. どのような場合でも、 __* this__が返されます。

5番目の関数は、`get(strbuf, widen('\n'))` を返します。

6 番目の関数は、要素を抽出し、それらを *strbuf* に挿入します。 抽出は、ファイルの終わりや、抽出されていない*区切り記号*と等しい要素で停止します。 また、挿入が失敗した場合または (キャッチされるが再スローされない) 例外をスローする場合は、対象の要素を抽出せずに停止します。 関数が要素を抽出しなかった場合、`setstate(failbit)`. いずれの場合も、関数は __* this__を返します。

### <a name="example"></a>例

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="getline"></a>  basic_istream::getline

入力ストリームから行を取得します。

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>パラメーター

*カウント*\
*strbuf* から読み取る文字の数。

*区切り記号*\
*カウント*の前に見つかった場合は、読み取りを終了する必要がある文字。

*str* \
書き込み先の文字列。

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

これらの書式設定されていない入力関数の1つ目は `getline(str, count, widen('\n'))` を返します。

2番目の関数は `count - 1` 要素までを抽出し、 *str*から始まる配列に格納します。 これは格納する抽出した要素の後に常に文字列終端文字を格納します。 テストの順に抽出は停止します。

- ファイルの終わり。

- 関数が*区切り記号*と等しい要素を抽出した後。 この場合、要素は戻されず、被制御シーケンスに追加されません。

- 関数が `count - 1` 要素を抽出した後。

関数が要素を抽出しなかった場合、または要素を `count - 1` 場合は、 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 どのような場合でも、 __* this__が返されます。

### <a name="example"></a>例

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="ignore"></a>  basic_istream::ignore

複数の要素を、現在読み取った位置からスキップさせます。

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>パラメーター

*カウント*\
現在の読み取り位置からスキップする要素の数。

*区切り記号*\
カウント前に検出された場合、`ignore` が返され、*区切り記号*の後にあるすべての要素を読み取ることができる要素。

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

書式設定されていない入力関数は、最大*数*の要素を抽出し、それらを破棄します。 ただし、 *count*が `numeric_limits<int>::max` の場合は、任意の大きさとして取得されます。 抽出は、ファイルの終わりまたは要素 `Ch` の早い段階で停止します。これにより `traits_type::`[ `to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` は、*区切り記号*(も抽出されます) と等しいかどうかを比較します。 この関数は __* this__を返します。

### <a name="example"></a>例

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="op_gt_gt"></a>basic \_istream:: operator > >

入力ストリームで関数を呼び出すか、または入力ストリームから書式設定されたデータを読み取ります。

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>パラメーター

*Pfn* \
関数ポインター。

*strbuf* \
`stream_buf` 型のオブジェクト。

*val* \
ストリームから読み取る値。

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

@No__t_0istream > ヘッダーでは、いくつかのグローバル抽出演算子も定義されています。 詳細については、「[operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt)」を参照してください。

最初のメンバー関数は、フォーム `istr >> ws` 式が[`ws`](../standard-library/istream-functions.md#ws) `(istr)` を呼び出すことを保証し、 __* this__を返します。 2番目と3番目の関数は、 [`hex`](../standard-library/ios-functions.md#hex)など、他のマニピュレーターも同様に動作することを保証します。 その他の関数は、書式設定された入力関数です。

関数:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

*strbuf*が null ポインターではない場合に要素を抽出し、 *strbuf*に挿入します。 抽出は、ファイルの終わりで停止します。 また、挿入が失敗した場合または (キャッチされるが再スローされない) 例外をスローする場合は、対象の要素を抽出せずに停止します。 関数が要素を抽出しなかった場合は、 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 いずれの場合も、関数は __* this__を返します。

関数:

```cpp
basic_istream& operator>>(bool& val);
```

[`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(`[ `getloc`](../standard-library/ios-base-class.md#getloc) `).`[ `get`](../standard-library/ios-base-class.md#getloc) [ `( InIt(` 0](../standard-library/basic-ios-class.md#rdbuf) 1 を呼び出すことによって、フィールドを抽出し、ブール値に変換します。 ここでは、`InIt` は[`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` として定義されています。 この関数は __* this__を返します。

各関数:

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

`use_facet<num_get<Char_T, InIt>(getloc).`[ `get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` を呼び出すことによって、フィールドを抽出し、数値に変換します。 ここでは、`InIt` が `istreambuf_iterator<Char_T, Tr>` として定義され、 *val*の型が**long**、 **unsigned long**、または**void** <strong>\*</strong>必要に応じて指定されています。

変換後の値を*val*の型として表すことができない場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 いずれの場合も、関数は __* this__を返します。

各関数:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

`use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` を呼び出してフィールドを抽出し、数値に変換します。 ここでは、`InIt` は `istreambuf_iterator<Char_T, Tr>` として定義され、 *val*は必要に応じて**double**または**long double**型になります。

変換後の値を*val*の型として表すことができない場合、関数は `setstate(failbit)` を呼び出します。 どのような場合でも、 __* this__が返されます。

### <a name="example"></a>例

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="op_eq"></a>  basic_istream::operator=

演算子の右辺の `basic_istream` をこのオブジェクトに代入します。 これは、コピーを残さない `rvalue` 参照を含む移動代入です。

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>パラメーター

*右*\
`basic_ifstream` オブジェクトへの `rvalue` 参照。

### <a name="return-value"></a>戻り値

__* This__を返します。

### <a name="remarks"></a>Remarks

このメンバー演算子は `swap(right)` を呼び出します。

## <a name="peek"></a>  basic_istream::peek

読み取る次の文字を返します。

```cpp
int_type peek();
```

### <a name="return-value"></a>戻り値

読み取る次の文字。

### <a name="remarks"></a>Remarks

書式設定されていない入力関数は、可能であれば `rdbuf->`[ `sgetc`](../standard-library/basic-streambuf-class.md#sgetc)を返すことで、要素を抽出します。 それ以外の場合は `traits_type::`[ `eof`](../standard-library/char-traits-struct.md#eof)を返します。

### <a name="example"></a>例

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="putback"></a>  basic_istream::putback

ストリームに指定された文字を配置します。

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>パラメーター

*Ch* \
ストリームに戻す文字。

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

書式設定されていない[入力関数](../standard-library/basic-istream-class.md)は、可能であれば、 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->`[ `sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)を呼び出すことによって、 *Ch*を戻します。 @No__t_0 が null ポインターの場合、または `sputbackc` の呼び出しによって `traits_type::`[ `eof`](../standard-library/char-traits-struct.md#eof)が返された場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` を呼び出します。 どのような場合でも、 __* this__が返されます。

### <a name="example"></a>例

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="read"></a>  basic_istream::read

指定された数の文字をストリームから読み取り、配列に保存します。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*str* \
文字の読み取り先の配列。

*カウント*\
読み取る文字の数。

### <a name="return-value"></a>戻り値

ストリーム ( `*this`)。

### <a name="remarks"></a>Remarks

書式設定されていない入力関数は、最大*数*の要素を抽出し、 *str*から始まる配列に格納します。 抽出は、ファイルの終わりの早い段階で停止します。この場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 どのような場合でも、 __* this__が返されます。

### <a name="example"></a>例

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="readsome"></a>  basic_istream::readsome

指定した文字の値の数を読み取ります。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*str* \
`readsome` が読み取る文字を格納する配列。

*カウント*\
読み取る文字の数。

### <a name="return-value"></a>戻り値

実際に読み取った文字数 ( [`gcount`](#gcount))。

### <a name="remarks"></a>Remarks

この書式設定されていない入力関数は、入力ストリームから*数*個の要素を抽出し、配列*str*に格納します。

この関数は入力を待機しません。 使用できる任意のデータを読み取ります。

### <a name="example"></a>例

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="seekg"></a>  basic_istream::seekg

ストリームでの読み取り位置を移動させます。

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>パラメーター

*pos* \
読み取りポインターの移動先の絶対位置。

*オフ*\
読み取り*ポインターを相対的*に移動するオフセット。

*方法*\
[ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 列挙体のうちの 1 つ。

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は絶対シークを実行し、2 つ目のメンバー関数は相対シークを実行します。

> [!NOTE]
> 標準 C++ ではテキスト ファイルでの相対シークをサポートしていないため、2 つ目のメンバー関数をテキスト ファイルで使用しないでください。

[@No__t_1](../standard-library/basic-ios-class.md#fail)が false の場合、1つ目のメンバー関数は、一部の `pubseekpos` 一時オブジェクト `(pos)` に対して `newpos = `[ `rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->`[ `pos_type`](../standard-library/basic-streambuf-class.md#pubseekpos) `fail`0 を呼び出します。 @No__t_0 が false の場合、2番目の関数は `newpos = rdbuf->`[ `pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` を呼び出します。 どちらの場合も、`(off_type)newpos == (off_type)(-1)` (配置操作が失敗) すると、関数は `istr.`[ `setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 どちらの関数も __* this__を返します。

[@No__t_1](../standard-library/basic-ios-class.md#fail)が true の場合、メンバー関数は何も行いません。

### <a name="example"></a>例

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="sentry"></a>  basic_istream::sentry

この入れ子になったクラスは、オブジェクトの宣言が書式設定された入力関数と書式設定されていない入力関数を構築するオブジェクトについて記述します。

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Remarks

@No__t_0[ `good`](../standard-library/basic-ios-class.md#good)が true の場合、コンストラクターは次のようになります。

- @No__t_6 が null ポインターでない場合は、`_Istr.`[ `tie`](../standard-library/basic-ios-class.md#tie) `->`[ `flush`](../standard-library/basic-ostream-class.md#flush)を呼び出します。

- @No__t_3[ `flags`](../standard-library/ios-base-class.md#flags) [ ` & ` `skipws` が 0](../standard-library/ios-functions.md#skipws)以外の場合に[`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` を効果的に呼び出します。

このような準備の後、`_Istr.good` が false の場合、コンストラクターは `_Istr.`[ `setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` を呼び出します。 いずれの場合も、コンストラクターは、`_Istr.good` によって返された値を `status` に格納します。 後で `operator bool` を呼び出すと、この格納された値が配信されます。

## <a name="swap"></a>  basic_istream::swap

2 つの `basic_istream` オブジェクトの内容を交換します。

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>パラメーター

*右*\
`basic_istream` オブジェクトへの左辺値参照。

### <a name="remarks"></a>Remarks

このメンバー関数は[`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` を呼び出します。 また、抽出カウントを*右側*の抽出カウントと交換します。

## <a name="sync"></a>  basic_istream::sync

ストリームの関連付けられた入力デバイスをストリームのバッファーと同期します。

```cpp
int sync();
```

### <a name="return-value"></a>戻り値

[@No__t_1](../standard-library/basic-ios-class.md#rdbuf)が null ポインターの場合、この関数は-1 を返します。 それ以外の場合は `rdbuf->`[ `pubsync`](../standard-library/basic-streambuf-class.md#pubsync)を呼び出します。 この呼び出しで-1 が返された場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` を呼び出し、-1 を返します。 それ以外の場合、関数は 0 を返します。

## <a name="tellg"></a>  basic_istream::tellg

ストリーム内の現在の読み取り位置を報告します。

```cpp
pos_type tellg();
```

### <a name="return-value"></a>戻り値

ストリームの現在の位置。

### <a name="remarks"></a>Remarks

[@No__t_1](../standard-library/basic-ios-class.md#fail)が false の場合、メンバー関数は[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` `->` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)を返します。 それ以外の場合は、 `pos_type(-1)`を返します。

### <a name="example"></a>例

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="unget"></a>  basic_istream::unget

最後に読み取った文字をストリームに戻します。

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>戻り値

ストリーム ( __* this__)。

### <a name="remarks"></a>Remarks

書式設定されていない[入力関数](../standard-library/basic-istream-class.md)は、可能であれば、`rdbuf->`[ `sungetc`](../standard-library/basic-streambuf-class.md#sungetc)を呼び出すことによって、ストリーム内の前の要素を戻します。 [@No__t_1](../standard-library/basic-ios-class.md#rdbuf)が null ポインターの場合、または `sungetc` の呼び出しによって `traits_type::`[ `eof`](../standard-library/basic-ios-class.md#eof)が返された場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` を呼び出します。 どのような場合でも、 __* this__が返されます。

@No__t_0 が失敗する方法の詳細については、「 [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
