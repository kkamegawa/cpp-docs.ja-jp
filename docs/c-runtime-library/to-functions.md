---
title: to 系関数
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: df8f59088cd402503fe31f768557e3ed936b31ec
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301692"
---
# <a name="to-functions"></a>to 系関数

各 **to** 関数と、もしあれば関連付けられているマクロは、任意の 1 文字を別の文字に変換します。

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper、_toupper、towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[tolower、_tolower、towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>コメント

**to** 系関数とマクロの変換は以下のとおりです。

|ルーチンによって返される値|マクロ|説明|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|`c` を ASCII 文字に変換する|
|`tolower`|`tolower`|該当する場合、`c` を小文字に変換する|
|`_tolower`|`_tolower`|`c` を小文字に変換する|
|`towlower`|[なし]|`c` を対応するワイド文字の小文字に変換する|
|`toupper`|`toupper`|該当する場合、`c` を大文字に変換する|
|`_toupper`|`_toupper`|`c` を大文字に変換する|
|`towupper`|[なし]|c を対応するワイド文字の大文字に変換する|

マクロとしても定義されている **to** ルーチンの関数バージョンを使用するには、`#undef` ディレクティブでマクロ定義を削除するか、CTYPE.H を含めないようにします。 /Za コンパイラ オプションを使用する場合、コンパイラは `toupper` または `tolower` の関数バージョンを使用します。 `toupper` および `tolower` 関数の宣言は STDLIB.H にあります。

`__toascii` ルーチンは `c` の下位 7 ビット以外をすべて 0 に設定し、変換値が ASCII 文字セットの文字を表すようにします。 `c` がすでに ASCII 文字セットの文字に該当している場合、`c` は変更されません。

`tolower` および `toupper` ルーチン:

- 現在のロケールの `LC_CTYPE` カテゴリに準拠します (`tolower` は `isupper` を呼び出し、`toupper` は `islower` を呼び出します)。

- `c` が現在のロケールにおいて変換可能な文字の大文字か小文字を表し、その逆の大文字か小文字がそのロケールに存在する場合、`c` を変換します。 それ以外の場合、`c` は変換されません。

`_tolower` および `_toupper` ルーチン:

- ロケールに依存しない、高速バージョンの `tolower` および **toupper** です。

- **isascii(** `c` **)** と、**isupper(** `c` **)** または **islower(** `c` **)** のいずれかがゼロ以外の場合にのみ使用できます。

- `c` が変換可能な適切な大文字または小文字の ASCII 文字でない場合、結果は未定義です。

次の条件が両方ともゼロ以外の場合にのみ `towlower` および `towupper` 関数は`c` の変換されたコピーを返します。 それ以外の場合、`c` は変換されません。

- `c` が適切な大文字または小文字のワイド文字である (つまり `iswupper` または **iswlower** が、それぞれゼロ以外の場合)。

- 対応する大文字または小文字のワイド文字がある (つまり、`iswlower` または **iswupper** が、それぞれゼロ以外の場合)。

## <a name="example"></a>使用例

```c
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>関連項目

[データ変換](../c-runtime-library/data-conversion.md)<br/>
[ロケール](../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../c-runtime-library/is-isw-routines.md)
