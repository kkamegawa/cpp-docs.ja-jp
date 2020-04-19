---
title: istrstream クラス
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 59b69d3f862715840e1557a10d6087350488a3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448075"
---
# <a name="istrstream-class"></a>istrstream クラス

クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーからの、要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Remarks

このオブジェクトは、クラス `strstreambuf` のオブジェクトを格納します。

> [!NOTE]
> このクラスは非推奨とされます。 代わりに、[istringstream](../standard-library/sstream-typedefs.md#istringstream) または [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) を使用することを検討してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[istrstream](#istrstream)|`istrstream` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[rdbuf](#rdbuf)|ストリームの関連付けられた `strstreambuf` オブジェクトへのポインターを返します。|
|[str](#str)|[freeze](../standard-library/strstreambuf-class.md#freeze) を呼び出し、被制御シーケンスの先頭へのポインターを返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<strstream>

**名前空間:** std

## <a name="istrstream"></a>  istrstream::istrstream

`istrstream` 型のオブジェクトを構築します。

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>パラメーター

*数*\
バッファーの長さ (*ptr*)。

*ポインター*\
バッファーが初期化されているコンテンツ。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、 [istream](../standard-library/istream-typedefs.md#istream)(**sb**) を呼び出すことによっ`sb`て基底クラスを初期化します。ここで、は[strstreambuf](../standard-library/strstreambuf-class.md)クラスの格納されているオブジェクトです。 最初の2つのコンストラクター `sb`は、 `strstreambuf`(( **const** `char` \*) `ptr`, 0) を呼び出すことによって初期化します。 残りの 2 つのコンストラクターは、代わりに `strstreambuf`( ( **const**`char` *) `ptr`, `count` ) を呼び出します。

## <a name="rdbuf"></a>  istrstream::rdbuf

ストリームの関連付けられた strstreambuf オブジェクトへのポインターを返します。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>戻り値

ストリームの関連付けられた strstreambuf オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、ポインター型の格納されたストリーム バッファーのアドレスを [strstreambuf](../standard-library/strstreambuf-class.md) に返します。

### <a name="example"></a>例

`rdbuf` の使用例は、[strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) を参照してください。

## <a name="str"></a>  istrstream::str

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

[istream](../standard-library/istream-typedefs.md#istream)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
