---
title: strstreambuf クラス
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: 75c9a96b727ef60280055536296f850f492d16ac
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327305"
---
# <a name="strstreambuf-class"></a>strstreambuf クラス

要素に格納されている要素のシーケンスとの間の転送を制御するストリーム バッファーについて説明します、 **char**配列オブジェクト。

## <a name="syntax"></a>構文

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Remarks

オブジェクトの構築方法に応じて、シーケンスにおける変更に対応できるように割り当て、拡張、解放を必要に応じて行えます。

クラス `strstreambuf` のオブジェクトは、`strstreambuf` モードのモード情報が入っているいくつかのビットを格納します。 これらのビットは、制御対象シーケンスに関して次の情報を示します。

- 割り当てがなされていて、最終的に解放する必要があるかどうか。

- 変更可能かどうか。

- 記憶域の再割り当てによって拡張可能かどうか。

- 操作できないようにされていて、オブジェクトを破棄する前に操作できるようにする必要があるかどうか、またはオブジェクト以外のエージェンシーで解放する必要があるかどうか (割り当てがなされている場合)。

操作できないようにされている制御対象シーケンスは、これらの別個のモード ビットに関係なく、変更も拡張もできません。

またオブジェクトは、`strstreambuf` 割り当てを制御する 2 つの関数へのポインターも格納します。 これらが null ポインターである場合、オブジェクトは制御対象シーケンスに対して記憶域の割り当ておよび解放を行う独自のメソッドを考案します。

