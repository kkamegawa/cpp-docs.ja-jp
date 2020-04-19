---
title: '&lt;istream&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890175"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 演算子

## <a name="op_gt_gt"></a>  operator&gt;&gt;

ストリームから文字と文字列を抽出します。

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>パラメーター

*Ch* \
単一の文字。

*Istr*\
ストリーム。

*str* \
文字列。

*val* \
型。

### <a name="return-value"></a>戻り値

ストリーム

### <a name="remarks"></a>Remarks

`basic_istream` クラスもいくつかの抽出演算子を定義します。 詳細については、「[basic_istream::operator >>](../standard-library/basic-istream-class.md#op_gt_gt)」を参照してください。

関数テンプレート:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

`N - 1` 要素までを抽出し、 *str*から始まる配列に格納します。 `Istr.`[width](../standard-library/ios-base-class.md#width)が0より大きい場合は、 *N*が `Istr.width`ます。それ以外の場合は、宣言できる `Elem` の最大配列のサイズです。 関数は、格納する抽出された要素の後に `Elem()` 値を常に格納します。 抽出は、ファイルの終わりから、(抽出されない) 値 `Elem(0)` を持つ文字、または[ws](../standard-library/istream-functions.md#ws)によって破棄される任意の要素 (抽出されていない) で停止します。 関数が要素を抽出しなかった場合は、`Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`を呼び出します。 いずれの場合も、`Istr.width(0)` を呼び出し、 *Istr*を返します。

**セキュリティ**に関する注意入力ストリームから抽出される null で終わる文字列は、コピー先のバッファー *str*のサイズを超えないようにする必要があります。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

関数テンプレート:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

可能な場合は要素を抽出し、 *Ch*に格納します。 それ以外の場合は、`is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`を呼び出します。 どのような場合でも、 *Istr*が返されます。

関数テンプレート:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

`Istr >> ( char * ) str` が返されます。

関数テンプレート:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

`Istr >> ( char& ) Ch` が返されます。

関数テンプレート:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

`Istr >> ( char * ) str` が返されます。

関数テンプレート:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

`Istr >> ( char& ) Ch` が返されます。

関数テンプレート:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

`Istr >> val` を返し、`Istr` の右辺値参照をプロセス内の左辺値に変換します。

### <a name="example"></a>例

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>関連項目

[\<istream>](../standard-library/istream.md)
