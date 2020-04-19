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
ms.openlocfilehash: 614e26b2329edeec2cccb32c7ba18b23e9d5320d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688440"
---
# <a name="basic_ios-class"></a>basic_ios クラス

クラステンプレートは、テンプレートパラメーターに依存する、(クラステンプレート[basic_istream](../standard-library/basic-istream-class.md)の) 入力ストリームと出力ストリーム (クラステンプレート[basic_ostream](../standard-library/basic-ostream-class.md)) の両方に共通するストレージおよびメンバー関数を記述します。 (クラス[ios_base](../standard-library/ios-base-class.md)は、テンプレートパラメーターに依存しない共通の機能を記述します。)クラス**basic_ios \<class Elem、クラス特性 >** のオブジェクトは `Elem` 型の要素を含むストリームを制御するのに役立ちます。この場合、文字特性は `Traits` クラスによって決定されます。

## <a name="syntax"></a>構文

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>パラメーター

*Elem* \
型。

*特徴*\
`char_traits` 型の変数。

## <a name="remarks"></a>Remarks

**basic_ios\<class Elem, class Traits>** クラスのオブジェクトは以下を格納します。

- [basic_istream](../standard-library/basic-istream-class.md) **\<Elem, Traits>** 型のオブジェクトを指し示すリンク付けポインター。

