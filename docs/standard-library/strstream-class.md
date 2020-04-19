---
title: strstream クラス
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 53baa350121796d5198211e1fdb08f4341df6b80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459104"
---
# <a name="strstream-class"></a>strstream クラス

クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーを使用して、要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Remarks

このオブジェクトは、クラス `strstreambuf` のオブジェクトを格納します。

> [!NOTE]
> このクラスは非推奨とされます。 代わりに、[stringstream](../standard-library/sstream-typedefs.md#stringstream) または [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) を使用することを検討してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[strstream](#strstream)|`strstream` 型のオブジェクトを構築します。|

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

## <a name="freeze"></a>  strstream::freeze

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

の使用`freeze`例については、「 [strstreambuf:: freeze](../standard-library/strstreambuf-class.md#freeze) 」を参照してください。

## <a name="pcount"></a>  strstream::pcount

被制御シーケンスに書き込まれる要素の数を返します。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>戻り値

被制御シーケンスに書き込まれる要素の数。

### <a name="remarks"></a>Remarks

このメンバー関数は、[rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount) を返します。

### <a name="example"></a>例

pcount の使用例は、[strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) をご覧ください。

## <a name="rdbuf"></a>  strstream::rdbuf

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

## <a name="str"></a>  strstream::str

[freeze](../standard-library/strstreambuf-class.md#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。

```cpp
char *str();
```

### <a name="return-value"></a>戻り値

被制御シーケンスの先頭へのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、[rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str) を返します。

### <a name="example"></a>例

を使用`str`するサンプルについては、「 [strstreambuf:: str](../standard-library/strstreambuf-class.md#str) 」を参照してください。

## <a name="strstream"></a>  strstream::strstream

`strstream` 型のオブジェクトを構築します。

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>パラメーター

*数*\
バッファーのサイズ。

*_Mode*\
バッファーの入出力モード。 詳細については、[ios_base::openmode](../standard-library/ios-base-class.md#openmode) をご覧ください。

*ポインター*\
バッファー。

### <a name="remarks"></a>Remarks

どちらのコンストラクターも、 [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**) を呼び出すことに`sb`よって基底クラスを初期化します。ここで、は[strstreambuf](../standard-library/strstreambuf-class.md)クラスの格納されているオブジェクトです。 最初のコンストラクターは、 `sb` [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf)を呼び出すことによっても初期化します。 2 番目のコンストラクターは、次のどちらかの方法で基本クラスを初期化します。

- `_Mode` **Ios_base:: app**= = 0 の場合 & 、 *ptr*は要素の`count`配列の最初の要素を指定する必要があり、コンストラクター `ptr`は ( `ptr`, `count`,) を呼び出し`strstreambuf`ます.

- それ以外の場合、 *ptr*は、最初の要素が*ptr*によって指定されている C 文字列を含む count 要素の配列の最初`strstreambuf`の要素を指定する必要があり、コンストラクターは ( `ptr`, `count`, を`ptr` 呼び出します。 + `strlen`( `ptr`) ).

## <a name="see-also"></a>関連項目

[iostream](../standard-library/istream-typedefs.md#iostream)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
