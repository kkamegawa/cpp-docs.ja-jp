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
ms.openlocfilehash: 8911c3763e6a0c861c162611e1b2617ec26f0cf9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333359"
---
# <a name="iosbase-class"></a>ios_base クラス

このクラスは、テンプレート パラメーターに依存しない、入力ストリームと出力ストリームの両方に共通のストレージとメンバー関数を表します。 (テンプレート クラス [basic_ios](../standard-library/basic-ios-class.md) は、テンプレート パラメーターに依存する、共通の要素を記述します。)

ios_base クラスのオブジェクトには、次の情報で構成される書式設定情報が格納されます。

- [fmtflags](#fmtflags) 型のオブジェクトの書式設定フラグ。

- [iostate](#iostate) 型のオブジェクト内の例外マスク。

- 型のオブジェクトのフィールド幅**int**します。

- 型のオブジェクトの表示桁数**int**します。

- 型のオブジェクトのロケール オブジェクト`locale`します。

- 型の要素の 2 つの拡張可能な配列**長い**と**void**ポインター。

ios_base クラスのオブジェクトでは、ストリームの状態情報が [iostate](#iostate) 型のオブジェクトに格納されるほか、コールバックのスタックも格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[ios_base](#ios_base)|`ios_base` オブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[event_callback](#event_callback)|[register_call](#register_callback) に渡される関数を記述します。|
|[fmtflags](#fmtflags)|出力の外観を指定する定数。|
|[iostate](#iostate)|ストリームの状態を表す定数を定義します。|
|[openmode](#openmode)|ストリームとの対話方法を記述します。|
|[seekdir](#seekdir)|オフセット演算の開始位置を指定します。|

### <a name="enums"></a>列挙型

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
|[boolalpha](#fmtflags)|挿入もしくは抽出型のオブジェクトを指定します**bool**名として (など**true**と**false**) ではなく数値。|
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

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[failure](#failure)|このメンバー クラスは、テンプレート クラス [basic_ios](../standard-library/basic-ios-class.md) のメンバー関数 [clear](../standard-library/basic-ios-class.md#clear) によってスローされるすべての例外の基底クラスとして機能します。|
|[flags](#flags)|現在のフラグ設定を設定するか返します。|
|[getloc](#getloc)|格納されているロケール オブジェクトを返します。|
|[imbue](#imbue)|ロケールを変更します。|
|[Init](#init)|構築時に標準の iostream オブジェクトを作成します。|
|[iword](#iword)|`iword` として格納される値を割り当てます。|
|[precision](#precision)|浮動小数点数で表示する桁数を指定します。|
|[pword](#pword)|`pword` として格納される値を割り当てます。|
|[register_callback](#register_callback)|コールバック関数を指定します。|
|[setf](#setf)|指定したフラグを設定します。|
|[sync_with_stdio](#sync_with_stdio)|iostream と C ランタイム ライブラリの処理が、ソース コードに現れる順序で実行されるようにします。|
|[unsetf](#unsetf)|指定したフラグをオフにします。|
|[width](#width)|出力ストリームの長さを設定します。|
|[xalloc](#xalloc)|変数がストリームの一部となるように指定します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|`ios_base` オブジェクトの代入演算子。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ios>

**名前空間:** std

## <a name="event"></a>  ios_base::event

イベントの種類を指定します。

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Remarks

型は、[register_callback](#register_callback) に登録されている関数の引数として使用するコールバック イベントを格納できるオブジェクトを記述する列挙型です。 それぞれのイベント値は次のとおりです。

- `copyfmt_event`、への呼び出しの末尾付近で発生するコールバックを識別するために[copyfmt](../standard-library/basic-ios-class.md#copyfmt)直前に、[例外マスク](../standard-library/ios-base-class.md)がコピーされます。

- `erase_event`、への呼び出しの開始時に発生するコールバックを識別するために[copyfmt](../standard-library/basic-ios-class.md#copyfmt)、またはのデストラクターへの呼び出しの先頭に **\*この**します。

- `imbue_event`、への呼び出しの最後に発生するコールバックを識別するために[imbue](#imbue)関数が戻る直前に、します。

### <a name="example"></a>例

例については、「[register_callback](#register_callback)」を参照してください。

## <a name="event_callback"></a>  ios_base::event_callback

[register_call](#register_callback) に渡される関数を記述します。

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>パラメーター

*_E*<br/>
[イベント](#event)。

*(_B)*<br/>
イベントが呼び出されたストリーム。

*_I*<br/>
ユーザー定義された番号。

### <a name="remarks"></a>Remarks

この型は、[register_callback](#register_callback) に登録できる関数へのポインターを記述します。 関数のこの型は例外をスローできません。

### <a name="example"></a>例

`event_callback` の使用例については、「[register_call](#register_callback)」を参照してください。

## <a name="failure"></a>  ios_base::failure

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

## <a name="flags"></a>  ios_base::flags

現在のフラグ設定を設定するか返します。

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>パラメーター

*fmtfl*<br/>
新しい `fmtflags` 設定。

### <a name="return-value"></a>戻り値

以前または現在の `fmtflags` 設定。

### <a name="remarks"></a>Remarks

フラグのリストについては、「[ios_base::fmtflags](#fmtflags)」を参照してください。

1 番目のメンバー関数は、格納されている書式設定フラグを返します。 2 番目のメンバー関数は*fmtfl*で書式設定フラグを返します前の値を格納します。

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

## <a name="fmtflags"></a>  ios_base::fmtflags

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

- `internal`、生成された数値フィールドの内部ポイントに必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます。 (フィールド幅の設定の詳細については、「[setw](../standard-library/iomanip-functions.md#setw)」を参照してください。)

- `left`、生成されたフィールドの最後に、必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます (左揃えの場合)。

- `right`、生成されたフィールドの先頭に、必要に応じて充てん文字を挿入することにより、フィールド幅を埋めます (右揃えの場合)。

- `boolalpha`、挿入または抽出型のオブジェクトに**bool**名として (など**true**と**false**) ではなく数値として。

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

## <a name="getloc"></a>  ios_base::getloc

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

## <a name="imbue"></a>  ios_base::imbue

ロケールを変更します。

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>パラメーター

*_Loc*<br/>
新しいロケール設定。

### <a name="return-value"></a>戻り値

以前のロケール。

### <a name="remarks"></a>Remarks

メンバーの関数は *_Loc*ロケール オブジェクトにし、コールバック イベントを報告し、`imbue_event`します。 以前に格納されていた値を返します。

### <a name="example"></a>例

例については、「[basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)」を参照してください。

## <a name="init"></a>  ios_base::Init

構築時に標準の iostream オブジェクトを作成します。

```cpp
class Init { };
```

### <a name="remarks"></a>Remarks

この入れ子になったクラスが記述するオブジェクトは、その構築により、任意の静的オブジェクトのコンストラクターの実行前でも標準 iostreams オブジェクトが正しく構築されるようにします。

## <a name="ios_base"></a>  ios_base::ios_base

Ios_base オブジェクトを構築します。

```cpp
ios_base();
```

### <a name="remarks"></a>Remarks

この (プロテクト) コンストラクターは、何も実行しません。 以降の **basic_ios::**[init](../standard-library/basic-ios-class.md#init) への呼び出しは、オブジェクトを安全に破棄する前に、初期化する必要があります。 このため、クラス ios_base の唯一の安全な使用は、テンプレート クラス [basic_ios](../standard-library/basic-ios-class.md) の基底クラスとして使用することです。

## <a name="iostate"></a>  ios_base::iostate

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

有効な値は、さらに、`goodbit`前に説明した各ビットが設定されている、(`goodbit`を 0 にすることが保証されます)。

## <a name="iword"></a>  ios_base::iword

`iword` として格納される値を割り当てます。

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>パラメーター

*idx*<br/>
`iword` として格納する値のインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数は要素への参照を返します*idx* 、拡張可能な配列の型の要素の**長い**します。 すべての要素は、実質的に存在し、最初に値 0 を格納します。 返される参照は、オブジェクトの `iword` への次の呼び出し後、オブジェクトが **basic_ios::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt) への呼び出しで変更された後、またはオブジェクトが破棄された後に無効になります。

場合*idx*が負か、一意のストレージが、要素を使用できない場合、関数は[setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** し、一意でない可能性がありますの参照を返します。

`ios_base` 型のすべてのオブジェクト間で使用するための一意のインデックスを取得するには、[xalloc](#xalloc) を呼び出します。

### <a name="example"></a>例

`iword` の使用例については、「[xalloc](#xalloc)」を参照してください。

## <a name="openmode"></a>  ios_base::openmode

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

この型は、複数の iostreams オブジェクトのオープン モードを格納できるオブジェクトを記述する `bitmask type` です。 個々のフラグの値 (要素) は、次のとおりです。

- `app`、各挿入前にストリームの末尾にシークします。

- `ate`、コントロール オブジェクトが最初に作成されたときに、ストリームの末尾にシークします。

- `binary`、テキスト ストリームではなく、バイナリ ストリームとしてファイルを読み取る。

- `in`、ストリームからの抽出を許可するようにします。

- `out`、ストリームへの挿入を許可するようにします。

- `trunc`、そのコントロールのオブジェクトが作成されたときに、既存のファイルの内容を削除します。

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

## <a name="op_eq"></a>  ios_base::operator=

ios_base オブジェクトの代入演算子。

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>パラメーター

*right*<br/>
`ios_base` 型のオブジェクト。

### <a name="return-value"></a>戻り値

割り当て先のオブジェクト。

### <a name="remarks"></a>Remarks

この演算子は、格納されている書式設定情報をコピーして、任意の拡張可能な配列の新しいコピーを作成します。 その後、**\*this** を返します。 コールバックのスタックはコピーされません。

この演算子は、`ios_base` から派生したクラスでのみ使用されます。

## <a name="precision"></a>  ios_base::precision

浮動小数点数で表示する桁数を指定します。

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>パラメーター

*_Prec*<br/>
表示する有効桁数または固定小数点表記での小数点の後の桁数。

### <a name="return-value"></a>戻り値

1 番目のメンバー関数は、格納されている[表示桁数](../standard-library/ios-base-class.md)を返します。 2 番目のメンバー関数は *_Prec*表示桁数を返しますで、前の値を格納します。

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

## <a name="pword"></a>  ios_base::pword

`pword` として格納される値を割り当てます。

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>パラメーター

*_Idx*<br/>
`pword` として格納する値のインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数が要素 _ への参照を返します*Idx* 、拡張可能な配列の型の要素の**void**ポインター。 すべての要素は、実質的に存在し、最初に Null ポインターを格納します。 返される参照は、オブジェクトの `pword` への次の呼び出し後、オブジェクトが **basic_ios::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt) への呼び出しで変更された後、またはオブジェクトが破棄された後に無効になります。

_ *Idx* が負の場合または要素に一意の値が格納されていない場合、関数は [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** を呼び出し、一意ではない可能性がある参照を返します。

`ios_base` 型のすべてのオブジェクト間で使用するための一意のインデックスを取得するには、[xalloc](#xalloc) を呼び出します。

### <a name="example"></a>例

`pword` の使用例については、「[xalloc](#xalloc)」を参照してください。

## <a name="register_callback"></a>  ios_base::register_callback

コールバック関数を指定します。

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>パラメーター

*pfn*<br/>
コールバック関数へのポインター。

*idx*<br/>
ユーザー定義された番号。

### <a name="remarks"></a>Remarks

メンバー関数は、プッシュ、ペア`{pfn, idx}`格納されているコールバックのスタックに[コールバックのスタック](../standard-library/ios-base-class.md)します。 コールバック イベント**ev**報告されると、関数は、レジストリの逆の順序で式によって呼び出される、`(*pfn)(ev, *this, idx)`します。

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

## <a name="seekdir"></a> ios_base::seekdir

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

型は、いくつかの iostream クラスのメンバー関数への引数として使用される、自動選局 モードを格納できるオブジェクトを表す列挙型です。 次に、それぞれのフラグ値を示します。

- `beg`、シークする (変更の現在の読み取りまたは書き込み位置を) (配列、ストリーム、またはファイル) のシーケンスの先頭を基準とします。

- `cur`、シーク、シーケンス内の現在の位置を基準にします。

- `end`、シーケンスの末尾からの相対シークします。

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

## <a name="setf"></a> ios_base::setf

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

*マスク (_m)*<br/>
オンにするフラグ。

*_Unset*<br/>
オフにするフラグ。

### <a name="return-value"></a>戻り値

前の書式指定フラグ

### <a name="remarks"></a>Remarks

最初のメンバー関数は効果的に呼び出す[フラグ](#flags)( *\_マスク* &#124; *\_フラグ*) (選択したビットを設定する) を返します、前の書式設定フラグ。 2 番目のメンバー関数は効果的に呼び出す`flags(_Mask & fmtfl, flags & ~_Mask)`(選択されているビット マスクを置換) し、前の書式設定フラグを返します。

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

## <a name="sync_with_stdio"></a> ios_base::sync_with_stdio

iostream と C ランタイム ライブラリの処理が、ソース コードに現れる順序で実行されるようにします。

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>パラメーター

*_Sync*<br/>
すべてのストリームが同期しているかどうか`stdio`します。

### <a name="return-value"></a>戻り値

この関数の以前の設定。

### <a name="remarks"></a>Remarks

静的メンバー関数のストアを`stdio`同期フラグは、最初に**true**します。 ときに**true**、このフラグにより間で同じファイルでの操作が正しく同期されている、 [iostreams](../standard-library/iostreams-conventions.md)関数と C++ 標準ライブラリで定義されています。 それ以外の場合、同期が保証されませんはパフォーマンスが向上する可能性があります。 関数は *_Sync*で、`stdio`フラグを同期し、格納されている以前の値を返します。 標準ストリームに対するすべての操作を実行する前にのみに確実に呼び出すことができます。

## <a name="unsetf"></a> ios_base::unsetf

指定したフラグをオフにします。

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>パラメーター

*マスク (_m)*<br/>
オフにしたいフラグ。

### <a name="remarks"></a>Remarks

メンバー関数は、効果的に呼び出す[フラグ](#flags)(`~`*_Mask* **& フラグ**) (選択したビットをオフに)。

### <a name="example"></a>例

参照してください[ios_base::setf](#setf)を使用するサンプルの`unsetf`します。

## <a name="width"></a> ios_base::width

出力ストリームの長さを設定します。

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>パラメーター

*_Wide*<br/>
出力ストリームの必要なサイズ。

### <a name="return-value"></a>戻り値

現在の幅の設定。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、ストアド フィールドの幅を返します。 2 番目のメンバー関数は *_Wide*でフィールドの幅を返します前の値を格納します。

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

## <a name="xalloc"></a> ios_base::xalloc

変数は、ストリームの一部であることを指定します。

```cpp
static int xalloc( );
```

### <a name="return-value"></a>戻り値

静的メンバー関数は、呼び出しのたびにインクリメントされますが格納されている静的な値を返します。

### <a name="remarks"></a>Remarks

メンバー関数を呼び出すときに、一意のインデックスの引数として戻り値を使用することができます[iword](#iword)または[pword](#pword)します。

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

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
