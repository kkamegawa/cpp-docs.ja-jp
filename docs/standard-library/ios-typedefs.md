---
title: '&lt;ios&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 20bffbeb7720274302633c5dda9e6364c06d5b54
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687884"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedefs

## <a name="ios"></a>ios

従来の iostream ライブラリの ios クラスをサポートします。

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ios](../standard-library/basic-ios-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="streamoff"></a>streamoff

内部操作をサポートします。

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Remarks

型は、さまざまなストリーム位置決め操作に関連するオフセット バイト数を格納できるオブジェクトを記述する、符号付き整数です。 この表現は、少なくとも 32 ビットあります。 これは、ストリーム内の任意のバイト位置を表すのに必ずしも十分なサイズとは限りません。 @No__t_0 値は、通常、間違ったオフセットを示します。

## <a name="streampos"></a>streampos

バッファー ポインターまたはファイル ポインターの現在の位置を保持します。

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Remarks

この型は、[fpos](../standard-library/fpos-class.md)< `mbstate_t`> の同意語です。

### <a name="example"></a>例

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a>  streamsize

ストリームのサイズを表します。

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Remarks

型は、さまざまなストリーム操作に関連する要素数のカウントを格納できるオブジェクトを記述する、符号付き整数です。 この表現は、少なくとも 16 ビットあります。 これは、ストリーム内の任意のバイト位置を表すのに必ずしも十分なサイズとは限りません。

### <a name="example"></a>例

次のプログラムをコンパイルおよび実行した後に、test.txt ファイルの中身を見て、`streamsize` の設定の効果を確認します。

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## <a name="wios"></a>  wios

従来の iostream ライブラリの wios クラスをサポートします。

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ios](../standard-library/basic-ios-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="wstreampos"></a>wstreampos

バッファー ポインターまたはファイル ポインターの現在の位置を保持します。

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Remarks

この型は、[fpos](../standard-library/fpos-class.md)< `mbstate_t`> の同意語です。

### <a name="example"></a>例

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```
