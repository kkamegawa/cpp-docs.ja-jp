---
title: strtof、_strtof_l、wcstof、_wcstof_l
ms.date: 04/05/2018
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: b2b2e7d230074b5a464260d36b41c28b9951d65b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957753"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof、_strtof_l、wcstof、_wcstof_l

文字列を単精度浮動小数点値に変換します。

## <a name="syntax"></a>構文

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>パラメーター

*strSource*<br/>
NULL で終わる変換対象の文字列。

*endptr*<br/>
スキャンの終了位置を示す文字へのポインター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**strtof**は、表現がオーバーフローを引き起こす場合を除き、浮動小数点数の値を返します。この場合、関数は +/-**HUGE_VALF**を返します。 **HUGE_VALF**の符号は、表現できない値の符号と一致します。 変換を実行できない場合、またはアンダーフローが発生した場合、 **strtof**は0を返します。

**wcstof**は、 **strtof**にと同様値を返します。 どちらの関数でも、オーバーフローまたはアンダーフローが発生して、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されると、 **errno**は**ERANGE**に設定されます。

リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

各関数は、入力文字列の*Strsource*を**float**に変換します。 **Strtof**関数は、 *strsource*を単精度値に変換します。 **strtof**は、数値の一部として認識できない最初の文字で文字列*strsource*の読み取りを停止します。 数値として認識できない最初の文字が、終端の NULL 文字の場合もあります。 **wcstof**は**strtof**のワイド文字バージョンです。*Strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

現在のロケールの**LC_NUMERIC** category 設定によって、 *strsource*の小数点文字が認識されます。詳細については、「 [setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。 **_L**サフィックスが付いていない関数は、現在のロケールを使用します。サフィックスが付いているものは、代わりに渡されたロケールを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**strtof**は、 *strsource*が次の形式の文字列を指すことを想定しています。

[*空白*][*sign*][*数字*][ __.__ *数字*][{**e** &#124; **e}** [*sign*]*数字*]

*空白*は空白文字とタブ文字で構成される場合があり、これらは無視されます。*sign*は、正符号 **+** () または **-** 負符号 () です。*数字*は1桁以上の10進数です。 小数点文字の前に数字がない場合は、少なくとも 1 つの数字が小数点文字の後に必要です。 10進数の後には指数部を指定できます。指数部は、指数部の最初の文字 (**e**または**e**) と、必要に応じて符号付き整数で構成されます。 指数部と小数点文字のいずれも指定されない場合は、文字列の最後の数字の後に小数点文字が続くと想定されます。 この形式に一致しない文字を見つけるとスキャンを停止します。

これらの関数の UCRT バージョンは、Fortran スタイル (**d**または**d**) の指数文字の変換をサポートしていません。 この非標準の拡張機能は、CRT の以前のバージョンでサポートされており、コードの互換性に影響する変更点がある可能性があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtof**、 **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> または \<stdlib.h>|
|**wcstof**、 **_wcstof_l**|C: \<stdlib.h > または \<wchar.h > C++: &lt;cstdlib >、\<stdlib.h > または \<wchar.h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
