---
title: '&lt;ostream&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453530"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 演算子

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  演算子&lt;&lt;

さまざまな型をストリームに書き込みます。

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>パラメーター

*Ch (_p)* \
単一の文字。

*Elem (_t)* \
要素型。

*_Ostr*\
`basic_ostream` オブジェクト。

*引数*\
文字列。

*Tr (_m)* \
文字の特徴 (traits)。

*val*\
型

### <a name="return-value"></a>戻り値

ストリーム。

### <a name="remarks"></a>Remarks

`basic_ostream`クラスもいくつかの挿入演算子を定義します。 詳細については、[basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)をご覧ください。

下記のテンプレート関数は

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

str で始まるシーケンスの`traits_type::`長さ N`str`=[長さ](../standard-library/char-traits-struct.md#length)() を決定し、シーケンスを挿入します。 N < `_Ostr.`[width](../standard-library/ios-base-class.md#width) の場合は、関数はまた `_Ostr.width` - N 充填文字の繰り返しを挿入します。 (`_Ostr`の場合、繰り返しはシーケンスの前に置かれます。 [flags](../standard-library/ios-base-class.md#flags) & != [left](../standard-library/ios-functions.md#left)。`adjustfield` それ以外の場合、繰り返しはシーケンスに後続します。 関数は、 *_Ostr*を返します。

下記のテンプレート関数は

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

要素 `_Ch`を挿入しています。 1 < `_Ostr.width` である場合、この関数はまた `_Ostr.width` - 1 充填文字の繰り返しを挿入します。 `_Ostr.flags & adjustfield != left` である場合、繰り返しはシーケンスに先行します。 それ以外の場合、繰り返しはシーケンスに後続します。 *_Ostr*が返されます。

下記のテンプレート関数は

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

次の関数と同様に動作します。

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

ただし、 *str*で始まるシーケンスの*各要素は*、 [put](../standard-library/basic-ostream-class.md#put)`_Ostr.`[(拡張 (](../standard-library/basic-ios-class.md#widen)`_Ch`)) を呼び`Elem`出す`_Ostr.`ことによって、型のオブジェクトに変換されます。

下記のテンプレート関数は

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

次の関数と同様に動作します。

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

ただし、 ( `Elem` `_Ostr.put` (`_Ch`)) を呼び出すことによって、Ch が型のオブジェクトに変換される点が異なります。 `_Ostr.widen`

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

次の関数と同様に動作します。

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(要素を挿入する前に拡張する必要はありません。)

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

次の関数と同様に動作します。

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(これを挿入する前に、 *Ch*を広げる必要はありません)。

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

< `_Ostr` < (`const char *` )`str`を返します。

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

< `_Ostr` < (`char` )`_Ch`を返します。

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

< `_Ostr` < (`const char *` )`str`を返します。

下記のテンプレート関数は

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

< `_Ostr` < (`char` )`_Ch`を返します。

下記のテンプレート関数は

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

`_Ostr` `<<` `val` を返します (さらに `_Ostr` への [RValue Reference](../cpp/rvalue-reference-declarator-amp-amp.md) をそのプロセス内の lvalue に変換します)。

### <a name="example"></a>例

`operator<<` の使用例は、[flush](../standard-library/ostream-functions.md#flush) をご覧ください。

## <a name="see-also"></a>関連項目

[\<ostream>](../standard-library/ostream.md)
