---
title: '&lt;bitset&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: 23c6abffe7e433a0550c45502a12e9adaf652a33
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257989"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 演算子

## <a name="op_amp"></a> 演算子&amp;

2 つのビットセット間でビットごとの `AND` を実行します。

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素が `AND` でビットごとに結合される 2 つのビットセットのうちの最初。

*右*\
それぞれの要素が `AND` でビットごとに結合される 2 つの valarray のうちの 2 つ目。

### <a name="return-value"></a>戻り値

*左右*の対応する要素に対して `AND` 操作を実行した結果*として*得られる要素を持つビットセット。

### <a name="example"></a>例

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a>演算子&lt;&lt;

ビット シーケンスのテキスト表現を出力ストリームに挿入します。

```cpp
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
文字列として出力ストリームに挿入する型 **bitset\<N>** のオブジェクト。

### <a name="return-value"></a>戻り値

`ostr`内のビットシーケンスのテキスト表現。

### <a name="remarks"></a>コメント

このテンプレート関数は `operator<<`をオーバーロードします。これにより、最初に文字列に変換せずにビットセットを書き出すことができます。 このテンプレート関数は、実質的に次の内容を実行します。

`ostr << right.`[to_string](bitset-class.md)`<CharType, Traits, allocator<CharType>>()`

### <a name="example"></a>例

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a>演算子&gt;&gt;

ビット文字の文字列をビットセットに読み込みます。

```cpp
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& i_str,
    bitset<N>& right);
```

### <a name="parameters"></a>パラメーター

*i_str*\
ビットセットに挿入する入力ストリームに入力される文字列。

*右*\
入力ストリームからビットを受け取るビットセット。

### <a name="return-value"></a>戻り値

このテンプレート関数は、文字列*i_str*を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`operator>>` をオーバーロードして、*ビットセット内*の値 `bitset(str)`を格納します。 `str` は、 *`< CharType, Traits, allocator< CharType > >&`* から抽出された[basic_string](basic-string-class.md)型のオブジェクトです。

このテンプレート関数は、 *i_str*から要素を抽出し、次のようになるまでビットセットに挿入します。

- すべてのビット要素が入力ストリームから抽出され、ビットセットに格納されています。

- ビットセットが入力ストリームからのビットでいっぱいになっています。

- 0 でも 1 でもない入力要素に遭遇しました。

### <a name="example"></a>例

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a>^ 演算子

2 つのビットセット間でビットごとの `EXCLUSIVE-OR` を実行します。

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素が `EXCLUSIVE-OR` でビットごとに結合される 2 つのビットセットのうちの最初。

*右*\
それぞれの要素が `EXCLUSIVE-OR` でビットごとに結合される 2 つの valarray のうちの 2 つ目。

### <a name="return-value"></a>戻り値

*左右*の対応する要素に対して `EXCLUSIVE-OR` 操作を実行した結果*として*得られる要素を持つビットセット。

### <a name="example"></a>例

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a>operator&#124;

2 つのビットセット間でビットごとの `OR` を実行します。

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
それぞれの要素が `OR` でビットごとに結合される 2 つのビットセットのうちの最初。

*右*\
それぞれの要素が `OR` でビットごとに結合される 2 つの valarray のうちの 2 つ目。

### <a name="return-value"></a>戻り値

*左右*の対応する要素に対して `OR` 操作を実行した結果*として*得られる要素を持つビットセット。

### <a name="example"></a>例

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
