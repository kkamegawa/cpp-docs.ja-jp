---
title: '&lt;locale&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 3c5d81aecb5e78a8fd3c3f32da82f6048ae4fac8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453563"
---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt; 関数

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a>  has_facet

特定のファセットが指定されたロケールに格納されているかどうかをテストします。

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>パラメーター

*Loc*\
ファセットの有無をテストするロケール。

### <a name="return-value"></a>戻り値

ロケールにテスト対象のファセットがある場合は **true**、ない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`use_facet` を呼び出す前に必須ではないファセットがロケール内にリストされているかどうかを確認し、なかった場合に例外がスローされるのを回避するために役立ちます。

### <a name="example"></a>例

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a>  isalnum

ロケールの要素が英字または数字であるかどうかをテストします。

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする英数字要素。

*Loc*\
テストする英数字要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が英数字である場合は **true**、そうでない場合は **false**。

### <a name="example"></a>例

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a>  isalpha

ロケールの要素が英字であるかどうかをテストします。

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする英字要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が英字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**アルファ**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a>  iscntrl

ロケールの要素が制御文字であるかどうかをテストします。

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が制御文字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **cntrl**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a>  isdigit

ロケールの要素が数字であるかどうかをテストします。

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が数字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**桁**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a>  isgraph

ロケールの要素が英字または句読点であるかどうかをテストします。

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が英字または句読点である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**グラフ**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a>  islower

ロケールの要素が小文字であるかどうかをテストします。

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が小文字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**低い**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a>  isprint

ロケールの要素が印刷可能な文字であるかどうかをテストします。

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が印刷可能である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**印刷**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a>  ispunct

ロケールの要素が句読点であるかどうかをテストします。

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が句読点である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **punct**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a>  isspace

ロケールの要素が空白文字であるかどうかをテストします。

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が余白である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**領域**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a>  isupper

ロケールの要素が大文字であるかどうかをテストします。

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストされた要素が大文字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>::**上限**、 `Ch`)。

### <a name="example"></a>例

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a>  isxdigit

ロケールの要素が 16 進数を表すために使用される文字であるかどうかをテストします。

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
テストする要素。

*Loc*\
テストする要素を含むロケール。

### <a name="return-value"></a>戻り値

テストする要素が 16 進数を表すために使用される文字である場合は **true**、そうでない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [は](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **xdigit**、 `Ch`)。

16 進数字は、0 から 9 までの数字と A から F までの文字 (大文字と小文字を区別しない) を使用して 0 から 15 までの 10 進数字を表す 16 進数を使用します。

### <a name="example"></a>例

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a>  tolower

文字を小文字に変換します。

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
小文字に変換される文字。

*Loc*\
変換される文字を含むロケール。

### <a name="return-value"></a>戻り値

小文字に変換された文字。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [tolower](../standard-library/ctype-class.md#tolower)( `Ch`).

### <a name="example"></a>例

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a>  toupper

文字を大文字に変換します。

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>パラメーター

*ハーフ*\
大文字に変換される文字。

*Loc*\
変換される文字を含むロケール。

### <a name="return-value"></a>戻り値

大文字に変換された文字。

### <a name="remarks"></a>Remarks

このテンプレート関数は、 [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **chartype**> > `Loc`() を返します。 [toupper](../standard-library/ctype-class.md#toupper)( `Ch`).

### <a name="example"></a>例

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a>  use_facet

ロケールに格納されている指定された型のファセットへの参照を返します。

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>パラメーター

*Loc*\
参照されるファセットの型を含む const ロケール。

### <a name="return-value"></a>戻り値

引数のロケールに含まれるクラス `Facet` のファセットへの参照。

### <a name="remarks"></a>Remarks

このテンプレート関数によって返されるファセットへの参照は、含んでいるロケールのコピーが存在する限り有効です。 このようなクラス `Facet` のファセット オブジェクトが引数のロケールにリストされていない場合、この関数は `bad_cast` 例外をスローします。

### <a name="example"></a>例

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)
