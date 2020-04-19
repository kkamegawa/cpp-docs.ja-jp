---
title: bitset クラス
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: a4771e9c2c48bfe9c4c09629278533b031d60979
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258238"
---
# <a name="bitset-class"></a>bitset クラス

固定数のビットで構成されるシーケンスを格納するオブジェクト型を記述します。これらのビットによって、一連の項目または条件のフラグを保持するためのコンパクトな方法が提供されます。 bitset クラスでは、ビットのコレクションを含み、各ビットへの一定時間のアクセスを提供する bitset 型のオブジェクトに対する操作をサポートします。

## <a name="syntax"></a>構文

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>パラメーター

*N*\
`size_t` 型の0以外の整数を持つビットセットオブジェクト内のビット数を指定します。これはコンパイル時に認識される必要があります。

## <a name="remarks"></a>コメント

よく似ている [vector\<bool> クラス](../standard-library/vector-bool-class.md)とは異なり、bitset クラスには反復子がなく、C++ 標準ライブラリのコンテナーでもありません。 また、\<bitset*N* **が宣言されている場合、テンプレート パラメーター \<N\> で指定したサイズに従い、コンパイル時のサイズが特定の値に固定されている点でも vector**bool> とは異なっています。

ビットは、その値が 1 の場合は設定され、0 の場合にはリセットされます。 ビットの反転や切り替えとは、その値を 1 から 0 へ、あるいは 0 から 1 へ変更することです。 ビットセット内の *N* ビットには、0 ～ *N* - 1 の整数値でインデックスが付けられます。0 は最初のビット位置、*N* - 1 は最終的なビット位置へのインデックスを表します。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[bitset](#bitset)|クラス `bitset\<N>` のオブジェクトを構築し、ビットを 0 か、指定した値、または文字列の文字から取得した値に初期化します。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|データ型のシノニムで**あり、`bitset`** 内の要素のビットを参照するために使用できる型。|

### <a name="functions"></a>関数

|||
|-|-|
|[all](#all)|すべてが**true**に設定されているかどうかを判断するために、この `bitset` 内のすべてのビットをテストします。|
|[任意](#any)|このメンバー関数は、シーケンス内のいずれかのビットが 1 に設定されているかどうかをテストします。|
|[count](#count)|このメンバー関数は、ビット シーケンスで設定されているビットの数を返します。|
|[flip](#flip)|`bitset` 内のすべてのビットの値を反転させるか、指定した位置の単一のビットを反転させます。|
|"[なし](#none)"|`bitset` オブジェクト内のどのビットも 1 に設定されていないかどうかをテストします。|
|[reset](#reset)|`bitset` 内のすべてのビットを 0 にリセットするか、指定した位置の 1 つのビットを 0 にリセットします。|
|[set](#set)|`bitset` 内のすべてのビットを 1 に設定するか、指定した位置の 1 つのビットを 1 に設定します。|
|[size](#size)|`bitset` オブジェクト内のビット数を返します。|
|[test](#test)|`bitset` 内の指定した位置のビットが 1 に設定されているかどうかをテストします。|
|[to_string](#to_string)|`bitset` オブジェクトを文字列形式に変換します。|
|[to_ullong](#to_ullong)|`bitset` 内のビット値の合計を**unsigned long long 型**として返します。|
|[to_ulong](#to_ulong)|`bitset` オブジェクトを、`bitset`の初期化に使用される場合に含まれるビットのシーケンスを生成する**unsigned long**に変換します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[reference](#reference)|`bitset` クラスの `operator[]` 用ヘルパー クラスとして、個々のビットへのアクセスと操作に使用される `bitset` に含まれるビットへの参照を提供するプロキシ クラス。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](#op_neq)|指定した `bitset` とターゲット `bitset` が等しくないことをテストします。|
|[operator&=](#op_and_eq)|`AND` 論理演算を使用して、ビットセットのビットごとの組み合わせを実行します。|
|[operator<<](#op_lshift)|`bitset` 内のビットを、指定した位置数だけ左側にシフトさせ、その結果を新しい `bitset` に返します。|
|[operator<<=](#op_lshift_eq)|`bitset` 内のビットを、指定した位置数だけ左側にシフトさせ、その結果を対象とする `bitset` に返します。|
|[operator==](#op_eq_eq)|指定した `bitset` とターゲット `bitset` が等しいことをテストします。|
|[operator>>](#op_rshift)|`bitset` 内のビットを、指定した位置数だけ右側にシフトさせ、その結果を新しい `bitset` に返します。|
|[operator>>=](#op_rshift_eq)|`bitset` 内のビットを、指定した位置数だけ右側にシフトさせ、その結果を対象とする `bitset` に返します。|
|[operator&#91;&#93;](#op_at)|`bitset` が変更可能な場合、`bitset` 内の指定した位置のビットへの参照を返します。それ以外の場合は、その位置のビットの値を返します。|
|[operator^=](#op_xor_eq)|排他的 `OR` 演算を使用して、ビットセットのビットごとの組み合わせを実行します。|
|[operator&#124;=](#op_or_eq)|包括的 `OR` 演算を使用して、ビットセットのビットごとの組み合わせを実行します。|
|[operator~](#op_not)|ターゲット `bitset` 内のすべてのビットを反転させ、その結果を返します。|

### <a name="structures"></a>構造体

|||
|-|-|
|[hash](#hash)||

### <a name="all"></a>すべての

このビットセットのビットすべてが true に設定されているかどうかを判別するテストを行います。

```cpp
bool all() const;
```

#### <a name="return-value"></a>戻り値

このセット内のすべてのビットが true の場合、true を返します。 1 つ以上のビットが false の場合は、**false** を返します。

### <a name="any"></a>いつ

シーケンス内のいずれかのビットが 1 に設定されているかどうかをテストします。

```cpp
bool any() const;
```

#### <a name="return-value"></a>戻り値

ビットセット内に 1 に設定されているビットがあれば **true** を、すべてのビットが 0 に設定されていれば **false** を返します。

#### <a name="example"></a>例

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a>ビットセット

クラス `bitset\<N>` のオブジェクトを構築し、ビットを 0 か、指定した値、または文字列の文字から取得した値に初期化します。

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>パラメーター

*val*\
符号なし整数。構築中のビットセット内のビットを 2 つの表現で初期化するとき、その基数が使用されます。

*str*\
ビットセットのビット値の初期化に 0 と 1 の文字列が使用されます。

*_CStr*\
ビットセットのビット値の初期化に 0 と 1 の C スタイルの文字列が使用されます。

*_Pos*\
文字列内の文字の位置。左から右に数え、ゼロから始まります。ビットセット内の最初のビットの初期化に使用されます。

*カウント*\
ビットセット内のビットの初期値を提供するために使用される文字列内の文字数。

*_Zero*\
0 を表すために使用される文字。 既定値は '0' です。

*_One*\
1 を表すために使用される文字。 既定値は '1' です。

#### <a name="remarks"></a>コメント

3 つのコンストラクターを利用し、クラス `bitset\<N>` のオブジェクトを構築できます。

- 最初のコンストラクターはパラメーターを受け取らず、クラス `bitset\<N>` のオブジェクトを構築し、すべての N ビットを既定値の 0 に初期化します。

- 2番目のコンストラクターは `bitset\<N>` クラスのオブジェクトを構築し、1つの**unsigned long long**パラメーターを使用してビットを初期化します。

- 3 番目のコンストラクターはクラス `bitset\<N>` のオブジェクトを構築し、0 と 1 の C スタイル文字列で与えられた文字に対応する値に N ビットを初期化します。 文字列を文字列型に型変換せずにコンストラクターを呼び出します。例: `bitset<5> b5("01011");`

2 つのコンストラクター テンプレートも提供されています。

- 最初のコンストラクター テンプレートはクラス `bitset\<N>` のオブジェクトを構築し、0 と 1 の文字列で与えられた文字のビットを初期化します。 文字列の文字に 0 か 1 以外の文字がある場合、このコンストラクターはクラス [invalid argument](../standard-library/invalid-argument-class.md) のオブジェクトをスローします。 指定された位置 ( *_Pos*) が文字列の長さを超えている場合、コンストラクターは[out_of_range](../standard-library/out-of-range-class.md)クラスのオブジェクトをスローします。 このコンストラクターは、位置 *で文字列の文字が 1 のビットのみをビットセットの位置*j`_Pos + j` に配置します。 既定では、 *_Pos*は0です。

- 2番目のコンストラクターテンプレートは最初のコンストラクターに似ていますが、初期化するビット数を指定するために使用される追加のパラメーター (*count*) が含まれています。 また、 *_Zero*と *_One*という2つの省略可能なパラメーターもあります。これは、それぞれ0ビットと1ビットを意味する*str*の文字を示します。

#### <a name="example"></a>例

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a>数

ビット シーケンスで設定されたビット数を返します。

```cpp
size_t count() const;
```

#### <a name="return-value"></a>戻り値

ビット シーケンスで設定されたビット数。

#### <a name="example"></a>例

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a>element_type

データ型のシノニムで**あり、ビット**セットの要素ビットを参照するために使用できる型。

```cpp
typedef bool element_type;
```

#### <a name="example"></a>例

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a>短辺

ビットセット内のすべてのビットの値を反転させるか、指定した位置の単一のビットを反転させます。

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
値を反転させるビットの位置。

#### <a name="return-value"></a>戻り値

メンバー関数が呼び出された変更後ビットセットのコピー。

#### <a name="remarks"></a>コメント

2番目のメンバー関数は、パラメーターとして指定された位置が、ビットが反転されたビット**セット\<** *n* **>** のサイズ*n*を超える場合に、 [out_of_range](../standard-library/out-of-range-class.md)例外をスローします。

#### <a name="example"></a>例

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a>ハッシュ

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a>存在

ビットセット オブジェクト内のどのビットも 1 に設定されていないかどうかをテストします。

```cpp
bool none() const;
```

#### <a name="return-value"></a>戻り値

ビットセットに 1 に設定されているビットがない場合は **true** を、1 に設定されているビットが 1 つでもあれば **false** を返します。

#### <a name="example"></a>例

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="op_neq"></a>operator! =

指定したビットセットとターゲット ビットセットが等しくないことをテストします。

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>パラメーター

*右*\
不等性についてターゲット ビットセットと比較されるビットセット。

#### <a name="return-value"></a>戻り値

ビットセットが異なる場合は **true** を、同じ場合は **false** を返します。

#### <a name="remarks"></a>コメント

メンバー演算子関数で不等性をテストするとき、ビットセットは同じサイズにする必要があります。

#### <a name="example"></a>例

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_and_eq"></a>演算子&amp;=

`AND` 論理演算を使用して、ビットセットのビットごとの組み合わせを実行します。

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>パラメーター

*右*\
ビット単位でターゲット ビットセットと結合するビットセット。

#### <a name="return-value"></a>戻り値

ビットセットをパラメーターとして指定してビットごとの `AND` 操作を実行した結果として得られる、変更されたターゲットビットセット。

#### <a name="remarks"></a>コメント

`AND` 演算子によって結合された2つのビットは、各ビットが true の場合に**true**を返します。それ以外の場合、これらの組み合わせは**false**を返します。

ビットセットは、メンバー演算子関数によって `AND` 演算子とビットごとに結合される同じサイズでなければなりません。

#### <a name="example"></a>例

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_lshift"></a>演算子\<\<

ビットセット内のビットを、指定した位置数だけ左側にシフトさせ、その結果を新しいビットセットに返します。

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内のビットを左側にシフトするときの位置数。

#### <a name="return-value"></a>戻り値

必要な位置数だけビットを左にシフトした変更後ビットセット。

#### <a name="remarks"></a>コメント

メンバー演算子関数は **bitset**( **\*this**) **<<= pos** を返します。[<<=](#op_lshift_eq) は、指定された位置数だけビットセット内のビットを左側にシフトし、結果をターゲット ビットセットに返します。

#### <a name="example"></a>例

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="op_lshift_eq"></a>演算子&lt;&lt;=

ビットセット内のビットを、指定した位置数だけ左側にシフトさせ、その結果を対象とするビットセットに返します。

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内のビットを左側にシフトするときの位置数。

#### <a name="return-value"></a>戻り値

必要な位置数だけビットを左側にシフトした変更後ターゲット ビットセット。

#### <a name="remarks"></a>コメント

その位置までシフトする要素がない場合、この関数はビットを消去し、値 0 にします。

#### <a name="example"></a>例

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="op_eq_eq"></a>operator = =

指定したビットセットとターゲット ビットセットが等しいことをテストします。

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>パラメーター

*右*\
ターゲット ビットセットと比較し、等しいかどうかを判定するビットセット。

#### <a name="return-value"></a>戻り値

ビットセットが同じ場合は **true** を、異なる場合は **false** を返します。

#### <a name="remarks"></a>コメント

メンバー演算子関数で等しいかどうかをテストするとき、ビットセットは同じサイズにする必要があります。

#### <a name="example"></a>例

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_rshift"></a>演算子&gt;&gt;

ビットセット内のビットを、指定した位置数だけ右側にシフトさせ、その結果を新しいビットセットに返します。

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内のビットを右側にシフトするときの位置数。

#### <a name="return-value"></a>戻り値

ターゲット ビットセットを基準にして必要な位置数だけビットが右側にシフトされた新しいビットセット。

#### <a name="example"></a>例

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="op_rshift_eq"></a>演算子&gt;&gt;=

ビットセット内のビットを、指定した位置数だけ右側にシフトさせ、その結果を対象とするビットセットに返します。

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内のビットを右側にシフトするときの位置数。

#### <a name="return-value"></a>戻り値

必要な位置数だけビットを右側にシフトした変更後ターゲット ビットセット。

#### <a name="remarks"></a>コメント

その位置までシフトする要素がない場合、この関数はビットを消去し、値 0 にします。

#### <a name="example"></a>例

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="op_at"></a>演算子 []

ビットセットが変更可能な場合、ビットセット内の指定した位置のビットへの参照を返します。それ以外の場合は、その位置のビットの値を返します。

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内のビットの位置。

#### <a name="remarks"></a>コメント

ビルドで [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) を 1 か 2 に定義すると、ビットセットの境界の外にある要素にアクセスしようとすると、実行可能ファイルでランタイム エラーが発生します。 詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

#### <a name="example"></a>例

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="op_xor_eq"></a>演算子 ^ =

排他的 `OR` 演算を使用して、ビットセットのビットごとの組み合わせを実行します。

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>パラメーター

*右*\
ビット単位でターゲット ビットセットと結合するビットセット。

#### <a name="return-value"></a>戻り値

パラメーターとして指定されたビットセットとビット単位で排他的 `OR` 演算された結果として生成される変更後ターゲット ビットセット。

#### <a name="remarks"></a>コメント

排他的 **OR** 演算子で結合された 2 つのビットは、両方ではなくいずれかが **true** の場合に **true** を返し、そうでない場合に **false** を返します。

メンバー演算子関数では、排他的 `OR` 演算子でビット単位で結合するとき、ビットセットのサイズを同じにする必要があります。

#### <a name="example"></a>例

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_or_eq"></a>operator&#124;=

包括的 `OR` 演算を使用して、ビットセットのビットごとの組み合わせを実行します。

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>パラメーター

*右*\
ビット単位でターゲット ビットセットと結合するビットセット。

#### <a name="return-value"></a>戻り値

パラメーターとして指定されたビットセットとビット単位で両立的 `OR` 演算された結果として生成される変更後ターゲット ビットセット。

#### <a name="remarks"></a>コメント

両立的 `OR` 演算子で結合された 2 つのビットは、いずれかが **true** の場合に **true** を返し、両方とも **false** の場合に **false** を返します。

メンバー演算子関数では、両立的 `OR` 演算子でビット単位で結合するとき、ビットセットのサイズを同じにする必要があります。

#### <a name="example"></a>例

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_not"></a>演算子 ~

ターゲット ビットセット内のすべてのビットを反転させ、その結果を返します。

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>戻り値

ターゲット ビットセットを基準にしてすべてのビットが反転されたビットセット。

#### <a name="example"></a>例

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a>「

ビットセット クラスのビットセット用ヘルパー クラスとして、個々のビットへのアクセスと操作に使用される `operator[]` に含まれるビットへの参照を提供するプロキシ クラス。

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>パラメーター

*val*\
ビットセット内のビットに割り当てられる**bool**型のオブジェクトの値。

*_Bitref*\
フォーム *x [ i ]* のビットセット *x* の位置 *i* のビット参照。

#### <a name="return-value"></a>戻り値

クラス参照の第 1、第 2、第 5 メンバー関数に対して引数位置により指定されるビットセットのビット参照。そして、**true** または **false**。これは、クラス参照の第 3 と第 4 メンバー関数に対してビットセットの変更後ビットの値を反映します。

#### <a name="remarks"></a>コメント

クラス `reference` は、ビットセット `operator[]` のヘルパー クラスとしてのみ存在します。 このメンバー クラスは、ビットセット内の個別ビットにアクセスできるオブジェクトを表します。 *B*は、型が**bool**、 *x* 、 *y*で、**ビットセット\<** *N* **>** のオブジェクト、およびそのようなオブジェクト内の*i*と*j*の有効な位置です。 表記 *x [i]* は、ビットセット *x* の位置 *i* のビットを指します。 クラス `reference` のメンバー関数は、次の演算を順に与えます。

|操作|Definition|
|---------------|----------------|
|*x*[*i*] = *b*|**ブール**値*b*をビットセット*x*のビット位置*i*に格納します。|
|*x*[*i*] = *y*[*j*]|ビットセット *x* のビット位置 *i* にビット *y*[ *j*] の値を保存します。|
|*b* = ~ *x*[*i*]|ビット*x*[ *i*] の反転値を**ブール** *b*に格納します。|
|*b* = *x*[*i*]|ビット*x*[ *i*] の値を**ブール** *b*に格納します。|
|*x*[*i*]. `flip`( )|*x* のビット位置 *i* にビット *x*[ *i*] の反転値を保存します。|

#### <a name="example"></a>例

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a>解除

ビットセット内のすべてのビットを 0 にリセットするか、指定した位置の 1 つのビットを 0 にリセットします。

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内で 0 にリセットするビットの位置。

#### <a name="return-value"></a>戻り値

メンバー関数が呼び出されたビットセットのコピー。

#### <a name="remarks"></a>コメント

2 番目のメンバー関数は、指定された位置がビットセットのサイズより大きい場合、[out_of_range](../standard-library/out-of-range-class.md) 例外をスローします。

#### <a name="example"></a>例

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a>一連

ビットセット内のすべてのビットを 1 に設定するか、指定した位置の 1 つのビットを 1 に設定します。

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内で、ある値を割り当てるように設定するビットの位置。

*val*\
指定された位置のビットに割り当てる値。

#### <a name="return-value"></a>戻り値

メンバー関数が呼び出されたビットセットのコピー。

#### <a name="remarks"></a>コメント

2 番目のメンバー関数は、指定された位置がビットセットのサイズより大きい場合、[out_of_range](../standard-library/out-of-range-class.md) 例外をスローします。

#### <a name="example"></a>例

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a>幅

bitset オブジェクト内のビット数を返します。

```cpp
size_t size() const;
```

#### <a name="return-value"></a>戻り値

bitset*N> 内のビットの数、* N\<。

#### <a name="example"></a>例

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a>test

ビットセット内の指定した位置のビットが 1 に設定されているかどうかをテストします。

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>パラメーター

*_Pos*\
ビットセット内でその値をテストするビットの位置。

#### <a name="return-value"></a>戻り値

引数位置により指定されたビットが 1 に設定されている場合は **true** を、それ以外の場合は **false** を返します。

#### <a name="remarks"></a>コメント

このメンバー関数は [out_of_range](../standard-library/out-of-range-class.md) をスローします。

### <a name="to_string"></a>to_string

ビットセットオブジェクトを文字列形式に変換します。

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>戻り値

`basic_string`クラスの文字列オブジェクト。ビットセット内の各ビットセットの対応する文字は1で、ビットが設定されていない場合は0です。

#### <a name="example"></a>例

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a>to_ullong

ビットセットオブジェクトの内容と同じビットセットを含む、 **unsigned long long 型**の値を返します。

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>戻り値

ビットシーケンス内の**符号なし long long 型**のビット値の合計を返します。 この**unsigned long long 型**の値は、ビットセットを初期化するために使用されている場合、同じセットのビットを再作成します。

#### <a name="exceptions"></a>例外

ビットシーケンス内のいずれかのビットに、 **unsigned long long**型の値として表現できないビット値がある場合、 [overflow_error](overflow-error-class.md)オブジェクトをスローします。

#### <a name="remarks"></a>コメント

ビットシーケンス内の**符号なし long long 型**のビット値の合計を返します。

### <a name="to_ulong"></a>to_ulong

ビットセットオブジェクトを、ビットセットの初期化に使用される場合に含まれるビットのシーケンスを生成する整数に変換します。

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>戻り値

ビットセットの初期化で使用される場合にビットセットのビットを生成する整数。

#### <a name="remarks"></a>コメント

このメンバー関数を適用すると、ビットセットに含まれるビットのシーケンスと同じ1桁と0の数字を持つ整数が返されます。

このメンバー関数は、ビットシーケンス内のいずれかのビットに**符号なし long**型の値として表すことができないビット値がある場合、 [overflow_error](overflow-error-class.md)オブジェクトをスローします。

#### <a name="example"></a>例

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
