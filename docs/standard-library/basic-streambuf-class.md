---
title: basic_streambuf クラス
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
ms.openlocfilehash: 1b43c2291499af87f2be1e5bec25717a30c28bfd
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688422"
---
# <a name="basic_streambuf-class"></a>basic_streambuf クラス

ストリームの特定の表現との相互間での要素の伝送を制御する、ストリーム バッファーを派生させるための抽象基底クラスについて説明します。

## <a name="syntax"></a>構文

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>パラメーター

*Elem* \
[char_type](#char_type)。

*Tr* \
文字の [traits_type](#traits_type)。

## <a name="remarks"></a>Remarks

クラステンプレートは、ストリームの特定の表現との間での要素の伝送を制御する、ストリームバッファーを派生させるための抽象基本クラスを記述します。 クラス `basic_streambuf` のオブジェクトは、 [char_type](#char_type)とも呼ばれる*Tr*型の要素を含むストリームを制御するのに役立ちます。この型の文字特性は、 [traits_type](#traits_type)とも呼ばれる[char_traits](../standard-library/char-traits-struct.md)クラスによって決まります。

各ストリーム バッファーは、抽出 (入力) 用ストリームと挿入 (出力) 用ストリームという 2 つの独立したストリームを概念上制御します。 ただし、特定の表現によってこれらのストリームのいずれか、もしくは両方がアクセス不可になる場合があります。 通常、そのような表現は、これら 2 つのストリームの何らかの関係を保持しています。 たとえば、[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> オブジェクトの出力ストリームに挿入したものが、その入力ストリームから後で抽出するものになります。 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> オブジェクトの 1 つのストリームを配置するときは、もう一方のストリームを直列に配置します。

クラステンプレートへのパブリックインターフェイス `basic_streambuf` は、すべてのストリームバッファーに共通する操作を提供します。ただし、特に特殊化されています。 保護されたインターフェイスでは、ストリームの特定の表現を動作させるのに必要な操作を行えます。 プロテクト仮想メンバー関数を使用することにより、ストリームの特定の表現に対する派生ストリーム バッファーの動作を調整できます。 このライブラリ内の各派生ストリーム バッファーで、各バッファーのプロテクト仮想メンバー関数に特殊化した動作方法について記述します。 基底クラスに対する既定の動作については (多くの場合、何の動作も発生しない)、このトピックで説明します。

残りのプロテクト メンバー関数は、ストリームとのバッファーのやり取りに提供されるストレージとのコピーのやり取りを制御します。 たとえば、入力バッファーには以下の特性を指定できます。

- [eback](#eback)、バッファーの先頭を指すポインター。

- [gptr](#gptr)、次に読み取る要素を指すポインター。

- [egptr](#egptr)、バッファーの末尾の直後を指すポインター。

同様に、出力バッファーには以下の特性を指定できます。

- [pbase](#pbase)、バッファーの先頭を指すポインター。

- [pptr](#pptr)、次に書き込む要素を指すポインター。

- [epptr](#epptr)、バッファーの末尾の直後を指すポインター。

どのバッファーの場合も、次のプロトコルが使用されます。

- ネクスト ポインターが null の場合、バッファーは存在しません。 それ以外の場合、3 つのポインターはすべて同じシーケンスを指し示します。 これらは順序で比較できます。

- 出力バッファーの場合、ネクスト ポインターの比較対象がエンド ポインター未満であれば、ネクスト ポインターで指定された書き込み位置に要素を格納できます。

- 入力バッファーの場合、ネクスト ポインターの比較対象がエンド ポインター未満であれば、ネクスト ポインターで指定された読み取り位置で要素を読み取ることができます。

- 入力バッファーの場合、開始ポインターの比較対象がネクスト ポインター未満であれば、デクリメントされたネクスト ポインターで指定された戻り位置の要素を戻すことができます。

`basic_streambuf`< `Elem`, `Tr`> の派生クラス用に作成するプロテクト仮想メンバー関数すべては、このプロトコルを維持する点で協調して動作する必要があります。

クラス `basic_streambuf`< `Elem`, `Tr`> のオブジェクトは、ここまでに説明した 6 つのポインターを格納します。 また、派生ストリーム バッファーが使用する可能性のある [locale](../standard-library/locale-class.md) 型のオブジェクトのロケール オブジェクトを格納します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_streambuf](#basic_streambuf)|`basic_streambuf` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|型名を `Elem` テンプレート パラメーターに関連付けます。|
|[int_type](#int_type)|`basic_streambuf` スコープ内の型名と `Elem` テンプレート パラメーターを関連付けます。|
|[off_type](#off_type)|`basic_streambuf` スコープ内の型名と `Elem` テンプレート パラメーターを関連付けます。|
|[pos_type](#pos_type)|`basic_streambuf` スコープ内の型名と `Elem` テンプレート パラメーターを関連付けます。|
|[traits_type](#traits_type)|型名を `Tr` テンプレート パラメーターに関連付けます。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[eback](#eback)|入力バッファーの先頭を指すポインターを返すプロテクト関数。|
|[egptr](#egptr)|入力バッファーの末尾の直後を指すポインターを返すプロテクト関数。|
|[epptr](#epptr)|出力バッファーの末尾の直後を指すポインターを返すプロテクト関数。|
|[gbump](#gbump)|`count` を入力バッファーのネクスト ポインターに追加するプロテクト関数。|
|[getloc](#getloc)|`basic_streambuf` オブジェクトのロケールを取得します。|
|[gptr](#gptr)|入力バッファーの次の要素を指すポインターを返すプロテクト関数。|
|[imbue](#imbue)|[pubimbue](#pubimbue) によって呼び出されるプロテクト仮想関数。|
|[in_avail](#in_avail)|バッファーから読み取る準備が整っている要素の数を返します。|
|[overflow](#overflow)|いっぱいのバッファーに新しい文字が挿入されたときに呼び出すことができる、プロテクト仮想関数。|
|[pbackfail](#pbackfail)|要素を入力ストリームに戻そうと試み、その要素を現在の要素に (ネクスト ポインターによって指されるように) するプロテクト仮想メンバー関数。|
|[pbase](#pbase)|出力バッファーの先頭を指すポインターを返すプロテクト関数。|
|[pbump](#pbump)|`count` を出力バッファーのネクスト ポインターに追加するプロテクト関数。|
|[pptr](#pptr)|出力バッファーの次の要素を指すポインターを返すプロテクト関数。|
|[pubimbue](#pubimbue)|`basic_streambuf` オブジェクトのロケールを設定します。|
|[pubseekoff](#pubseekoff)|派生クラスでオーバーライドされるプロテクト仮想関数 [seekoff](#seekoff) を呼び出します。|
|[pubseekpos](#pubseekpos)|派生クラスでオーバーライドされ、現在のポインターの位置をリセットするプロテクト仮想関数 [seekpos](#seekpos) を呼び出します。|
|[pubsetbuf](#pubsetbuf)|派生クラスでオーバーライドされるプロテクト仮想関数 [setbuf](#setbuf) を呼び出します。|
|[pubsync](#pubsync)|派生クラスでオーバーライドされ、このバッファーに関連付けられた外部ストリームを更新するプロテクト仮想関数 [sync](#sync) を呼び出します。|
|[sbumpc](#sbumpc)|ストリーム ポインターを移動させながら、現在の要素を読み取って返します。|
|[seekoff](#seekoff)|プロテクト仮想メンバー関数が、制御されているストリームの現在の位置を変更しようと試みます。|
|[seekpos](#seekpos)|プロテクト仮想メンバー関数が、制御されているストリームの現在の位置を変更しようと試みます。|
|[setbuf](#setbuf)|プロテクト仮想メンバー関数が、各派生ストリーム バッファーに固有の操作を実行します。|
|[setg](#setg)|開始ポインターの `_Gbeg`、ネクスト ポインターの `_Gnext`、およびエンド ポインターの `_Gend` を入力バッファー用に格納するプロテクト関数。|
|[setp](#setp)|開始ポインターの `_Pbeg` およびエンド ポインターの `_Pend` を出力バッファー用に格納するプロテクト関数。|
|[sgetc](#sgetc)|ストリーム内の位置を変更せずに、現在の要素を返します。|
|[sgetn](#sgetn)|読み取られる要素数を返します。|
|[showmanyc](#showmanyc)|入力ストリームから抽出できる文字数のカウントを返し、プログラムが無期限の待機状態にならないようにするプロテクト仮想メンバー関数。|
|[snextc](#snextc)|現在の要素を読み取り、次の要素を返します。|
|[sputbackc](#sputbackc)|`char_type` をストリームに渡します。|
|[sputc](#sputc)|ストリームに単一の文字を渡します。|
|[sputn](#sputn)|ストリームに文字列を渡します。|
|[stossc](#stossc)|ストリーム内の現在の要素の直後に移動します。|
|[sungetc](#sungetc)|ストリームから単一の文字を取得します。|
|[swap](#swap)|このオブジェクトの値を、指定した `basic_streambuf` オブジェクト パラメーターの値と交換します。|
|[sync](#sync)|制御されているストリームと関連付けられている外部ストリームとの同期を試みるプロテクト仮想関数。|
|[uflow](#uflow)|入力ストリームから現在の要素を抽出するプロテクト仮想関数。|
|[underflow](#underflow)|入力ストリームから現在の要素を抽出するプロテクト仮想関数。|
|[xsgetn](#xsgetn)|入力ストリームから要素を抽出するプロテクト仮想関数。|
|[xsputn](#xsputn)|出力ストリームに要素を挿入するプロテクト仮想関数。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|別の `basic_streambuf` オブジェクトの値をこのオブジェクトに割り当てます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<streambuf>

**名前空間:** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

`basic_streambuf` 型のオブジェクトを構築します。

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>パラメーター

*右*\
この `basic_streambuf` オブジェクトに値を設定するために使用される `basic_streambuf` オブジェクトへの左辺値参照。

### <a name="remarks"></a>Remarks

最初の保護されたコンストラクターは、入力バッファーと出力バッファーを制御するすべてのポインターに Null ポインターを格納します。 また、`locale::classic` をロケール オブジェクトに格納します。 詳細については、「[locale::classic](../standard-library/locale-class.md#classic)」を参照してください。

2番目のプロテクトコンストラクターは、ポインターとロケールを*右*からコピーします。

## <a name="char_type"></a>  basic_streambuf::char_type

型名を **Elem** テンプレート パラメーターに関連付けます。

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

入力バッファーの先頭を指すポインターを返すプロテクト関数。

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>戻り値

バッファーの先頭を指すポインター。

## <a name="egptr"></a>  basic_streambuf::egptr

入力バッファーの末尾の直後を指すポインターを返すプロテクト関数。

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>戻り値

入力バッファーの末尾の直後を指すポインター。

## <a name="epptr"></a>  basic_streambuf::epptr

出力バッファーの末尾の直後を指すポインターを返すプロテクト関数。

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>戻り値

出力バッファーの末尾の直後を指すポインター。

## <a name="gbump"></a>  basic_streambuf::gbump

入力バッファーの次のポインターに*カウント*を追加するプロテクト関数。

```cpp
void gbump(int count);
```

### <a name="parameters"></a>パラメーター

*カウント*\
マウス ポインターを進める量。

## <a name="getloc"></a>  basic_streambuf::getloc

basic_streambuf オブジェクトのロケールを取得します。

```cpp
locale getloc() const;
```

### <a name="return-value"></a>戻り値

格納されているロケール オブジェクト。

### <a name="remarks"></a>Remarks

関連情報については、「[ios_base::getloc](../standard-library/ios-base-class.md#getloc)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a>  basic_streambuf::gptr

入力バッファーの次の要素を指すポインターを返すプロテクト関数。

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>戻り値

入力バッファーの次の要素へのポインター。

## <a name="imbue"></a>  basic_streambuf::imbue

[pubimbue](#pubimbue) によって呼び出されるプロテクト仮想関数。

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
ロケールへの参照。

### <a name="remarks"></a>Remarks

既定の動作では、何も行いません。

## <a name="in_avail"></a>  basic_streambuf::in_avail

バッファーから読み取る準備が整っている要素の数を返します。

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>戻り値

バッファーから読み取る準備が整っている要素の数。

### <a name="remarks"></a>Remarks

[読み取り位置](../standard-library/basic-streambuf-class.md)が使用可能な場合、メンバー関数は[egptr](#egptr)  - [gptr](#gptr)を返します。 それ以外の場合は、[showmanyc](#showmanyc) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a>  basic_streambuf::int_type

basic_streambuf スコープ内の型名をテンプレート パラメーター内の型のいずれかと関連付けます。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

basic_streambuf スコープ内の型名をテンプレート パラメーター内の型のいずれかと関連付けます。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator=

別の `basic_streambuf` オブジェクトの値をこのオブジェクトに割り当てます。

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>パラメーター

*右*\
このオブジェクトに値を代入するために使用される `basic_streambuf` オブジェクトへの左辺値参照。

### <a name="remarks"></a>Remarks

プロテクトメンバー演算子は、入力バッファーと出力バッファーを制御するポインターを*右*からコピーします。 また、`right.`[getloc()](#getloc) を `locale object` に格納します。 `*this` を返します。

## <a name="overflow"></a>  basic_streambuf::overflow

いっぱいのバッファーに新しい文字が挿入されたときに呼び出すことができる、プロテクト仮想関数。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>パラメーター

*メタ \ (_s)*
バッファーまたは **traits_type::** [eof](../standard-library/char-traits-struct.md#eof) に挿入する文字。

### <a name="return-value"></a>戻り値

関数は失敗すると、**traits_type::eof** を返すか、例外をスローします。 それ以外の場合は、**traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*) を返します。 既定の動作では、**traits_type::eof** を返します。

### <a name="remarks"></a>Remarks

*@No__t_1Meta*が**traits_type:: eof**と等しくない場合、プロテクト仮想メンバー関数は、要素**traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_Meta*) を出力ストリームに挿入しようとします。 これはさまざまな方法で行うことができます。

- `write position` が使用可能な場合は、書き込み位置に要素を格納し、出力バッファーのネクスト ポインターをインクリメントできます。

- 新しい記憶域または追加の記憶域を出力バッファーに割り当てることで、書き込み位置を使用可能にすることができます。

- 出力バッファーの先頭とネクスト ポインターの間の一部またはすべての要素をいくつかの外部の宛先に書き出すことで、書き込み位置を使用可能にすることができます。

仮想オーバーフロー関数は [sync](#sync) 関数と [underflow](#underflow) 関数とともに、streambuf から派生したクラスの特性を定義します。 派生した各クラスは、オーバーフローを異なる方法で実装できますが、呼び出すストリーム クラスとのインターフェイスは同じです。

`overflow` 関数は、put 領域がいっぱいの時に `sputc` や `sputn` のようなパブリック `streambuf` 関数で最も頻繁に呼び出されますが、ストリーム クラスなどのその他のクラスはいつでも `overflow` を呼び出すことができます。

関数は、`pbase` ポインターと `pptr` ポインター間の put 領域内の文字を使用し、put 領域を再初期化します。 `overflow` 関数は、(`nCh` が `EOF` ではない場合は) `nCh` も使用する必要があります。または、次の呼び出しで使用されるように新しい put 領域に文字を配置することもできます。

消費の定義は、派生クラスによって異なります。 たとえば、`filebuf` クラスが文字をファイルに書き込むのに対し、`strstreambuf` クラスは、文字をそのバッファーに保持して、(バッファーが動的として指定されている場合は) オーバーフローへの呼び出しに応えてバッファーを拡張します。 この拡張は、古いバッファーを解放して、新しいより大きなバッファーで置換することで実現されます。 ポインターは必要に応じて調整されます。

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

要素を入力ストリームに戻そうと試み、その要素を現在の要素に (ネクスト ポインターによって指されるように) するプロテクト仮想メンバー関数。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>パラメーター

*メタ \ (_s)*
バッファーまたは **traits_type::** [eof](../standard-library/char-traits-struct.md#eof) に挿入する文字。

### <a name="return-value"></a>戻り値

関数は失敗すると、**traits_type::eof** を返すか、例外をスローします。 それ以外の場合、関数は別の値を返します。 既定の動作では、**traits_type::eof** を返します。

### <a name="remarks"></a>Remarks

*@No__t_1Meta*が**traits_type:: eof**と等しい場合、プッシュバックする要素は、実際には、現在の要素の前に既にストリームにある要素になります。 それ以外の場合、その要素は**traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_Meta*) に置き換えられます。 この関数は、さまざまな方法で要素を戻すことができます。

- 戻り位置が使用可能な場合は、戻り位置に要素を格納し、入力バッファーのネクスト ポインターをデクリメントできます。

- 新しい記憶域または追加の記憶域を入力バッファーに割り当てることで、戻り位置を使用可能にすることができます。

- 一般的な入力ストリームと出力ストリームがあるストリーム バッファーの場合、出力バッファーの先頭とネクスト ポインターの間の一部またはすべての要素をいくつかの外部の宛先に書き出すことで、戻り位置を使用可能にすることができます。

## <a name="pbase"></a>  basic_streambuf::pbase

出力バッファーの先頭を指すポインターを返すプロテクト関数。

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>戻り値

出力バッファーの先頭を指すポインター。

## <a name="pbump"></a>  basic_streambuf::pbump

出力バッファーの次のポインターに*カウント*を追加するプロテクト関数。

```cpp
void pbump(int count);
```

### <a name="parameters"></a>パラメーター

*カウント*\
書き込み位置を前方に移動する文字数。

## <a name="pos_type"></a>  basic_streambuf::pos_type

basic_streambuf スコープ内の型名をテンプレート パラメーター内の型のいずれかと関連付けます。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

出力バッファーの次の要素を指すポインターを返すプロテクト関数。

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>戻り値

出力バッファーの次の要素を指すポインター。

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

basic_streambuf オブジェクトのロケールを設定します。

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
ロケールへの参照。

### <a name="return-value"></a>戻り値

ロケール オブジェクトに格納されている以前の値。

### <a name="remarks"></a>Remarks

メンバー関数は、_ *Loc* をロケール オブジェクトに格納し、[imbue](#imbue) を呼び出します。

### <a name="example"></a>例

`pubimbue` の使用例については、「[basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)」を参照してください。

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

派生クラスでオーバーライドされるプロテクト仮想関数 [seekoff](#seekoff) を呼び出します。

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
に対して相対的にシークする*位置。*

@No__t_1*方法 (_d)*
オフセット演算の開始位置。 有効値については、「[seekdir](../standard-library/ios-base-class.md#seekdir)」を参照してください。

*@No__t_1*
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

新しい位置または無効なストリーム位置 ( [seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`) ) を返します。

### <a name="remarks"></a>Remarks

ポインターを相対*方向*に移動します。

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

派生クラスでオーバーライドされ、現在のポインターの位置をリセットするプロテクト仮想関数 [seekpos](#seekpos) を呼び出します。

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*Sp \ (_s)*
シークする位置。

*@No__t_1*
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

新しい位置または無効なストリーム位置。 ストリームの位置が無効であることを確認するには、戻り値と `pos_type(off_type(-1))` を比較します。

### <a name="remarks"></a>Remarks

このメンバー関数は、[seekpos](#seekpos)(_ *Sp*, `_Which`) を返します。

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

派生クラスでオーバーライドされるプロテクト仮想関数 [setbuf](#setbuf) を呼び出します。

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*バッファーの \ (_l)*
このインスタンス化の `char_type` を指すポインター。

*カウント*\
バッファーのサイズ。

### <a name="return-value"></a>戻り値

[setbuf](#setbuf)( `_Buffer`, `count`) を返します。

## <a name="pubsync"></a>  basic_streambuf::pubsync

派生クラスでオーバーライドされ、このバッファーに関連付けられた外部ストリームを更新するプロテクト仮想関数 [sync](#sync) を呼び出します。

```cpp
int pubsync();
```

### <a name="return-value"></a>戻り値

[同期](#sync)を返します。失敗した場合は-1 を返します。

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

ストリーム ポインターを移動させながら、現在の要素を読み取って返します。

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>戻り値

現在の要素。

### <a name="remarks"></a>Remarks

読み取り位置が使用可能な場合、メンバー関数は **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong>[gptr](#gptr)) を返し、入力バッファーのネクスト ポインターをインクリメントします。 それ以外の場合は、[uflow](#uflow) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Input
3
```

```Output
33
51
```

## <a name="seekoff"></a>  basic_streambuf::seekoff

制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*オフ \ (_r)*
に対して相対的にシークする*位置。*

@No__t_1*方法 (_d)*
オフセット演算の開始位置。 有効値については、「[seekdir](../standard-library/ios-base-class.md#seekdir)」を参照してください。

*@No__t_1*
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

新しい位置または無効なストリーム位置 ( `seekoff` (_ *Off*, `_Way`, `_Which`) ) を返します。

### <a name="remarks"></a>Remarks

新しい位置は、次のように決定されます。

- `_Way` == `ios_base::beg` の場合、新しい位置はストリームの先頭と _ *Off* です。

- `_Way` == `ios_base::cur` の場合、新しい位置は現在のストリームの位置と _ *Off* です。

- `_Way` == `ios_base::end` の場合、新しい位置はストリームの最後と _ *Off* です。

通常、**which & ios_base::in** が 0 以外の場合、入力ストリームが影響を受け、**which & ios_base::out** が 0 以外の場合、出力ストリームが影響を受けます。 ただし、このパラメーターの実際の使用は、派生ストリーム バッファー間で異なります。

関数はストリームの位置の変更に成功すると、結果のストリームの位置を返します。複数の位置の変更に成功した場合は、結果のストリームの位置のうちの 1 つを返します。 それ以外の場合は、無効なストリームの位置が返されます。 既定の動作では、無効なストリームの位置を返します。

## <a name="seekpos"></a>  basic_streambuf::seekpos

制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*Sp \ (_s)*
シークする位置。

*@No__t_1*
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

新しい位置または無効なストリーム位置。 ストリームの位置が無効であることを確認するには、戻り値と `pos_type(off_type(-1))` を比較します。

### <a name="remarks"></a>Remarks

新しい位置は _ *Sp* です。

通常、**which & ios_base::in** が 0 以外の場合、入力ストリームが影響を受け、**which & ios_base::out** が 0 以外の場合、出力ストリームが影響を受けます。 ただし、このパラメーターの実際の使用は、派生ストリーム バッファー間で異なります。

関数はストリームの位置の変更に成功すると、結果のストリームの位置を返します。複数の位置の変更に成功した場合は、結果のストリームの位置のうちの 1 つを返します。 それ以外の場合は、無効なストリームの位置 (-1) を返します。 既定の動作では、無効なストリームの位置を返します。

## <a name="setbuf"></a>  basic_streambuf::setbuf

各派生ストリーム バッファーに固有の操作を実行するプロテクト仮想メンバー関数。

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*バッファーの \ (_l)*
バッファーへのポインター。

*カウント*\
バッファーのサイズ。

### <a name="return-value"></a>戻り値

既定の動作では、**this** が返されます。

### <a name="remarks"></a>Remarks

「[basic_filebuf](../standard-library/basic-filebuf-class.md)」を参照してください。 `setbuf` は `streambuf` オブジェクトが使用するメモリ領域を提供します。 派生クラス内の定義でのバッファーの使用方法。

## <a name="setg"></a>  basic_streambuf::setg

開始ポインターの _ *Gbeg*、ネクスト ポインターの `_Gnext`、およびエンド ポインターの `_Gend` を入力バッファー用に格納するプロテクト関数。

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>パラメーター

*_Gbeg* \
バッファーの先頭を指すポインター。

*次の \ (_s)*
バッファーの中心付近を指すポインター。

*Gend \ (_c)*
バッファーの末尾を指すポインター。

## <a name="setp"></a>  basic_streambuf::setp

*_Pbeg*を開始ポインターに格納し、出力バッファーのエンドポインターで*保留*するプロテクト関数。

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>パラメーター

*_Pbeg* \
バッファーの先頭を指すポインター。

*保留 \ (_r)*
バッファーの末尾を指すポインター。

## <a name="sgetc"></a>  basic_streambuf::sgetc

ストリーム内の位置を変更せずに、現在の要素を返します。

```cpp
int_type sgetc();
```

### <a name="return-value"></a>戻り値

現在の要素。

### <a name="remarks"></a>Remarks

読み取り位置が使用可能な場合、メンバー関数は **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr)) を返します。 それ以外の場合は、[underflow](#underflow) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a>  basic_streambuf::sgetn

最大文字*数*を入力バッファーから抽出し、指定されたバッファー *ptr*に格納します。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*ptr* \
抽出した文字を格納するバッファー。

*カウント*\
読み取られる要素数。

### <a name="return-value"></a>戻り値

読み取られる要素数。 詳細については、「[streamsize](../standard-library/ios-typedefs.md#streamsize)」を参照してください。

### <a name="remarks"></a>Remarks

このメンバー関数は [xsgetn](#xsgetn)( `ptr`, `count`) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

入力ストリームから抽出できる文字数のカウントを返し、プログラムが無期限の待機状態にならないようにするプロテクト仮想メンバー関数。

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>戻り値

既定の動作では、0 が返されます。

## <a name="snextc"></a>  basic_streambuf::snextc

現在の要素を読み取り、次の要素を返します。

```cpp
int_type snextc();
```

### <a name="return-value"></a>戻り値

ストリームの次の要素。

### <a name="remarks"></a>Remarks

メンバー関数は [sbumpc](#sbumpc) を呼び出し、その関数が **traits_type::** [eof](../standard-library/char-traits-struct.md#eof) を返す場合には、**traits_type::eof** を返します。 それ以外の場合は、[sgetc](#sgetc) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Input
aa
```

```Output
aa97
```

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

ストリームに char_type を配置します。

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>パラメーター

*Ch \ (_s)*
文字。

### <a name="return-value"></a>戻り値

文字またはエラーを返します。

### <a name="remarks"></a>Remarks

戻り位置が使用可能であり、その位置に格納されている文字と等しいかどうか*を比較する*場合、メンバー関数は、入力バッファーの次のポインターをデクリメントし、 **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`) を返します。 それ以外の場合は、[pbackfail](#pbackfail)( `_Ch`) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a>  basic_streambuf::sputc

ストリームに単一の文字を渡します。

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>パラメーター

*Ch \ (_s)*
文字。

### <a name="return-value"></a>戻り値

正常終了した場合は、文字を返します。

### <a name="remarks"></a>Remarks

@No__t_0 が使用可能な場合、メンバー関数は、書き込み位置に " *Ch* " を格納し、出力バッファーの次のポインターをインクリメントして、 **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`) を返します。 それ以外の場合は、[overflow](#overflow)( `_Ch`) を返します。

### <a name="example"></a>例

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a>  basic_streambuf::sputn

ストリームに文字列を渡します。

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>パラメーター

*ptr* \
文字列。

*カウント*\
文字数。

### <a name="return-value"></a>戻り値

ストリームに実際に挿入された文字数。

### <a name="remarks"></a>Remarks

このメンバー関数は [xsputn](#xsputn)( `ptr`, `count`) を返します。 詳細については、このメンバーの「コメント」セクションを参照してください。

### <a name="example"></a>例

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a>  basic_streambuf::stossc

ストリーム内の現在の要素の直後に移動します。

```cpp
void stossc();
```

### <a name="remarks"></a>Remarks

メンバー関数は、[sbumpc](#sbumpc) を呼び出します。 このメンバー関数を指定するために実装は不要です。

### <a name="example"></a>例

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a>  basic_streambuf::sungetc

ストリームから単一の文字を取得します。

```cpp
int_type sungetc();
```

### <a name="return-value"></a>戻り値

文字またはエラーを返します。

### <a name="remarks"></a>Remarks

戻り位置が使用可能な場合、メンバー関数は入力バッファーのネクスト ポインターをデクリメントし、`traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr)) を返します。 ただし、現在のバッファーの状態でキャプチャできるように、読み取る最後の文字を判断できない場合もあります。 この場合、関数は [pbackfail](#pbackfail) を返します。 このような状況を避けるためには、戻す文字を追跡し、`sputbackc(ch)` を呼び出します。これはストリームの先頭で呼び出さず、複数の文字を戻そうとしなければ、失敗しません。

### <a name="example"></a>例

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a>  basic_streambuf::swap

このオブジェクトの値を、指定した `basic_streambuf` オブジェクトの値と交換します。

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|値を交換するために使用される `basic_streambuf` オブジェクトの左辺値参照。|

### <a name="remarks"></a>Remarks

プロテクトメンバー関数は、`input buffer` と `output buffer` を制御するすべてのポインターを*右*に交換します。 `right.`[getloc()](#getloc) も `locale` オブジェクトと交換します。

## <a name="sync"></a>  basic_streambuf::sync

制御されているストリームと関連付けられている外部ストリームとの同期を試みるプロテクト仮想関数。

```cpp
virtual int sync();
```

### <a name="return-value"></a>戻り値

関数が失敗すると、-1 を返します。 既定の動作では、0 が返されます。

### <a name="remarks"></a>Remarks

`sync` には出力バッファーの開始ポインターとネクスト ポインター間の任意の要素の記述が必要です。 入力バッファーのネクスト ポインターとエンド ポインター間の任意の要素を戻す必要はありません。

## <a name="traits_type"></a>  basic_streambuf::traits_type

型名を **Tr** テンプレート パラメーターに関連付けます。

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

入力ストリームから現在の要素を抽出するプロテクト仮想関数。

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>戻り値

現在の要素。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、現在の要素 **ch** を入力バッファーから抽出しようとし、現在のストリームの位置を進め、**traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**) として要素を返します。 これはさまざまな方法で行うことができます。

- 読み取り位置が使用可能な場合は、読み取り位置に格納されている要素として **ch** を使用し、入力バッファーのネクスト ポインターを進めます。

- いくつかの外部ソースから直接、要素を読み取り、それを値 **ch** として配付できます。

- 一般的な入力ストリームと出力ストリームがあるストリーム バッファーの場合、出力バッファーの先頭とネクスト ポインターの間の一部またはすべての要素をいくつかの外部の宛先に書き出すことで、読み取り位置を使用可能にすることができます。 または、入力バッファーに新しい記憶域または追加の記憶域を割り当てることができます。 その後、関数はいくつかの外部ソースから 1 つまたは複数の要素を読み取ります。

関数は失敗すると、**traits_type::** [eof](../standard-library/char-traits-struct.md#eof) を返すか、例外をスローします。 それ以外の場合、上記のように変換された入力ストリームの現在の要素 `ch` を返して、入力バッファーのネクスト ポインターを進めます。 既定の動作では、[underflow](#underflow) を呼び出し、その関数が **traits_type::eof** を返す場合は、**traits_type::eof** を返します。 それ以外の場合、関数は上記のように変換された入力ストリームの現在の要素 **ch** を返して、入力バッファーのネクスト ポインターを進めます。

## <a name="underflow"></a>  basic_streambuf::underflow

入力ストリームから現在の要素を抽出するプロテクト仮想関数。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>戻り値

現在の要素。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、現在のストリームの位置を進めずに現在の要素 **ch** を入力ストリームから抽出しようとし、それを `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**) として返します。 これはさまざまな方法で行うことができます。

- 読み取り位置が使用可能な場合、**ch** は読み取り位置に格納されている要素です。 この詳細については、[basic_streambuf クラス](../standard-library/basic-streambuf-class.md)の「コメント」セクションを参照してください。

- 新しい記憶域または追加の記憶域を入力バッファーに割り当てた後に、いくつかの外部ソースから 1 つまたは複数の要素を読み取ることで、読み取り位置を使用可能にすることができます。 この詳細については、[basic_streambuf クラス](../standard-library/basic-streambuf-class.md)の「コメント」セクションを参照してください。

関数は失敗すると、`traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` を返すか、例外をスローします。 それ以外の場合、上記のように変換された入力ストリームの現在の要素が返されます。 既定の動作では、`traits_type::eof()` が返されます。

仮想 `underflow` 関数は [sync](#sync) 関数と [overflow](#overflow) 関数とともに、`streambuf` から派生したクラスの特性を定義します。 派生した各クラスは、`underflow` を異なる方法で実装できますが、呼び出すストリーム クラスとのインターフェイスは同じです。

`underflow` 関数は、get 領域が空のときに [sgetc](#sgetc) や [sgetn](#sgetn) のようなパブリック `streambuf` 関数で最も頻繁に呼び出されますが、ストリーム クラスなどのその他のクラスはいつでも `underflow` を呼び出すことができます。

`underflow` 関数は get 領域に入力ソースからの文字を提供します。 get 領域に文字が含まれている場合、`underflow` は最初の文字を返します。 get 領域が空の場合、get 領域をいっぱいにして次の文字を返します (これは get 領域に残ります)。 これ以上使用できる文字がない場合には、`underflow` は `EOF` を返し、get 領域を空のままにします。

`strstreambuf` クラスでは、`underflow` は [egptr](#egptr) ポインターを調整して、`overflow` への呼び出しによって動的に割り当てられたストレージにアクセスします。

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

入力ストリームから要素を抽出するプロテクト仮想関数。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*ptr* \
抽出した文字を格納するバッファー。

*カウント*\
抽出する要素数。

### <a name="return-value"></a>戻り値

抽出された要素の数。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、 [sbumpc](#sbumpc)を繰り返し呼び出した場合と同じように、入力ストリームから最大*数*の要素を抽出し、それらを*ptr*で始まる配列に格納します。 実際に抽出された要素の数を返します。

## <a name="xsputn"></a>  basic_streambuf::xsputn

出力ストリームに要素を挿入するプロテクト仮想関数。

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>パラメーター

*ptr* \
挿入する要素へのポインター。

*カウント*\
挿入する要素の数。

### <a name="return-value"></a>戻り値

ストリームに実際に挿入された要素の数。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、 *ptr*から始まる配列から、 [sputc](#sputc)を繰り返し呼び出した場合と同じように、最大*数*の要素を出力ストリームに挿入します。 すべての*カウント*文字が書き込まれるか、または `sputc( count)` を呼び出すと `traits::eof()` が返されると、出力ストリームへの文字の挿入は停止します。 実際に挿入された要素の数を返します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