> [!NOTE]
> このクラスは非推奨とされます。 代わりに [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) または [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf) を使用することを検討してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[strstreambuf](#strstreambuf)|`strstreambuf` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[freeze](#freeze)|ストリーム バッファーの操作により、ストリーム バッファーを使用不可にします。|
|[overflow](#overflow)|いっぱいのバッファーに新しい文字が挿入されたときに呼び出すことができる、プロテクト仮想関数。|
|[pbackfail](#pbackfail)|要素を入力ストリームに戻してから、その要素を現在の要素 (ネクスト ポインターによって指される) にしようとするプロテクト仮想メンバー関数。|
|[pcount](#pcount)|被制御シーケンスに書き込まれる要素の数を返します。|
|[seekoff](#seekoff)|制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。|
|[seekpos](#seekpos)|制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。|
|[str](#str)|[freeze](#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。|
|[underflow](#underflow)|入力ストリームから現在の要素を抽出するプロテクト仮想関数。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<strstream>

**名前空間:** std

## <a name="freeze"></a>  strstreambuf::freeze

ストリーム バッファーの操作により、ストリーム バッファーを使用不可にします。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>パラメーター

*_Freezeit*<br/>
A **bool**ストリームを停止するかどうかを示します。

### <a name="remarks"></a>Remarks

場合 *_Freezeit*が true の場合、この関数は、格納されている変更`strstreambuf`モードが固定されている被制御シーケンスを変更します。 それ以外の場合、被制御シーケンスは固定されません。

[str](#str) は `freeze` を意味します。

> [!NOTE]
> 固定されたバッファーは、`strstreambuf` の破棄中には解放されません。 メモリ リークを避けるために、バッファーを解放する前に固定解除する必要があります。

### <a name="example"></a>例

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="overflow"></a>  strstreambuf::overflow

いっぱいのバッファーに新しい文字が挿入されたときに呼び出すことができる、プロテクト仮想関数。

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>パラメーター

*_Meta*<br/>
バッファーに挿入する文字または `EOF`。

### <a name="return-value"></a>戻り値

関数が成功しない場合は、`EOF` が返されます。 の場合 *\_メタ*  == `EOF`、他にもいくつかの値を返します`EOF`します。 返しますそれ以外の場合、 *\_メタ*します。

### <a name="remarks"></a>Remarks

場合 *\_メタ* ! = `EOF`、プロテクト仮想メンバー関数は、要素を挿入しようとする`(char)_Meta`出力バッファーにします。 これはさまざまな方法で行うことができます。

- 書き込み位置が使用可能な場合は、書き込み位置に要素を格納し、出力バッファーの次のポインターをインクリメントできます。

- 格納されている strstreambuf モードによって被制御シーケンスが変更可能、拡張可能で、固定されていないことが示されている場合、この関数は出力バッファーに新規に割り当てることによって書き込み位置を使用可能にできます。 このように出力バッファーを拡張すると、関連付けられているすべての入力バッファーも拡張されます。

## <a name="pbackfail"></a>  strstreambuf::pbackfail

要素を入力ストリームに戻してから、その要素を現在の要素に (次のポインターによって指されるように) しようとするプロテクト仮想メンバー関数。

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>パラメーター

*_Meta*<br/>
バッファーに挿入する文字または `EOF`。

### <a name="return-value"></a>戻り値

関数が成功しない場合は、`EOF` が返されます。 の場合 *\_メタ*  == `EOF`、他にもいくつかの値を返します`EOF`します。 返しますそれ以外の場合、 *\_メタ*します。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数が要素を入力バッファーに戻そうと試み、その要素を現在の要素に (次のポインターによって指されるように) します。

場合 *\_メタ* == `EOF`、プッシュ バックする要素が既に現在の要素より前に、のストリームで 1 つでは効果的にします。 それ以外の場合、その要素は置き換えられます`ch = (char)_Meta`します。 この関数は、さまざまな方法で要素を戻すことができます。

- 戻り位置が使用してに格納されている要素が等しい場合`ch`、入力バッファーのネクスト ポインターをデクリメントできます。

- 戻り位置が使用可能なと関数に格納できる場合は、strstreambuf モードによると、被制御シーケンスは変更可能な場合`ch`戻り位置に、入力バッファーのネクスト ポインターをデクリメントします。

## <a name="pcount"></a>  strstreambuf::pcount

被制御シーケンスに書き込まれる要素の数を返します。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>戻り値

被制御シーケンスに書き込まれる要素の数。

### <a name="remarks"></a>Remarks

具体的には、[pptr](../standard-library/basic-streambuf-class.md#pptr) が Null ポインターの場合、この関数はゼロを返します。 返しますそれ以外の場合、 `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)します。

### <a name="example"></a>例

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="seekoff"></a>  strstreambuf::seekoff

制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*_Off*<br/>
に対して相対的にシークする位置 *_Way*します。

*_Way*<br/>
オフセット演算の開始位置。 有効値については、「[seekdir](../standard-library/ios-base-class.md#seekdir)」を参照してください。

*_Which*<br/>
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

いずれかまたは両方のストリームの位置を変更することで、関数が成功すると、結果のストリームの位置が返されます。 それ以外の場合は、失敗し、無効なストリームの位置が返されます。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数が、制御対象ストリームの現在の位置を変更しようと試みます。 クラス strstreambuf のオブジェクトの場合、ストリームの位置がストリーム オフセットのみで構成されます。 オフセット ゼロは、被制御シーケンスの最初の要素を指定します。

新しい位置は、次のように決定されます。

- 場合`_Way == ios_base::beg`、新しい位置はプラス ストリームの先頭 *_Off*します。

- 場合`_Way == ios_base::cur`、新しい位置は、現在のストリームの位置と *_Off*します。

- 場合`_Way == ios_base::end`、プラス ストリームの末尾が新しい位置 *_Off*します。

場合`_Which & ios_base::in`0 以外の場合は、この関数は、次に、入力バッファーに読み取る位置を変更、入力バッファーが存在します。 場合`_Which & ios_base::out`が 0 以外の場合、また`_Way != ios_base::cur`、出力バッファーが存在して、この関数は、次に読み取る位置に一致するように記述する次の位置を設定します。

の場合`_Which & ios_base::out`0 以外の場合は、出力バッファーが存在して、、、この関数は、次に、出力バッファーに書き込む位置を変更します。 それ以外の場合、配置操作が失敗します。 配置操作を正常に完了するためには、結果のストリームの位置が被制御シーケンス内になければなりません。

## <a name="seekpos"></a>  strstreambuf::seekpos

制御対象ストリームの現在の位置を変更しようと試みるプロテクト仮想メンバー関数。

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*_Sp*<br/>
シークする位置。

*_Which*<br/>
ポインター位置のモードを指定します。 既定では、読み取り位置および書き込み位置を変更できます。

### <a name="return-value"></a>戻り値

いずれかまたは両方のストリームの位置を変更することで、関数が成功すると、結果のストリームの位置が返されます。 それ以外の場合は、失敗し、無効なストリームの位置が返されます。 ストリームの位置が無効であることを確認するには、戻り値と `pos_type(off_type(-1))` を比較します。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数が、制御対象ストリームの現在の位置を変更しようと試みます。 クラス strstreambuf のオブジェクトの場合、ストリームの位置がストリーム オフセットのみで構成されます。 オフセット ゼロは、被制御シーケンスの最初の要素を指定します。 新しい位置によって決まり *_Sp*します。

`_Which` & **ios_base::in** が 0 以外であり、入力バッファーが存在する場合、この関数は次の位置を変更して入力バッファーに読み取ります。 `_Which` & `ios_base::out` が 0 以外であり、出力バッファーが存在する場合、この関数は、次の位置を設定して読み取る次の位置に一致するように書き込みます。 それ以外の場合、`_Which` & `ios_base::out` が 0 以外であり、出力バッファーが存在する場合、この関数は次の位置を変更して出力バッファーに書き込みます。 それ以外の場合、配置操作が失敗します。 配置操作を正常に完了するためには、結果のストリームの位置が被制御シーケンス内になければなりません。

## <a name="str"></a>  strstreambuf::str

[freeze](#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。

```cpp
char *str();
```

### <a name="return-value"></a>戻り値

被制御シーケンスの先頭へのポインター。

### <a name="remarks"></a>Remarks

明示的に挿入しない場合、終端の null 要素は存在しません。

### <a name="example"></a>例

**str** の使用例は、「[strstreambuf::freeze](#freeze)」を参照してください。

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

`strstreambuf` 型のオブジェクトを構築します。

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>パラメーター

*_Allocfunc*<br/>
バッファー メモリの割り当てに使用される関数。

*count*<br/>
指し示されるバッファーの長さを決定 *_Getptr*します。 場合 *_Getptr*引数ではない (最初のコンス トラクター フォーム)、割り当ての提案がバッファーのサイズします。

*_Freefunc*<br/>
バッファー メモリを解放するために使用する関数。

*_Getptr*<br/>
入力に使用するバッファー。

*_Putptr*<br/>
出力に使用するバッファー。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、入力バッファー、出力バッファー、および strstreambuf 割り当てを制御するすべてのポインターに Null ポインターを格納します。 被制御シーケンスを変更および拡張できるように、ストアド strstreambuf モードに設定します。 受け入れます。*カウント*提案される初期割り当てサイズとして。

格納する点を除いて、最初のように 2 つ目のコンス トラクターは、動作 *\_Allocfunc*記憶域の割り当てするために呼び出す関数へのポインターとしてと *\_Freefunc*ポインターとしてストレージを解放するために呼び出す関数。

3 つのコンストラクター:

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

これらは、`_Getptr` が被制御シーケンスを保持するために使用する配列オブジェクトを指定する点を除いて、最初のコンストラクターのように動作します。 (したがって、Null ポインターにすることはできません。)配列内の要素の数 *N* は、次のように決定されます。

- 場合 (`count` > 0)、し*N*は`count`します。

- 場合 (`count` 0 を = =)、し*N*は`strlen`(( **const** `char` *) `_Getptr` )。

- 場合 (`count` < 0)、し*N*は**INT_MAX**します。

`_Putptr` が Null ポインターの場合、関数は次を実行することによって入力バッファーだけを確立します。

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

それ以外の場合、次を実行することによって入力と出力の両方のバッファーを確立します。

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

この場合、`_Putptr` は間隔 [ `_Getptr`, `_Getptr` + *N*] 内である必要があります。

最後に、3 つのコンストラクターを示します。

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

すべて次と同様に動作します。

```cpp
streambuf((char *)_Getptr, count);
```

ストアド モードによって被制御シーケンスが変更可能にも拡張可能にもならない点を除きます。

## <a name="underflow"></a>  strstreambuf::underflow

入力ストリームから現在の要素を抽出するプロテクト仮想関数。

```cpp
virtual int underflow();
```

### <a name="return-value"></a>戻り値

関数が成功しない場合は、`EOF` が返されます。 それ以外の場合、上記のように変換された入力ストリームの現在の要素が返されます。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、現在の要素を抽出しようと`ch`は入力バッファーから現在のストリームの位置を進める、およびとして要素を返します (`int`) (`unsigned char`) **ch**します。 1 つの方法で行うことができます。 かかる読み取り位置が使用可能な場合は、`ch`要素は、読み取り位置に格納されていると、入力バッファーのネクスト ポインターを進めます。

## <a name="see-also"></a>関連項目

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream プログラミング](../standard-library/iostream-programming.md)<br/>
[iostreams の規則](../standard-library/iostreams-conventions.md)<br/>
