---
title: ostreambuf_iterator Class
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: be4421a7646756da5687ebc9b98f18daf4845809
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687220"
---
# <a name="ostreambuf_iterator-class"></a>ostreambuf_iterator Class

クラステンプレート ostreambuf_iterator は、抽出**演算子 > >** を使用して連続する文字要素を出力ストリームに書き込む出力反復子オブジェクトを記述します。 `ostreambuf_iterator` は、出力ストリームに挿入されるオブジェクトの型がジェネリック型ではなく文字である点が、[ostream_iterator クラス](../standard-library/ostream-iterator-class.md)のオブジェクトとは異なります。

## <a name="syntax"></a>構文

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>パラメーター

*Chartype* \
ostreambuf_iterator の文字型を表す型。 この引数は省略可能であり、既定値は**char**です。

*特徴*\
ostreambuf_iterator の文字型を表す型。 この引数は省略可能であり、既定値は `char_traits`\< *CharType>* です。

## <a name="remarks"></a>Remarks

ostreambuf_iterator クラスは出力反復子の要件を満たす必要があります。 アルゴリズムは `ostreambuf_iterator` を使用して出力ストリームに直接書き込むことができます。 このクラスは、生の (フォーマットされていない) I/O ストリームに文字の形式でアクセスできる低レベルのストリームの反復子を提供し、高レベルのストリーム反復子に関連付けられたバッファリングや文字変換をバイパスすることができます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|出力ストリームに文字を書き込むために初期化された `ostreambuf_iterator` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|`ostreambuf_iterator` の文字型を提供する型。|
|[ostream_type](#ostreambuf_iterator_ostream_type)|`ostream_iterator` のストリーム型を提供する型。|
|[streambuf_type](#streambuf_type)|`ostreambuf_iterator` のストリーム型を提供する型。|
|[traits_type](#traits_type)|`ostream_iterator` の文字特性型を提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[failed](#failed)|出力ストリーム バッファーへの挿入の失敗をテストします。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator*](#op_star)|@No__t_1  =  `x` \* の出力反復子式を実装するために使用される逆参照演算子。|
|[operator++](#op_add_add)|操作が呼び出される前に示したものと同じオブジェクトに `ostreambuf_iterator` を返す、実質的な機能を持たないインクリメント演算子。|
|[operator=](#op_eq)|この演算子は、関連付けられているストリーム バッファーに文字を挿入します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="char_type"></a>  ostreambuf_iterator::char_type

`ostreambuf_iterator` の文字型を提供する型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `CharType` のシノニムです。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="failed"></a>  ostreambuf_iterator::failed

出力ストリーム バッファーへの挿入の失敗をテストします。

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>戻り値

これまでに出力ストリーム バッファーへの挿入が失敗していない場合は、**true**。そうでない場合は、**false**。

### <a name="remarks"></a>Remarks

このメンバー関数は、これまでのメンバー `operator=` の使用で、**subf**_-> `sputc` の呼び出しが **eof** を返した場合、**true** を返します。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="op_star"></a>ostreambuf_iterator:: operator \*

出力反復子式 \* *i* = *x* を実装するために使用される逆参照演算子。

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>戻り値

ostreambuf 反復子オブジェクト。

### <a name="remarks"></a>Remarks

この演算子は、出力反復子式 \* *i* = *x* 内でのみ機能して、ストリーム バッファーに文字を出力します。 ostreambuf 反復子に適用されて、反復子を返します。 **\*iter** は **iter** を返します。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="op_add_add"></a>  ostreambuf_iterator::operator++

操作が呼び出される前に示したものと同じ文字に ostream 反復子を返す、実質的な機能を持たないインクリメント演算子。

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>戻り値

最初に示された文字または、`ostreambuf_iterator`\< **CharType**, **Traits**> に変換できる実装定義のオブジェクトへの参照。

### <a name="remarks"></a>Remarks

この演算子は、出力反復子式 \* *i* = *x* を実装するために使用されます。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="op_eq"></a>  ostreambuf_iterator::operator=

この演算子は、関連付けられているストリーム バッファーに文字を挿入します。

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>パラメーター

*文字 \ (_s)*
ストリーム バッファーに挿入する文字。

### <a name="return-value"></a>戻り値

ストリーム バッファーに挿入された文字への参照。

### <a name="remarks"></a>Remarks

出力ストリームに書き込むための出力反復子式 \* *i* = *x* を実装するために使用される代入演算子。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator

出力ストリームに文字を書き込むために初期化された `ostreambuf_iterator` を構築します。

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>パラメーター

*strbuf* \
出力ストリームバッファー ポインターを初期化するために使用される出力 streambuf オブジェクト。

*Ostr* \
出力ストリームバッファー ポインターを初期化するために使用される出力ストリーム オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、 *strbuf*を使用して出力ストリームバッファーポインターを初期化します。

2 番目のコンストラクターは、出力ストリームバッファー ポインターを `Ostr`. `rdbuf`. 格納されたポインターは null ポインターでない必要があります。

### <a name="example"></a>例

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type

`ostream_iterator` のストリーム型を提供する型。

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Remarks

この型は、`basicOstream`\< **CharType**, **Traits**> のシノニムです。

### <a name="example"></a>例

`ostream_type` を宣言して使用する方法の例については、[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) に関するセクションをご覧ください。

## <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type

`ostreambuf_iterator` のストリーム型を提供する型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Remarks

この型は、文字型**char**に特化している場合に `streambuf` される i/o バッファーのストリームクラス `basic_streambuf` \< **chartype**、**特徴**> のシノニムです。

### <a name="example"></a>例

`streambuf_type` を宣言して使用する方法の例については、[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) に関するセクションをご覧ください。

## <a name="traits_type"></a>  ostreambuf_iterator::traits_type

`ostream_iterator` の文字特性型を提供する型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Traits` のシノニムです。

### <a name="example"></a>例

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
