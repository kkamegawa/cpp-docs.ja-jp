---
title: basic_ios クラス
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: c22e048d01665deed83a9474525f414dfd874fe0
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524913"
---
# <a name="basicios-class"></a>basic_ios クラス

このテンプレート クラスは、テンプレート パラメーターに依存する、入力ストリーム([basic_istream](../standard-library/basic-istream-class.md) テンプレート クラス) と出力ストリーム ([basic_ostream](../standard-library/basic-ostream-class.md) テンプレート クラス) の両方に共通のストレージとメンバー関数を表します。 (クラス [ios_base](../standard-library/ios-base-class.md) は、テンプレート パラメーターに依存しない、共通の要素を記述します。)クラスのオブジェクト**basic_ios\<class Elem, class Traits >** 型の要素を含むストリームを制御するのに役立ちます`Elem`、その文字特性はクラスによって決まります`Traits`します。

## <a name="syntax"></a>構文

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>パラメーター

*Elem*<br/>
型。

*Traits*<br/>
`char_traits` 型の変数。

## <a name="remarks"></a>Remarks

**basic_ios\<class Elem, class Traits>** クラスのオブジェクトは以下を格納します。

- [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>** 型のオブジェクトを指し示すリンク付けポインター。

- [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits >** 型のオブジェクトを指し示すストリーム バッファー ポインター。

- [書式設定情報](../standard-library/ios-base-class.md)。

- [ios_base](../standard-library/ios-base-class.md) 型のベース オブジェクトの[ストリームの状態情報](../standard-library/ios-base-class.md)。

- `char_type` 型のオブジェクトの充てん文字。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_ios](#basic_ios)|`basic_ios` クラスを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|テンプレート パラメーター `Elem` のシノニム。|
|[int_type](#int_type)|`Traits::int_type` と同義。|
|[off_type](#off_type)|`Traits::off_type` と同義。|
|[pos_type](#pos_type)|`Traits::pos_type` と同義。|
|[traits_type](#traits_type)|テンプレート パラメーター `Traits` のシノニム。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[bad](#bad)|ストリーム バッファーの整合性の損失を示します。|
|[clear](#clear)|すべてのエラー フラグをクリアします。|
|[copyfmt](#copyfmt)|1 つのストリームから別のストリームにフラグをコピーします。|
|[eof](#eof)|ストリームの末尾に達しているかどうかを示します。|
|[exceptions](#exceptions)|ストリームによってどの例外がスローされるかを示します。|
|[fail](#fail)|ストリームからの有効フィールドの抽出エラーを示します。|
|[fill](#fill)|テキストがストリームの幅に満たない場合に使用される文字を指定するか、返します。|
|[good](#good)|ストリームの状態が良好であることを示します。|
|[imbue](#imbue)|ロケールを変更します。|
|[init](#init)|`basic_ios` コンストラクターによって呼び出されます。|
|[move](#move)|ストリーム バッファーへのポインターを除くすべての値を、パラメーターから現在のオブジェクトに移動します。|
|[narrow](#narrow)|指定された `char_type` と同等の文字を検索します。|
|[rdbuf](#rdbuf)|指定したバッファーにストリームをルーティングします。|
|[rdstate](#rdstate)|フラグのビットの状態を読み取ります。|
|[set_rdbuf](#set_rdbuf)|ストリーム バッファーを割り当てて、このストリーム オブジェクトの読み取りバッファーとして使用します。|
|[setstate](#setstate)|追加のフラグを設定します。|
|[swap](#swap)|`basic_ios` オブジェクトの値を別の `basic_ios` オブジェクトの値と交換します。 ストリーム バッファーへのポインターは交換されません。|
|[tie](#tie)|1 つのストリームが別のストリームの前に処理されるようにします。|
|[widen](#widen)|指定された char と同等の `char_type` を検索します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[explicit operator bool](#op_bool)|使用できるように、`basic_ios`オブジェクトとして、 **bool**します。 しばしば発生する意図しない副作用を防ぐため、自動型変換は無効になっています。|
|[operator void *](#op_void_star)|ストリームが依然として良好かどうかを示します。|
|[operator!](#op_not)|ストリームが悪化していないかどうかを示します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ios>

**名前空間:** std

## <a name="bad"></a>  basic_ios::bad

ストリーム バッファーの整合性の損失を示します。

```cpp
bool bad() const;
```

### <a name="return-value"></a>戻り値

**true**場合`rdstate & badbit`は 0 以外。 それ以外の場合は、 **false**します。

`badbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_ios"></a>  basic_ios::basic_ios

basic_ios クラスを構築します。

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>パラメーター

*sb*<br/>
入力要素または出力要素を格納する標準のバッファー。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、[init](#init)(_ *Sb*) を呼び出すことによってそのメンバー オブジェクトを初期化します。 2 つ目の (保護された) コンストラクターは、そのメンバー オブジェクトを初期化前の状態のままにします。 以降の呼び出し`init`安全に破棄する前に、オブジェクトを初期化する必要があります。

## <a name="char_type"></a>  basic_ios::char_type

テンプレート パラメーター `Elem` のシノニム。

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>  basic_ios::clear

すべてのエラー フラグをクリアします。

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>パラメーター

*state*<br/>
(省略可能)すべてのフラグを消去した後に設定するフラグ。 既定値は `goodbit` です。

*reraise*<br/>
(省略可能)例外が再発生するかどうかを指定します。 既定値は**false** (再、が例外を発生していません)。

### <a name="remarks"></a>Remarks

フラグは`goodbit`、 `failbit`、 `eofbit`、および`badbit`します。 [good](#good)、[bad](#bad)、[eof](#eof)、および [fail](#fail) で、これらのフラグをテストします。

このメンバー関数は、格納されているストリームの状態情報を次のものに置き換えます。

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

`state`**&**[exceptions](#exceptions) が 0 以外の場合、[failure](../standard-library/ios-base-class.md#failure) クラスのオブジェクトをスローします。

### <a name="example"></a>例

参照してください[rdstate](#rdstate)と[getline](../standard-library/string-functions.md#getline)使用例については`clear`します。

## <a name="copyfmt"></a>  basic_ios::copyfmt

1 つのストリームから別のストリームにフラグをコピーします。

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
フラグをコピーするストリーム。

### <a name="return-value"></a>戻り値

フラグをコピーするストリームの **this** オブジェクト。

### <a name="remarks"></a>Remarks

メンバー関数は、コールバック イベントを報告する**消去\_イベント**します。 コピーし、*右* に **\*この** 充填文字、リンク付けポインター、および書式設定情報。 例外マスクを変更する前に、コールバック イベントを報告`copyfmt_event`します。 コピーの完了後、**state &**[exceptions](#exceptions) が 0 以外の場合、関数は引数 [rdstate](#rdstate) を使って効果的に [clear](#clear) を呼び出します。 **\*this** を返します。

### <a name="example"></a>例

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="eof"></a>  basic_ios::eof

ストリームの末尾に達しているかどうかを示します。

```cpp
bool eof() const;
```

### <a name="return-value"></a>戻り値

**true**ストリームの末尾に達している場合**false**それ以外の場合。

### <a name="remarks"></a>Remarks

メンバー関数を返します**true**場合[rdstate](#rdstate) `& eofbit`が 0 以外。 `eofbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="exceptions"></a>  basic_ios::exceptions

ストリームによってどの例外がスローされるかを示します。

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>パラメーター

*Newexcept*<br/>
例外をスローするフラグ。

### <a name="return-value"></a>戻り値

ストリームに対して例外をスローするように現在指定されているフラグ。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されている例外マスクを返します。 2 つ目のメンバー関数は、*_Except* を例外マスクに格納し、その前に格納されていた値を返します。 新しい例外マスクを格納することで、[clear](#clear)( [rdstate](#rdstate) ) の呼び出しと同じように例外をスローできます。

### <a name="example"></a>例

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="fail"></a>  basic_ios::fail

ストリームからの有効フィールドの抽出エラーを示します。

```cpp
bool fail() const;
```

### <a name="return-value"></a>戻り値

**true**場合[rdstate](#rdstate) `& (badbit|failbit)` 0 以外の場合、それ以外の場合は、 **false**します。

`failbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="fill"></a>  basic_ios::fill

テキストがストリームの幅に満たない場合に使用される文字を指定するか、返します。

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>パラメーター

*Char*<br/>
充填文字として必要な文字。

### <a name="return-value"></a>戻り値

現在の充填文字。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されている充填文字を返します。 2 番目のメンバー関数は*Char*充填文字を返しますで、前の値を格納します。

### <a name="example"></a>例

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="good"></a>  basic_ios::good

ストリームの状態が良好であることを示します。

```cpp
bool good() const;
```

### <a name="return-value"></a>戻り値

**true**場合[rdstate](#rdstate) `== goodbit` (状態フラグが設定されていない)、それ以外の場合、 **false**します。

`goodbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

### <a name="example"></a>例

`good` の使用例については、「[basic_ios::bad](#bad)」を参照してください。

## <a name="imbue"></a>  basic_ios::imbue

ロケールを変更します。

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>パラメーター

*Loc*<br/>
ロケールの文字列。

### <a name="return-value"></a>戻り値

以前のロケール。

### <a name="remarks"></a>Remarks

[rdbuf](#rdbuf) が Null ポインターではない場合、メンバー関数は以下を呼び出します。

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

いずれの場合も、[ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*) を返します。

### <a name="example"></a>例

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="init"></a>  basic_ios::init

basic_ios コンストラクターによって呼び出されます。

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>パラメーター

*_Sb*<br/>
入力要素または出力要素を格納する標準のバッファー。

*_Isstd*<br/>
これが標準のストリームかどうかを指定します。

### <a name="remarks"></a>Remarks

メンバー関数は、以下のようにするため、すべてのメンバー オブジェクトに値を格納します。

- [rdbuf](#rdbuf) が *_Sb* を返す。

- [tie](#tie) が Null ポインターを返す。

- [rdstate](#rdstate)返します[goodbit](../standard-library/ios-base-class.md#iostate)場合 *_Sb* 0 以外の値。 それ以外では返します[badbit](../standard-library/ios-base-class.md#iostate)します。

- [例外](#exceptions)返します`goodbit`します。

- [flags](../standard-library/ios-base-class.md#flags) が [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags) を返す。

- [width](../standard-library/ios-base-class.md#width) が 0 を返す。

- [precision](../standard-library/ios-base-class.md#precision) が 6 を返す。

- [fill](#fill) が空白文字を返す。

- [getloc](../standard-library/ios-base-class.md#getloc) が `locale::classic` を返す。

- [iword](../standard-library/ios-base-class.md#iword) が 0 を返し、[pword](../standard-library/ios-base-class.md#pword) がすべての引数値に Null ポインターを返す。

## <a name="int_type"></a>  basic_ios::int_type

`traits_type::int_type` と同義。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::move

ストリーム バッファーへのポインターを除くすべての値を、パラメーターから現在のオブジェクトに移動します。

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
値の移動元となる `ios_base` オブジェクト。

### <a name="remarks"></a>Remarks

プロテクト メンバー関数に格納されているすべての値を移動する*右*に`*this`を除き、格納されている`stream buffer pointer`、変更されないままにする*右*で null ポインターに設定し、`*this`します。 格納されている`tie pointer`で null ポインターに設定されている*右*します。

## <a name="narrow"></a>  basic_ios::narrow

指定された `char_type` と同等の文字を検索します。

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>パラメーター

*Char*<br/>
**Char**に変換します。

*既定値*<br/>
**Char**する返された同等が見つからない場合。

### <a name="return-value"></a>戻り値

相当**char**を指定された`char_type`します。

### <a name="remarks"></a>Remarks

メンバー関数を返します[use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc](../standard-library/ios-base-class.md#getloc)()).`narrow`( `Char`, `Default`).

### <a name="example"></a>例

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="off_type"></a>  basic_ios::off_type

`traits_type::off_type` と同義。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>  basic_ios::operator void *

ストリームが依然として良好かどうかを示します。

```cpp
operator void *() const;
```

### <a name="return-value"></a>戻り値

演算子は [fail](#fail) の場合にのみ Null ポインターを返します。

### <a name="example"></a>例

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="op_not"></a>  basic_ios::operator!

ストリームが悪化していないかどうかを示します。

```cpp
bool operator!() const;
```

### <a name="return-value"></a>戻り値

[fail](#fail) を返します。

### <a name="example"></a>例

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="op_bool"></a>  basic_ios::operator bool

使用できるように、`basic_ios`オブジェクトとして、 **bool**します。 しばしば発生する意図しない副作用を防ぐため、自動型変換は無効になっています。

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Remarks

演算子に変換できる値を返します**false**場合にのみ`fail()`します。 戻り値の型にのみ変換可能**bool**ではなく、`void *`またはその他の既知のスカラー型。

## <a name="pos_type"></a>  basic_ios::pos_type

`traits_type::pos_type` と同義。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>  basic_ios::rdbuf

指定したバッファーにストリームをルーティングします。

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>パラメーター

*_Sb*<br/>
ストリーム。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されているストリーム バッファー ポインターを返します。

2 番目のメンバー関数は *_Sb*格納されたストリーム バッファー ポインターに以前に格納された値を返します。

### <a name="example"></a>例

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="rdstate"></a>  basic_ios::rdstate

フラグのビットの状態を読み取ります。

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>戻り値

格納されているストリームの状態情報。

### <a name="example"></a>例

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="setstate"></a>  basic_ios::setstate

追加のフラグを設定します。

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>パラメーター

*_State*<br/>
設定する追加のフラグ。

### <a name="remarks"></a>Remarks

メンバー関数は効果的に [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)) を呼び出します。

### <a name="example"></a>例

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="set_rdbuf"></a>  basic_ios::set_rdbuf

ストリーム バッファーを割り当てて、このストリーム オブジェクトの読み取りバッファーとして使用します。

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>パラメーター

*strbuf*<br/>
読み取りバッファーになるストリーム バッファー。

### <a name="remarks"></a>Remarks

プロテクト メンバー関数のストア*strbuf*で、`stream buffer pointer`します。呼び出しません`clear`します。

## <a name="tie"></a>  basic_ios::tie

1 つのストリームが別のストリームの前に処理されるようにします。

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
ストリーム。

### <a name="return-value"></a>戻り値

1 つ目のメンバー関数は、格納されているリンク付けポインターを返します。 2 番目のメンバー関数は*str*リンク付けポインターを返しますで、前の値を格納します。

### <a name="remarks"></a>Remarks

`tie` は 2 つのストリームを同期させて、一方のストリームでの操作が完了すると、もう一方のストリームで操作が行われるようにします。

### <a name="example"></a>例

この例では、cout に cin にリンクすることで、"Enter a number:" 文字列がコンソールに移動した後で、数字が cin から抽出されることを保証します。 これにより、数値の読み取り時に "Enter a number:" 文字列がバッファーにまだ残っている可能性を排除して、ユーザーが応答するプロンプトが必ずいくつかあるようにします。 既定では、cin と cout は関連付けられています。

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="traits_type"></a>  basic_ios::traits_type

テンプレート パラメーター `Traits` のシノニム。

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>  basic_ios::widen

相当するものを検索します`char_type`を指定された**char**します。

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>パラメーター

*Char*<br/>
変換する文字。

### <a name="return-value"></a>戻り値

相当するものを検索します`char_type`を指定された**char**します。

### <a name="remarks"></a>Remarks

メンバー関数は [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **E**> >( [getloc](../standard-library/ios-base-class.md#getloc)) を返します。 `widen`( `Char`).

### <a name="example"></a>例

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="swap"></a>  basic_ios::swap

`basic_ios` オブジェクトの値を別の `basic_ios` オブジェクトの値と交換します。 ただし、ストリーム バッファーへのポインターは交換されません。

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
値を交換するために使用される `basic_ios` オブジェクト。

### <a name="remarks"></a>Remarks

プロテクト メンバー関数に格納されているすべての値を交換*右*で`*this`を除き、格納されている`stream buffer pointer`します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