- [basic_streambuf](../standard-library/basic-streambuf-class.md) **\<Elem, Traits >** 型のオブジェクトを指し示すストリーム バッファー ポインター。

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
|[explicit operator bool](#op_bool)|@No__t_0 オブジェクトを**ブール**値として使用できるようにします。 しばしば発生する意図しない副作用を防ぐため、自動型変換は無効になっています。|
|[operator void *](#op_void_star)|ストリームが依然として良好かどうかを示します。|
|[operator!](#op_not)|ストリームが悪化していないかどうかを示します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<ios>

**名前空間:** std

## <a name="bad"></a>  basic_ios::bad

ストリーム バッファーの整合性の損失を示します。

```cpp
bool bad() const;
```

### <a name="return-value"></a>戻り値

`rdstate & badbit` が0以外の場合は**true** 。それ以外の場合は**false**。

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

*sb* \
入力要素または出力要素を格納する標準のバッファー。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、[init](#init)(_ *Sb*) を呼び出すことによってそのメンバー オブジェクトを初期化します。 2 つ目の (保護された) コンストラクターは、そのメンバー オブジェクトを初期化前の状態のままにします。 後で `init` を呼び出す場合は、オブジェクトを安全に破棄する前に、そのオブジェクトを初期化する必要があります。

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

*状態*\
Optionalすべてのフラグをクリアした後に設定するフラグ。 既定値は `goodbit` です。

*reraise* \
Optional例外を再生成する必要があるかどうかを指定します。 既定値は**false**です (例外は再発生しません)。

### <a name="remarks"></a>Remarks

フラグは、`goodbit`、`failbit`、`eofbit`、および `badbit` です。 [good](#good)、[bad](#bad)、[eof](#eof)、および [fail](#fail) で、これらのフラグをテストします。

このメンバー関数は、格納されているストリームの状態情報を次のものに置き換えます。

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

`state` **&** [exceptions](#exceptions) が 0 以外の場合、[failure](../standard-library/ios-base-class.md#failure) クラスのオブジェクトをスローします。

### <a name="example"></a>例

@No__t_2 を使用する例については、「 [rdstate](#rdstate) 」と「 [getline](../standard-library/string-functions.md#getline) 」を参照してください。

## <a name="copyfmt"></a>  basic_ios::copyfmt

1 つのストリームから別のストリームにフラグをコピーします。

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
フラグをコピーするストリーム。

### <a name="return-value"></a>戻り値

フラグをコピーするストリームの **this** オブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数は、コールバックイベントの**消去 \_event**を報告します。 次に、fill 文字、結合ポインター、および書式設定情報 **\*this** *右*からコピーします。 例外マスクを変更する前に、コールバックイベント `copyfmt_event` を報告します。 コピーの完了後、**state &** [exceptions](#exceptions) が 0 以外の場合、関数は引数 [rdstate](#rdstate) を使って効果的に [clear](#clear) を呼び出します。 **\*this** を返します。

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

ストリームの末尾に到達した場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [rdstate](#rdstate) `& eofbit` が0以外の場合に**true**を返します。 `eofbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

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

*Newexcept* \
例外をスローするフラグ。

### <a name="return-value"></a>戻り値

ストリームに対して例外をスローするように現在指定されているフラグ。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されている例外マスクを返します。 2 つ目のメンバー関数は、 *_Except* を例外マスクに格納し、その前に格納されていた値を返します。 新しい例外マスクを格納することで、[clear](#clear)( [rdstate](#rdstate) ) の呼び出しと同じように例外をスローできます。

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

[rdstate](#rdstate) `& (badbit|failbit)` が0以外の場合は**true** 、それ以外の場合は**false**。

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

*Char* \
充填文字として必要な文字。

### <a name="return-value"></a>戻り値

現在の充填文字。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されている充填文字を返します。 2番目のメンバー関数は、 *Char*を fill 文字に格納し、その前に格納された値を返します。

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

[rdstate](#rdstate) `== goodbit` (状態フラグが設定されていない) の場合は**true** 、それ以外の場合は**false**。

`goodbit` の詳細については、「[ios_base::iostate](../standard-library/ios-base-class.md#iostate)」を参照してください。

### <a name="example"></a>例

`good` の使用例については、「[basic_ios::bad](#bad)」を参照してください。

## <a name="imbue"></a>  basic_ios::imbue

ロケールを変更します。

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>パラメーター

*Loc* \
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

*Sb* \
入力要素または出力要素を格納する標準のバッファー。

*_Isstd* \
これが標準のストリームかどうかを指定します。

### <a name="remarks"></a>Remarks

メンバー関数は、以下のようにするため、すべてのメンバー オブジェクトに値を格納します。

- [rdbuf](#rdbuf) が *_Sb* を返す。

- [tie](#tie) が Null ポインターを返す。

- [rdstate](#rdstate)が0以外*の場合は* [goodbit](../standard-library/ios-base-class.md#iostate)を返します。それ以外の場合は、 [badbit](../standard-library/ios-base-class.md#iostate)を返します。

- [例外](#exceptions)は `goodbit` を返します。

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

*右*\
値の移動元となる `ios_base` オブジェクト。

### <a name="remarks"></a>Remarks

Protected メンバー関数は、 *right*に格納されているすべての値を `*this` に移動します。ただし、格納さ*れている*`stream buffer pointer` は変更されず、`*this` の null ポインターに設定されます。 格納されている `tie pointer` が、*右*の null ポインターに設定されています。

## <a name="narrow"></a>  basic_ios::narrow

指定された `char_type` と同等の文字を検索します。

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>パラメーター

*Char* \
変換する**char** 。

*Default*\
等価のが見つからない場合に返される**char** 。

### <a name="return-value"></a>戻り値

指定された `char_type` に対する等価の**char** 。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype \<E > > ( [getloc](../standard-library/ios-base-class.md#getloc)()) を返します。`narrow` (`Char`、`Default`)。

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

@No__t_0 オブジェクトを**ブール**値として使用できるようにします。 しばしば発生する意図しない副作用を防ぐため、自動型変換は無効になっています。

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Remarks

演算子は、`fail()` 場合にのみ、 **false**に変換可能な値を返します。 戻り値の型は、`void *` またはその他の既知のスカラー型ではなく、 **bool**にのみ変換できます。

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

*Sb* \
ストリーム。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されているストリーム バッファー ポインターを返します。

2番目のメンバー関数は、格納されているストリームバッファーポインターに*Sb*を格納し、以前に格納された値を返します。

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

*状態 \ (_c)*
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

*strbuf* \
読み取りバッファーになるストリーム バッファー。

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、 *strbuf*を `stream buffer pointer` に格納します。 `clear` を呼び出しません。

## <a name="tie"></a>  basic_ios::tie

1 つのストリームが別のストリームの前に処理されるようにします。

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>パラメーター

*str* \
ストリーム。

### <a name="return-value"></a>戻り値

1 つ目のメンバー関数は、格納されているリンク付けポインターを返します。 2番目のメンバー関数は、同一のポインターに*str*を格納し、その前に格納された値を返します。

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

指定した**char**に等しい `char_type` を検索します。

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>パラメーター

*Char* \
変換する文字。

### <a name="return-value"></a>戻り値

指定した**char**に等しい `char_type` を検索します。

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

*右*\
値を交換するために使用される `basic_ios` オブジェクト。

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、格納されている `stream buffer pointer` を除く、 *right*に格納されているすべての値を `*this` と交換します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
