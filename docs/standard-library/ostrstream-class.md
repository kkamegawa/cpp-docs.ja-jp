---
title: ostrstream クラス
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: c73ab13d3cb2531ff3d741766bc86f8354a0be9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458060"
---
# <a name="ostrstream-class"></a>ostrstream クラス

クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーへの、要素とエンコードされたオブジェクトの挿入を制御するオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Remarks

このオブジェクトは、クラス `strstreambuf` のオブジェクトを格納します。

> [!NOTE]
> このクラスは非推奨とされます。 代わりに、[ostringstream](../standard-library/sstream-typedefs.md#ostringstream) または [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) を使用することを検討します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[ostrstream](#ostrstream)|`ostrstream` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[freeze](#freeze)|ストリーム バッファーの操作により、ストリーム バッファーを使用不可にします。|
|[pcount](#pcount)|被制御シーケンスに書き込まれる要素の数を返します。|
|[rdbuf](#rdbuf)|ストリームの関連付けられた `strstreambuf` オブジェクトへのポインターを返します。|
|[str](#str)|[freeze](../standard-library/strstreambuf-class.md#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<strstream>

**名前空間:** std

## <a name="freeze"></a>  ostrstream::freeze

ストリーム バッファーの操作により、ストリーム バッファーを使用不可にします。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>パラメーター

*_Freezeit*\
ストリームを固定するかどうかを示す**ブール**値。

### <a name="remarks"></a>Remarks

メンバー関数は [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*) を呼び出します。

### <a name="example"></a>例

の使用`freeze`例については、「 [strstream:: freeze](../standard-library/strstreambuf-class.md#freeze) 」を参照してください。

## <a name="ostrstream"></a>  ostrstream::ostrstream

`ostrstream` 型のオブジェクトを構築します。

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>パラメーター

*ポインター*\
バッファー。

*数*\
バッファーのサイズ (バイト単位)。

*_Mode*\
バッファーの入出力モード。 詳細については、[ios_base::openmode](../standard-library/ios-base-class.md#openmode) をご覧ください。

### <a name="remarks"></a>Remarks

どちらのコンストラクターも、 [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**) を呼び出すことに`sb`よって基底クラスを初期化します。ここで、は[strstreambuf](../standard-library/strstreambuf-class.md)クラスの格納されているオブジェクトです。 最初のコンストラクターは、 `sb`を呼び`strstreambuf`出すことによっても初期化します。 2 番目のコンストラクターは、次のどちらかの方法で基本クラスを初期化します。

- Ios_base `_Mode` `count`  &  `strstreambuf` **::** `ptr` app=`count`= 0 の場合、は要素の配列の最初の要素を指定する必要があり、コンストラクターは(,,)を呼び出します。`ptr` `ptr`).

- それ以外`ptr`の場合は、最初の要素がによって`ptr`指定された C 文字列を含む count 要素の最初の要素を指定する`ptr`必要`count`があります。また、コンストラクターは (,, を`strstreambuf` `ptr`呼び出します。 + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

被制御シーケンスに書き込まれる要素の数を返します。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>戻り値

被制御シーケンスに書き込まれる要素の数。

### <a name="remarks"></a>Remarks

このメンバー関数は、[rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount) を返します。

### <a name="example"></a>例

`pcount` の使用例は、[strstream::pcount](../standard-library/strstreambuf-class.md#pcount) をご覧ください。

## <a name="rdbuf"></a>  ostrstream::rdbuf

ストリームの関連付けられた strstreambuf オブジェクトへのポインターを返します。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>戻り値

ストリームの関連付けられた strstreambuf オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、型`pointer`の格納されているストリームバッファーのアドレスを[strstreambuf](../standard-library/strstreambuf-class.md)に返します。

### <a name="example"></a>例

`rdbuf` の使用例は、[strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) をご覧ください。

## <a name="str"></a>  ostrstream::str

[freeze](../standard-library/strstreambuf-class.md#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。

```cpp
char *str();
```

### <a name="return-value"></a>戻り値

被制御シーケンスの先頭へのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、[rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str) を返します。

### <a name="example"></a>例

を使用`str`するサンプルについては、「 [strstream:: str](../standard-library/strstreambuf-class.md#str) 」を参照してください。

## <a name="see-also"></a>関連項目

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
