---
title: ios_base クラス
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: 17fb83cdbf882467f0ec330e05a6506b13051cab
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890124"
---
# <a name="ios_base-class"></a>ios_base クラス

このクラスは、テンプレート パラメーターに依存しない、入力ストリームと出力ストリームの両方に共通のストレージとメンバー関数を表します。 (クラステンプレート[basic_ios](../standard-library/basic-ios-class.md)は、テンプレートパラメーターに依存している共通の機能について説明しています)。

ios_base クラスのオブジェクトには、次の情報で構成される書式設定情報が格納されます。

- [`fmtflags`](#fmtflags)型のオブジェクトの書式設定フラグ。

- [`iostate`](#iostate)型のオブジェクトの例外マスク。

- **Int**型のオブジェクトのフィールド幅。

- **Int**型のオブジェクトの表示精度。

- `locale`型のオブジェクトのロケールオブジェクト。

- **Long**および**void**ポインター型の要素を持つ2つの拡張可能な配列。

Ios_base クラスのオブジェクトでは、ストリームの状態情報も[`iostate`](#iostate)型のオブジェクトとコールバックスタックに格納されます。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[ios_base](#ios_base)|`ios_base` オブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[event_callback](#event_callback)|[register_call](#register_callback) に渡される関数を記述します。|
|[`fmtflags`](#fmtflags)|出力の外観を指定する定数。|
|[`iostate`](#iostate)|ストリームの状態を表す定数を定義します。|
|[openmode](#openmode)|ストリームとの対話方法を記述します。|
|[seekdir](#seekdir)|オフセット演算の開始位置を指定します。|

### <a name="enums"></a>列挙体

|||
|-|-|
|[event](#event)|イベントの種類を指定します。|

### <a name="constants"></a>定数

|||
|-|-|
|[adjustfield](#fmtflags)|`internal` &#124; `left` &#124; `right` のように定義されたビットマスク。|
|[app](#openmode)|各挿入前にストリームの末尾にシークするように指定します。|
|[ate](#openmode)|コントロール オブジェクトが最初に作成されたときに、ストリームの末尾にシークするように指定します。|
|[badbit](#iostate)|ストリーム バッファーの整合性の損失を記録します。|
|[basefield](#fmtflags)|`dec` &#124; `hex` &#124; `oct` のように定義されたビットマスク。|
|[beg](#seekdir)|シーケンスの先頭からの相対シークを指定します。|
|[binary](#openmode)|テキスト ストリームではなく、バイナリ ストリームとしてファイルを読み取るように指定します。|
|[boolalpha](#fmtflags)|**ブール**型のオブジェクトを数値としてではなく、名前 ( **true**や**false**など) として挿入または抽出するように指定します。|
|[cur](#seekdir)|シーケンス内の現在位置からの相対シークを指定します。|
|[dec](#fmtflags)|10 進形式で整数値を挿入もしくは抽出するように指定します。|
|[end](#seekdir)|シーケンスの末尾からの相対シークを指定します。|
|[eofbit](#iostate)|ストリームからの抽出中にファイルの終わりを記録します。|
|[failbit](#iostate)|ストリームからの有効フィールドの抽出エラーを記録します。|
|[fixed](#fmtflags)|固定小数点形式 (指数フィールドなし) で浮動小数点値を挿入するように指定します。|
|[floatfield](#fmtflags)|`fixed` &#124; `scientific` のように定義されたビットマスク。|
|[goodbit](#iostate)|状態ビットをすべてクリアします。|
|[hex](#fmtflags)|16 進数形式で整数値を挿入もしくは抽出するように指定します。|
|[in](#openmode)|ストリームからの抽出を指定します。|
|[internal](#fmtflags)|生成された数値フィールドの内部ポイントに充てん文字を挿入することにより、フィールド幅を埋めます。|
|[left](#fmtflags)|左揃えを指定します。|
|[oct](#fmtflags)|8 進数形式で整数値を挿入もしくは抽出するように指定します。|
|[out](#openmode)|ストリームへの挿入を指定します。|
|[right](#fmtflags)|右揃えを指定します。|
|[scientific](#fmtflags)|指数形式 (指数フィールドあり) で浮動小数点値を挿入するように指定します。|
|[showbase](#fmtflags)|生成された整数フィールドのベースを示すプレフィックスを挿入するように指定します。|
|[showpoint](#fmtflags)|生成された浮動小数点フィールドに無条件で小数点を挿入するように指定します。|
|[showpos](#fmtflags)|生成された負の値を取らない数値フィールドにプラス記号を挿入するように指定します。|
|[skipws](#fmtflags)|特定の抽出の前に、先頭の空白文字をスキップすることを指定します。|
|[trunc](#openmode)|既存のファイルのコントロール オブジェクトが作成されたときに、そのファイルの内容を削除するように指定します。|
|[unitbuf](#fmtflags)|各挿入後に出力をフラッシュします。|
|[uppercase](#fmtflags)|特定の挿入で小文字に対応する大文字を挿入するように指定します。|

### <a name="functions"></a>関数

|||
|-|-|
|[failure](#failure)|このメンバークラスは、クラステンプレート[basic_ios](../standard-library/basic-ios-class.md)のメンバー関数[clear](../standard-library/basic-ios-class.md#clear)によってスローされるすべての例外の基本クラスとして機能します。|
|[flags](#flags)|現在のフラグ設定を設定するか返します。|
|[getloc](#getloc)|格納されているロケール オブジェクトを返します。|
|[imbue](#imbue)|ロケールを変更します。|
|[Init](#init)|構築時に標準 `iostream` オブジェクトを作成します。|
|[iword](#iword)|`iword` として格納される値を割り当てます。|
|[precision](#precision)|浮動小数点数で表示する桁数を指定します。|
|[pword](#pword)|`pword` として格納される値を割り当てます。|
|[register_callback](#register_callback)|コールバック関数を指定します。|
|[setf](#setf)|指定したフラグを設定します。|
|[sync_with_stdio](#sync_with_stdio)|`iostream` および C ランタイムライブラリの操作が、ソースコードに出現する順序で実行されることを保証します。|
|[unsetf](#unsetf)|指定したフラグをオフにします。|
|[width](#width)|出力ストリームの長さを設定します。|
|[xalloc](#xalloc)|変数がストリームの一部となるように指定します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_eq)|`ios_base` オブジェクトの代入演算子。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<ios>

**名前空間:** std

## <a name="event"></a>場合

イベントの種類を指定します。

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Remarks

型は、[register_callback](#register_callback) に登録されている関数の引数として使用するコールバック イベントを格納できるオブジェクトを記述する列挙型です。 それぞれのイベント値は次のとおりです。

- `copyfmt_event`、[例外マスク](../standard-library/ios-base-class.md)がコピーされる直前に、 [copyfmt へ](../standard-library/basic-ios-class.md#copyfmt)の呼び出しの末尾付近に発生するコールバックを識別します。

- `erase_event`、 [copyfmt へ](../standard-library/basic-ios-class.md#copyfmt)の呼び出しの開始時に発生するコールバックを識別したり、**このを\*** ためにデストラクターの呼び出しの先頭にあるコールバックを識別したりします。

- `imbue_event`、関数がを返す直前に、 [imbue](#imbue)の呼び出しの最後に発生するコールバックを識別します。

### <a name="example"></a>例

例については、「[register_callback](#register_callback)」を参照してください。

## <a name="event_callback"></a>event_callback

[register_call](#register_callback) に渡される関数を記述します。

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>パラメーター

\ *(_r)*
[イベント](#event)。

*基本\ (_c)*
イベントが呼び出されたストリーム。

*_I*\
ユーザー定義された番号。

### <a name="remarks"></a>Remarks

この型は、[register_callback](#register_callback) に登録できる関数へのポインターを記述します。 関数のこの型は例外をスローできません。

### <a name="example"></a>例

`event_callback` の使用例については、「[register_call](#register_callback)」を参照してください。

## <a name="failure"></a>不具合

クラス `failure` は、ストリーム バッファー処理中に検出されたエラーを報告するために `iostreams` ライブラリの関数によって例外としてスローされるすべてのオブジェクトの型の基底クラスを定義します。

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>Remarks

`what()` によって返される値は `_Message` のコピーであり、`_Code` に基づいて、テストにより拡張されている可能性があります。 `_Code` を指定しない場合、既定値は `make_error_code(io_errc::stream)` になります。

### <a name="example"></a>例

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a>示す

現在のフラグ設定を設定するか返します。

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>パラメーター

*fmtfl* \
新しい `fmtflags` 設定。

### <a name="return-value"></a>戻り値

以前または現在の `fmtflags` 設定。

### <a name="remarks"></a>Remarks

フラグのリストについては、「[ios_base::fmtflags](#fmtflags)」を参照してください。

1 番目のメンバー関数は、格納されている書式設定フラグを返します。 2番目のメンバー関数は、 *fmtfl*を format フラグに格納し、その前に格納された値を返します。

### <a name="example"></a>例

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a>fmtflags

出力の外観を指定する定数。

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>Remarks

[ios](../standard-library/ios.md) のマニピュレーターをサポートします。

この型は、書式設定フラグを格納できるオブジェクトを記述するビットマスク型です。 個々のフラグの値 (要素) は、次のとおりです。

- `dec`、10 進形式で整数値を挿入または抽出します。

- `hex`、16 進数形式で整数値を挿入または抽出します。

- `oct`、8 進数形式で整数値を挿入または抽出します。

- `showbase`、生成された整数フィールドのベースを示すプレフィックスを挿入します。

- `internal`、生成された数値フィールドの内部ポイントに必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます。 (フィールド幅の設定の詳細については、「 [`setw`](../standard-library/iomanip-functions.md#setw))」を参照してください。

- `left`、生成されたフィールドの最後に、必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます (左揃えの場合)。

- `right`、生成されたフィールドの先頭に、必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます (右揃えの場合)。

- `boolalpha`、数値としてではなく、 **bool**型のオブジェクトを名前 ( **true**や**false**など) として挿入または抽出します。

- `fixed`、固定小数点形式 (指数フィールドなし) で浮動小数点値を挿入します。

- `scientific`、指数形式 (指数フィールドあり) で浮動小数点値を挿入します。

- `showpoint`、生成された浮動小数点フィールドに無条件で小数点を挿入します。

- `showpos`、生成された負の値を取らない数値フィールドにプラス記号を挿入します。

- `skipws`、特定の抽出の前にある先頭の空白文字をスキップします。

- `unitbuf`、各挿入後に出力をフラッシュします。

- `uppercase`、特定の挿入で小文字に対応する大文字を挿入します。

さらに、次の値も役立ちます。

- `adjustfield`、`internal` &#124; `left` &#124; `right` のように定義されるビットマスク。

- `basefield`、`dec` &#124; `hex` &#124; `oct` のように定義されます。

- `floatfield`、`fixed` &#124; `scientific` のように定義されます。

これらの書式設定フラグを変更する関数の例については、「[\<iomanip>](../standard-library/iomanip.md)」を参照してください。

## <a name="getloc"></a>getloc

格納されているロケール オブジェクトを返します。

```cpp
locale getloc() const;
```

### <a name="return-value"></a>戻り値

格納されているロケール オブジェクト。

### <a name="example"></a>例

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a>imbue

ロケールを変更します。

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>パラメーター

*\*
新しいロケール設定。

### <a name="return-value"></a>戻り値

以前のロケール。

### <a name="remarks"></a>Remarks

このメンバー関数は、locale オブジェクトにある*Loc*を格納してから、コールバックイベントと `imbue_event`を報告します。 以前に格納されていた値を返します。

### <a name="example"></a>例

例については、「[basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)」を参照してください。

## <a name="init"></a>初期化

構築時に標準 `iostream` オブジェクトを作成します。

```cpp
class Init { };
```

### <a name="remarks"></a>Remarks

入れ子になったクラスは、任意の静的オブジェクトのコンストラクターを実行する前でも、標準の `iostream` オブジェクトが適切に構築されることを保証するオブジェクトを表します。

## <a name="ios_base"></a>ios_base

Ios_base オブジェクトを構築します。

```cpp
ios_base();
```

### <a name="remarks"></a>Remarks

この (プロテクト) コンストラクターは、何も実行しません。 後で `basic_ios::`[init](../standard-library/basic-ios-class.md#init)を呼び出す場合は、オブジェクトを安全に破棄する前に、そのオブジェクトを初期化する必要があります。 このため、クラス ios_base の安全な使用は、クラステンプレート[basic_ios](../standard-library/basic-ios-class.md)の基底クラスとしてのみ使用されます。

## <a name="iostate"></a>iostate

ストリームの状態を表す定数の型。

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Remarks

この型は、ストリーム状態情報を格納できるオブジェクトを記述するビットマスク型です。 個々のフラグの値 (要素) は、次のとおりです。

- `badbit`。ストリーム バッファーの整合性の損失を記録します。

- `eofbit`。ストリームからの抽出中にファイルの終わりを記録します。

- `failbit`。ストリームからの有効フィールドの抽出エラーを記録します。

また、有効な値は `goodbit` です。前述のビットはいずれも設定されていません (`goodbit` はゼロであることが保証されています)。

## <a name="iword"></a>iword

`iword` として格納される値を割り当てます。

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>パラメーター

*idx* \
`iword` として格納する値のインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数は、 **long**型の要素を含む拡張可能な配列の要素*idx*への参照を返します。 すべての要素は、実質的に存在し、最初に値 0 を格納します。 返された参照は、オブジェクトに対して次に `iword` を呼び出した後、`basic_ios::`[copyfmt へ](../standard-library/basic-ios-class.md#copyfmt)の呼び出しによってオブジェクトが変更された後、またはオブジェクトが破棄された後に無効になります。

*Idx*が負の場合、または要素に対して一意のストレージを使用できない場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)` を呼び出し、一意でない可能性がある参照を返します。

`ios_base`型のすべてのオブジェクトで使用するための一意のインデックスを取得するには、 [`xalloc`](#xalloc)を呼び出します。

### <a name="example"></a>例

`iword`の使用方法の例については、「 [`xalloc`](#xalloc) 」を参照してください。

## <a name="openmode"></a>openmode

ストリームとの対話方法を記述します。

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Remarks

この型は、複数の `iostream` オブジェクトの開始モードを格納できるオブジェクトを表す `bitmask type` です。 個々のフラグの値 (要素) は、次のとおりです。

- `app`、各挿入前にストリームの末尾をシークします。

- `ate`、そのコントロールオブジェクトが最初に作成されたときに、ストリームの末尾をシークします。

- `binary`、テキストストリームとしてではなく、バイナリストリームとしてファイルを読み取ることができます。

- `in`。ストリームからの抽出を許可します。

- `out`。ストリームへの挿入を許可します。

- `trunc`、そのコントロールオブジェクトが作成されたときに、既存のファイルの内容を削除します。

### <a name="example"></a>例

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="op_eq"></a>operator =

ios_base オブジェクトの代入演算子。

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>パラメーター

*右*\
`ios_base` 型のオブジェクト。

### <a name="return-value"></a>戻り値

割り当て先のオブジェクト。

### <a name="remarks"></a>Remarks

この演算子は、格納されている書式設定情報をコピーして、任意の拡張可能な配列の新しいコピーを作成します。 その後、 **\*this** を返します。 コールバックのスタックはコピーされません。

この演算子は、`ios_base` から派生したクラスでのみ使用されます。

## <a name="precision"></a>精度

浮動小数点数で表示する桁数を指定します。

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>パラメーター

*_Prec*\
表示する有効桁数または固定小数点表記での小数点の後の桁数。

### <a name="return-value"></a>戻り値

1 番目のメンバー関数は、格納されている[表示桁数](../standard-library/ios-base-class.md)を返します。 2番目のメンバー関数は、 *_Prec*を表示精度に格納し、その前に格納された値を返します。

### <a name="remarks"></a>Remarks

浮動小数点数は、[fixed](../standard-library/ios-functions.md#fixed) によって固定小数点表記で表示されます。

### <a name="example"></a>例

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a>pword

`pword` として格納される値を割り当てます。

```cpp
void *& pword(int index);
```

### <a name="parameters"></a>パラメーター

*インデックス*\
`pword` として格納する値のインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数は、 **void**ポインター型の要素を含む拡張可能な配列の要素*インデックス*への参照を返します。 すべての要素は、実質的に存在し、最初に Null ポインターを格納します。 返された参照は、オブジェクトに対して次に `pword` を呼び出した後、`basic_ios::`[copyfmt へ](../standard-library/basic-ios-class.md#copyfmt)の呼び出しによってオブジェクトが変更された後、またはオブジェクトが破棄された後に無効になります。

*Index*が負の場合、または要素に対して一意のストレージを使用できない場合、関数は[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)` を呼び出し、一意でない可能性がある参照を返します。

`ios_base`型のすべてのオブジェクトで使用するための一意のインデックスを取得するには、 [`xalloc`](#xalloc)を呼び出します。

### <a name="example"></a>例

`pword`の使用例については、「 [`xalloc`](#xalloc) 」を参照してください。

## <a name="register_callback"></a>register_callback

コールバック関数を指定します。

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>パラメーター

*pfn* \
コールバック関数へのポインター。

*idx* \
ユーザー定義された番号。

### <a name="remarks"></a>Remarks

このメンバー関数は、`{pfn, idx}` ペアを、格納されているコールバックスタックの[コールバックスタック](../standard-library/ios-base-class.md)にプッシュします。 コールバックイベント**ev**が報告されると、`(*pfn)(ev, *this, idx)` 式によって、レジストリの逆の順序で関数が呼び出されます。

### <a name="example"></a>例

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a>seekdir

オフセット演算の開始位置を指定します。

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>Remarks

この型は、複数の `iostream` クラスのメンバー関数への引数として使用されるシークモードを格納できるオブジェクトを表す列挙型です。 次に、それぞれのフラグ値を示します。

- `beg`、シーケンス (配列、ストリーム、またはファイル) の先頭を基準にしてシーク (現在の読み取りまたは書き込みの位置を変更) します。

- `cur`。シーケンス内の現在位置を基準としてシークします。

- `end`、シーケンスの末尾を基準にしてシークします。

### <a name="example"></a>例

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a>setf

指定したフラグを設定します。

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>パラメーター

*マスクの\ (_l)*
オンにするフラグ。

\ の設定解除 *(_c)*
無効にするフラグ。

### <a name="return-value"></a>戻り値

前の書式設定フラグ

### <a name="remarks"></a>Remarks

最初のメンバー関数は、`(_Mask | _Flags)` (選択されたビットを設定する)[フラグ](#flags)を効果的に呼び出し、前の書式フラグを返します。 2番目のメンバー関数は、`flags(_Mask & fmtfl, flags & ~_Mask)` (マスクの下で選択されているビットを置き換える) を実際に呼び出し、前の書式設定フラグを返します。

### <a name="example"></a>例

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a>sync_with_stdio

`iostream` および C ランタイムライブラリの操作が、ソースコードに出現する順序で実行されることを保証します。

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>パラメーター

*同期\ (_d)*
すべてのストリームが `stdio` と同期されているかどうか。

### <a name="return-value"></a>戻り値

この関数の以前の設定。

### <a name="remarks"></a>Remarks

静的メンバー関数は、最初は**true**である `stdio` 同期フラグを格納します。 **True**の場合、このフラグにより、同じファイルに対する操作が、 [`iostreams`](../standard-library/iostreams-conventions.md)の関数とC++標準ライブラリで定義されている関数の間で適切に同期されます。 そうしないと、同期が保証されるか、または保証されない場合がありますが、パフォーマンスが向上する可能性があります。 関数は、`stdio` 同期フラグに*同期*を格納し、その前に格納された値を返します。 標準ストリームに対して操作を実行する前にのみ、確実に呼び出すことができます。

## <a name="unsetf"></a>unsetf

指定したフラグをオフにします。

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>パラメーター

*マスクの\ (_l)*
オフにしたいフラグ。

### <a name="remarks"></a>Remarks

このメンバー関数は、明示的に[フラグ](#flags)(`~`*マスク* **& フラグ**) を呼び出します (選択したビットをクリアします)。

### <a name="example"></a>例

`unsetf`の使用例については、「 [ios_base:: setf](#setf) 」を参照してください。

## <a name="width"></a>幅

出力ストリームの長さを設定します。

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>パラメーター

*ワイド\ (_s)*
出力ストリームの必要なサイズ。

### <a name="return-value"></a>戻り値

現在の幅の設定。

### <a name="remarks"></a>Remarks

1つ目のメンバー関数は、格納されているフィールドの幅を返します。 2番目のメンバー関数は、フィールド*幅に幅を格納*し、その前に格納された値を返します。

### <a name="example"></a>例

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a>xalloc

変数がストリームの一部であることを指定します。

```cpp
static int xalloc( );
```

### <a name="return-value"></a>戻り値

静的メンバー関数は、格納されている静的な値を返します。この値は、呼び出しごとに増加します。

### <a name="remarks"></a>Remarks

メンバー関数[`iword`](#iword)または[`pword`](#pword)を呼び出すときに、戻り値を一意のインデックス引数として使用できます。

### <a name="example"></a>例

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
