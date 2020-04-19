---
title: char_traits 構造体
ms.date: 05/07/2019
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: efb926bc8c2ae55835391f884a0e3430e3da8aca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856400"
---
# <a name="char_traits-struct"></a>char_traits 構造体

char_traits 構造体は文字に関連付けられた属性を記述します。

## <a name="syntax"></a>構文

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>パラメーター

*Chartype*\
要素のデータ型。

## <a name="remarks"></a>解説

テンプレート構造体は `CharType`型のさまざまな文字の特徴を記述します。 クラステンプレート[basic_string](../standard-library/basic-string-class.md)と、 [basic_ios](../standard-library/basic-ios-class.md)を含むいくつかの iostream クラステンプレートだけでなく、この情報を使用して `CharType`型の要素を操作します。 このような要素型では、明示的な構築や破棄を要求できません。 既定のコンストラクター、コピー コンストラクター、および代入演算子を、必要なセマンティクスと共に指定する必要があります。 ビットごとのコピーは、代入と同じ効果を持つ必要があります。 char_traits 構造体のメンバー関数は、いずれも例外をスローしません。

### <a name="typedefs"></a>Typedefs

|種類の名前。|Description|
|-|-|
|[char_type](#char_type)|文字の型。|
|[int_type](#int_type)|`char_type` 型の文字、またはファイルの終端 (EOF) 文字を表すことができる整数型。|
|[off_type](#off_type)|ストリーム内の位置間のオフセットを表すことのできる整数型。|
|[pos_type](#pos_type)|ストリーム内の位置を表すことのできる整数型。|
|[state_type](#state_type)|ストリーム内のマルチバイト文字の変換状態を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|Description|
|-|-|
|[assign](#assign)|1 つの文字の値を別の文字に割り当てます。|
|[compare](#compare)|指定した文字数まで 2 つの文字列を比較します。|
|[copy](#copy)|1 つの文字列から別の文字列に指定した数の文字をコピーします。 非推奨になりました。 代わりに [char_traits::_Copy_s](#copy_s) を使用してください。|
|[_Copy_s](#copy_s)|1 つの文字列から別の文字列に指定した数の文字をコピーします。|
|[eof](#eof)|ファイルの終端 (EOF) 文字を返します。|
|[eq](#eq)|2 つの `char_type` 文字が等しいかどうかをテストします。|
|[eq_int_type](#eq_int_type)|`int_type` として表される 2 つの文字が等しいかどうかをテストします。|
|[find](#find)|文字の範囲内で指定した文字が最初に出現する位置を検索します。|
|[length](#length)|文字列の長さを返します。|
|[lt](#lt)|1 つの文字が別の文字よりも小さいかどうかをテストします。|
|[move](#move)|シーケンス内の文字を、指定された文字数だけ、重複が生じる可能性のある別のシーケンスにコピーします。 非推奨になりました。 代わりに [char_traits::_Move_s](#move_s) を使用してください。|
|[_Move_s](#move_s)|シーケンス内の文字を、指定された文字数だけ、重複が生じる可能性のある別のシーケンスにコピーします。|
|[not_eof](#not_eof)|文字がファイルの終端 (EOF) 文字であるかどうかをテストします。|
|[to_char_type](#to_char_type)|`int_type` の文字を `char_type` の対応する文字に変換し、その結果を返します。|
|[to_int_type](#to_int_type)|`char_type` の文字を `int_type` の対応する文字に変換し、その結果を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<文字列 >

**名前空間:** std

## <a name="assign"></a>  char_traits::assign

別の文字値または文字列内の要素の範囲に 1 つの文字値を割り当てます。

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>パラメーター

値が割り当てられる文字からの **_** *charfrom*

*_CharTo*\
文字値を割り当てられる要素。

*Strto*\
最初の要素が割り当てられた文字値になる文字列または文字の配列。

*_Num*\
値を割り当てられる要素の数。

### <a name="return-value"></a>戻り値

2番目のメンバー関数は、最初の *_Num*要素に *_CharFrom*の値が割り当てられている文字列へのポインターを返します。

### <a name="example"></a>例

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_type"></a>  char_traits::char_type

文字の型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `CharType`のシノニムです。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#copy)copy`char_type` の例を参照してください。

## <a name="compare"></a>  char_traits::compare

指定した文字数まで 2 つの文字列を比較します。

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>パラメーター

*str1*\
相互に比較する 2 つの文字列の最初の文字列。

*str2*\
相互に比較する 2 つの文字列の 2 番目の文字列。

*_Num*\
比較する文字列内の要素の数。

### <a name="return-value"></a>戻り値

最初の文字列が 2 番目の文字列より少ない場合は負の値、2 つの文字列が等しい場合は 0、最初の文字列が 2 番目の文字列より多い場合は正の値になります。

### <a name="remarks"></a>解説

文字列間の比較は要素ごとに行われます。最初に等しいかどうかがテストされ、シーケンス テスト内の要素のペアが等しくない場合は、より少ないかどうかのテストが実行されます。

2 つの文字列の比較で一定の範囲が等しい場合でも、1 つの文字列が他の文字列より長い場合、2 つのうち短い文字列が長い文字列よりも少ないということになります。

### <a name="example"></a>例

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="copy"></a>  char_traits::copy

1 つの文字列から別の文字列に指定した数の文字をコピーします。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。 代わりに [char_traits::_Copy_s](#copy_s) の使用を検討してください。

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>パラメーター

*_To*\
コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列の先頭にある要素。

*_From*\
コピーされるソース文字列または文字配列の先頭にある要素。

*_Num*\
コピーする要素の数。

### <a name="return-value"></a>戻り値

コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列にコピーされる最初の要素。

### <a name="remarks"></a>解説

ソースとコピー先の文字シーケンスは重複できません。

### <a name="example"></a>例

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="copy_s"></a>  char_traits::_Copy_s

1 つの文字列から別の文字列に指定した数の文字をコピーします。

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>パラメーター

*dest*\
コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列。

*dest_size*\
*Dest*のサイズ。 `char_type` が**char**の場合、このサイズはバイト単位です。 `char_type` が**wchar_t**場合、このサイズは単語単位です。

*_From*\
コピーされるソース文字列または文字配列。

*カウント*\
コピーする要素の数。

### <a name="return-value"></a>戻り値

コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列。

### <a name="remarks"></a>解説

ソースとコピー先の文字シーケンスは重複できません。

### <a name="example"></a>例

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="eof"></a>  char_traits::eof

ファイルの終端 (EOF) 文字を返します。

```cpp
static int_type eof();
```

### <a name="return-value"></a>戻り値

EOF 文字。

### <a name="remarks"></a>解説

EOF や WEOF など、ファイルの終端を表す値。

C++ 規格によると、この値は、有効な `char_type` 値に対応しないようにする必要があります。 Microsoft C++コンパイラは**char**型にこの制約を適用しますが、型**wchar_t**には適用しません。 次に示しているのはその例です。

### <a name="example"></a>例

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="eq"></a>  char_traits::eq

2 つの `char_type` 文字が等しいかどうかをテストします。

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>パラメーター

*_Ch1*\
等しいかどうかをテストする 2 つの文字の最初の文字。

*_Ch2*\
等しいかどうかをテストする 2 つの文字の 2 番目文字。

### <a name="return-value"></a>戻り値

最初の文字が 2 番目の文字に等しい場合は **true**、等しくない場合は **false** です。

### <a name="example"></a>例

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="eq_int_type"></a>  char_traits::eq_int_type

`int_type` として表される 2 つの文字が等しいかどうかをテストします。

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>パラメーター

*_Ch1*\
`int_type`s として等しいかどうかをテストする2つの文字の最初の文字。

*_Ch2*\
`int_type` として等しいかどうかをテストする 2 つの文字の 2 番目の文字。

### <a name="return-value"></a>戻り値

最初の文字が 2 番目の文字に等しい場合は **true**、等しくない場合は **false** です。

### <a name="example"></a>例

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="find"></a>  char_traits::find

文字の範囲内で指定した文字が最初に出現する位置を検索します。

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>パラメーター

*str*\
検索される文字列の先頭の文字。

*_Num*\
検索される範囲内で先頭から数えてその位置が何番目かを示す数。

*_Ch*\
範囲内で検索される文字。

### <a name="return-value"></a>戻り値

一致するものが見つかった場合は、範囲内で指定された値の最初に出現した箇所へのポインター、それ以外の場合は、Null ポインター。

### <a name="example"></a>例

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="int_type"></a>  char_traits::int_type

`char_type` 型の文字、またはファイルの終端 (EOF) 文字を表すことができる整数型。

```cpp
typedef long int_type;
```

### <a name="remarks"></a>解説

`int_type` `CharType` 型の値を型キャストして、元の値を変更せずに `CharType` に戻すことができるようにする必要があります。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#eq_int_type)eq_int_type`int_type` の例を参照してください。

## <a name="length"></a>  char_traits::length

文字列の長さを返します。

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>パラメーター

*str*\
長さを測定する C 文字列。

### <a name="return-value"></a>戻り値

Null 終端文字を含まない、測定するシーケンス内の要素の数。

### <a name="example"></a>例

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="lt"></a>  char_traits::lt

1 つの文字が別の文字よりも小さいかどうかをテストします。

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>パラメーター

*_Ch1*\
少ないかどうかをテストする 2 つの文字の最初の文字。

*_Ch2*\
少ないかどうかをテストする 2 つの文字の 2 番目の文字。

### <a name="return-value"></a>戻り値

最初の文字が 2 番目の文字より少ない場合は **true**、それ以外の場合は **false** です。

### <a name="example"></a>例

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="move"></a>  char_traits::move

シーケンス内の文字を、指定された文字数だけ、重複が生じる可能性のある別のシーケンスにコピーします。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。 代わりに [char_traits::_Move_s](#move_s) の使用を検討してください。

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>パラメーター

*_To*\
コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列の先頭にある要素。

*_From*\
コピーされるソース文字列または文字配列の先頭にある要素。

*_Num*\
ソース文字列からコピーされる要素の数。

### <a name="return-value"></a>戻り値

最初の要素 *_To* 、コピーされた文字のシーケンスを受け取る対象の文字列または文字配列にコピーされます。

### <a name="remarks"></a>解説

ソースと宛先が重複してもかまいません。

### <a name="example"></a>例

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="move_s"></a>  char_traits::_Move_s

シーケンス内の文字を、指定された文字数だけ、重複が生じる可能性のある別のシーケンスにコピーします。

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>パラメーター

*dest*\
コピーされた文字のシーケンスの受信ターゲットとなる文字列または文字配列の先頭にある要素。

*dest_size*\
*Dest*のサイズ。 `char_type` が**char**の場合、これはバイト単位です。 `char_type` が**wchar_t**場合、これは単語単位です。

*_From*\
コピーされるソース文字列または文字配列の先頭にある要素。

*カウント*\
ソース文字列からコピーされる要素の数。

### <a name="return-value"></a>戻り値

コピーされた文字のシーケンスを受け取る対象の文字列または文字配列にコピーされた最初*の要素の*位置。

### <a name="remarks"></a>解説

ソースと宛先が重複してもかまいません。

### <a name="example"></a>例

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="not_eof"></a>  char_traits::not_eof

文字がファイルの終端 (EOF) 文字であるかどうかをテストします。

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>パラメーター

*_Ch*\
EOF 文字であるかどうかをテストされる `int_type` として表される文字。

### <a name="return-value"></a>戻り値

文字の `int_type` が EOF 文字の文字と等しくない場合にテストされる文字の `int_type` 表現。

文字 `int_type` 値が EOF `int_type` 値と等しい場合は、**false** です。

### <a name="example"></a>例

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="off_type"></a>  char_traits::off_type

ストリーム内の位置間のオフセットを表すことのできる整数型。

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>解説

型は、さまざまなストリーム位置決め操作に関連するオフセット バイト数を格納できるオブジェクトを記述する、符号付き整数です。 通常は、[streamoff](../standard-library/ios-typedefs.md#streamoff) のシノニムですが、基本的にその型と同じプロパティを持っています。

## <a name="pos_type"></a>  char_traits::pos_type

ストリーム内の位置を表すことのできる整数型。

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>解説

この型は、ストリーム内の任意のファイル位置インジケーターを復元するために必要なすべての情報を格納できるオブジェクトを表します。 通常は、[streampos](../standard-library/ios-typedefs.md#streampos) のシノニムですが、どのような場合も基本的にその型と同じプロパティを持っています。

## <a name="state_type"></a>  char_traits::state_type

ストリーム内のマルチバイト文字の変換状態を表す型。

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>解説

この型は、変換状態を表すことができるオブジェクトを表します。 通常は、`mbstate_t` のシノニムですが、どのような場合も基本的にその型と同じプロパティを持っています。

## <a name="to_char_type"></a>  char_traits::to_char_type

`int_type` の文字を `char_type` の対応する文字に変換し、その結果を返します。

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>パラメーター

*_Ch*\
`int_type` として表される `char_type` 文字。

### <a name="return-value"></a>戻り値

`char_type` 文字に対応する `int_type` 文字。

このように表すことができない *_Ch*の値は、指定されていない結果を生成します。

### <a name="remarks"></a>解説

変換操作 [to_int_type](#to_int_type) と `to_char_type` は互いに逆の操作を実行できるので、次のようになります。

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

`int_type` *x*と

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

`char_type` *x*の場合。

### <a name="example"></a>例

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="to_int_type"></a>  char_traits::to_int_type

`char_type` の文字を `int_type` の対応する文字に変換し、その結果を返します。

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>パラメーター

*_Ch*\
`char_type` として表される `int_type` 文字。

### <a name="return-value"></a>戻り値

`int_type` 文字に対応する `char_type` 文字。

### <a name="remarks"></a>解説

変換操作 `to_int_type`to_char_type[ と ](#to_char_type) は互いに逆の操作を実行できるので、次のようになります。

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

`int_type` *x*の場合

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

`char_type` *x*の場合。

### <a name="example"></a>例

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>参照

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
