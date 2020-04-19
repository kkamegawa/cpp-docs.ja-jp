---
title: strtoull、_strtoull_l、wcstoull、_wcstoull_l
ms.date: 11/04/2016
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 70d7a53219a9176e848fde239d90291366b67eb0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957601"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull、_strtoull_l、wcstoull、_wcstoull_l

文字列を符号なし長整数の値に変換します。

## <a name="syntax"></a>構文

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
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

**strtoull**は、変換された値 (存在する場合)、またはオーバーフロー時の**ULLONG_MAX**を返します。 変換を実行できない場合、 **strtoull**は0を返します。 **wcstoull**は、 **strtoull**にと同様値を返します。 どちらの関数でも、オーバーフローまたはアンダーフローが発生した場合、 **errno**は**ERANGE**に設定されます。

リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

これらの各関数は、入力文字列*Strsource*を**符号なし** **long** **長**整数値に変換します。

**strtoull**は、数値の一部として認識できない最初の文字で文字列*strsource*の読み取りを停止します。 これは、終端の null 文字である場合もあれば、*基数*以上の最初の数字の場合もあります。 ロケールの**LC_NUMERIC**カテゴリの設定によって、 *strsource*の小数点文字が認識されます。詳細については、「 [setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。 **strtoull**と**wcstoull**は現在のロケールを使用します。代わりに、 **_strtoull_l**と **_wcstoull_l**は渡されたロケールを使用しますが、それ以外の場合は同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**wcstoull**は**strtoull**のワイド文字バージョンであり、その*strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull**は、 *strsource*が次の形式の文字列を指すことを想定しています。

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

*空白*は、空白文字とタブ文字で構成される場合があります。これは無視されます。 *数字*は1桁以上の10進数です。 *文字*は、' a ' ~ ' z ' (または ' a ' ~ ' z ') の1つ以上の文字です。 この形式に一致しない文字を見つけるとスキャンを停止します。 *Base*が 2 ~ 36 の場合は、数値の基数として使用されます。 *Base*が0の場合、 *strsource*によって指定された文字列の最初の文字が、ベースを決定するために使用されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' 以外の場合、文字列は 8 進数と解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 'a' ～ 'z' (または 'A' ～ 'Z') の文字には、10 ～ 35 の値が割り当てられています。*基数*よりも小さい値が割り当てられている文字のみ許可されます。 基数の範囲外にある文字を最初に見つけた時点で、スキャンは停止されます。 たとえば、 *base*が0で、スキャンされた最初の文字が ' 0 ' の場合、8進数の整数と見なされ、' 8 ' または ' 9 ' の文字がスキャンを停止します。 **strtoull**では、正符号 **+** () または負 **-** 符号 () のプレフィックスを使用できます。先頭の負符号は、戻り値が否定されることを示します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> または \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[strtod](strtod-strtod-l-wcstod-wcstod-l.md) の例をご覧ください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
