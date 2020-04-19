---
title: strtod、_strtod_l、wcstod、_wcstod_l
ms.date: 10/20/2017
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: 5372525eb99dc9d39e31b10def0377c9aad5296c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946491"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod、_strtod_l、wcstod、_wcstod_l

文字列を倍精度値に変換します。

## <a name="syntax"></a>構文

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*strSource*<br/>
NULL で終わる変換対象の文字列。

*endptr*<br/>
スキャンの終了位置を示す文字へのポインター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**strtod**は、表現がオーバーフローを引き起こす場合を除き、浮動小数点数の値を返します。この場合、関数は +/-**HUGE_VAL**を返します。 **HUGE_VAL**の符号は、表現できない値の符号と一致します。 変換を実行できない場合、またはアンダーフローが発生した場合、 **strtod**は0を返します。

**wcstod**は、 **strtod**にと同様値を返します。 どちらの関数でも、オーバーフローまたはアンダーフローが発生して、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されると、 **errno**は**ERANGE**に設定されます。 戻り値の詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

各関数は、入力文字列の*Strsource*を**double**に変換します。 **Strtod**関数は、 *strsource*を倍精度値に変換します。 **strtod**は、数値の一部として認識できない最初の文字で文字列*strsource*の読み取りを停止します。 数値として認識できない最初の文字が、終端の NULL 文字の場合もあります。 **wcstod**は**strtod**のワイド文字バージョンです。*Strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

現在のロケールの**LC_NUMERIC** category 設定によって、 *strsource*の小数点文字が認識されます。 詳細については、「[setlocale](setlocale-wsetlocale.md)」をご覧ください。 **_L**サフィックスが付いていない関数は、現在のロケールを使用します。 **_strtod_l**は、渡された*ロケール*を代わりに使用する点を除いて、 **_strtod_l**と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**strtod**は、 *strsource*が次のいずれかの形式の文字列を指すことを想定しています。

[*空白*][*sign*]{*数字*[*基数* *]* &#124; *基数* *}* [{**e** &#124; **e}** [*sign*] *digits*] [*whitespace*] [*sign*] {**0x** &#124; **0x**} {*hexdigits* [*radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **p}** [*sign*] *hexdigits*] [*whitespace*] [*sign*] {**INF** &#124; **無限大**} [*whitespace*] [*sign*] **NAN** [*sequence*]

省略可能な先頭の*空白*文字は、スペースとタブ文字で構成され、無視されます。*sign*は正符号 (+) またはマイナス記号 (-) です。*数字*は1桁以上の10進数です。*hexdigits*は、1つまたは複数の16進数字です。*基数*は、小数点文字 (既定の "C" ロケールのピリオド (.))、またはロケールに固有の値 (現在のロケールが異なる場合、または*ロケール*が指定されている場合) です。*シーケンス*は、英数字またはアンダースコア文字のシーケンスです。 10進数と16進数の両方の形式で、小数点文字の前に数字がない場合は、少なくとも1つは小数点以下を表す必要があります。 10進数形式では、10進数の後に指数部を指定できます。指数部は、指数部の導入文字 (**e**または**e**) と、必要に応じて符号付き整数で構成されます。 16進数形式では、16進数字の後に指数部を指定できます。指数部は、指数部を表す文字 (**p**または**p**) と、必要に応じて符号付き16進整数 (指数部は2の累乗) で構成されます。 どちらの形式でも、指数部と小数点文字のどちらも表示されない場合、基数のポイント文字は文字列の最後の桁に続くと見なされます。 **INF**と**NAN**の両方の形式では、Case は無視されます。 これらの形式のいずれかに一致しない最初の文字は、スキャンを停止します。

これらの関数の UCRT バージョンは、Fortran スタイル (**d**または**d**) の指数文字の変換をサポートしていません。 この非標準の拡張機能は、CRT の以前のバージョンでサポートされており、コードの互換性に影響する変更点がある可能性があります。 UCRT バージョンでは、16進文字列と INF 値と NAN 値のラウンドトリップがサポートされていましたが、以前のバージョンではサポートされていませんでした。 これにより、コードに重大な変更が加えられる可能性もあります。 たとえば、文字列 "0x1a" は、 **strtod**によって以前のバージョンの0.0 として解釈されますが、ucrt バージョンでは26.0 として解釈されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtod**、 **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> または &lt;stdlib.h> |
|**wcstod**、 **_wcstod_l**|C: &lt;stdlib.h > または &lt;wchar.h > C++: &lt;cstdlib >、&lt;stdlib.h > または &lt;wchar.h > |

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
