---
title: _strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l
ms.date: 11/04/2016
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: be7d779bac50d332dde879c9d5b070fd2bf7e7e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946435"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l

文字列を符号なし **__int64**値に変換します。

## <a name="syntax"></a>構文

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*strSource*<br/>
NULL で終わる変換対象の文字列。

*endptr*<br/>
スキャンの終了位置を示す文字へのポインター。

*base*<br/>
使用する基数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_strtoui64**は、文字列*strsource*に示されている値を返します。ただし、オーバーフローを引き起こす場合を除き、 **_UI64_MAX**を返します。 変換を実行できない場合、 **_strtoui64**は0を返します。

**_UI64_MAX**は制限で定義されています。始め.

*Strsource*が**NULL**であるか、*ベース*が0以外で、2より大きいか、または36を超える場合、 **errno**は**EINVAL**に設定されます。

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_Strtoui64**関数は、 *strsource*を**unsigned** **__int64**に変換します。 **_wcstoui64**は、 **_strtoui64**のワイド文字バージョンです。*Strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

どちらの関数も、数値の一部として認識できない最初の文字で文字列*Strsource*の読み取りを停止します。 これは、終端の null 文字でもかまいません。または、*基数*以上の最初の数値文字である場合もあります。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

現在のロケールの**LC_NUMERIC** category 設定によって、 *strsource*の小数点文字が認識されます。詳細については、「 [setlocale](setlocale-wsetlocale.md)」を参照してください。 _L サフィックスが付いていない関数は、現在のロケールを使用します。 **_strtoui64_l**と **_wcstoui64_l**は、代わりに渡されたロケールを使用することを除いて、 **_l**サフィックスが付いていない対応する関数と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**_strtoui64**は、 *strsource*が次の形式の文字列を指すことを想定しています。

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

*空白*は、空白文字とタブ文字で構成される場合があります。これは無視されます。 *数字*は1桁以上の10進数です。 *文字*は、' a ' ~ ' z ' (または ' a ' ~ ' z ') の1つ以上の文字です。 この形式に一致しない文字を見つけるとスキャンを停止します。 *Base*が 2 ~ 36 の場合は、数値の基数として使用されます。 *Base*が0の場合は、 *strsource*が指す文字列の先頭の文字が、ベースを決定するために使用されます。 最初の文字が 0 で、2 番目の文字が 'x' または 'X' 以外の場合、文字列は 8 進数と解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 'a' ～ 'z' (または 'A' ～ 'Z') の文字には、10 ～ 35 の値が割り当てられています。*基数*よりも小さい値が割り当てられている文字のみ許可されます。 基数の範囲外にある文字を最初に見つけた時点で、スキャンは停止されます。 たとえば、 *base*が0で、スキャンされた最初の文字が ' 0 ' の場合、8進数の整数と見なされ、' 8 ' または ' 9 ' の文字がスキャンを停止します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> または \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
