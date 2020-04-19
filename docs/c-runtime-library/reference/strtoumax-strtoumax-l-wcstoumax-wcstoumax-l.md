---
title: strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l
ms.date: 11/04/2016
api_name:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
ms.openlocfilehash: a4ed09ad51e538f3964fea87fa55e410c79d3a5d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957687"
---
# <a name="strtoumax-_strtoumax_l-wcstoumax-_wcstoumax_l"></a>strtoumax、_strtoumax_l、wcstoumax、_wcstoumax_l

サポートされる最大の符号なし整数型の整数値に文字列を変換します。

## <a name="syntax"></a>構文

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
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

**strtoumax**は、変換された値 (存在する場合)、またはオーバーフロー時の**UINTMAX_MAX**を返します。 変換を実行できない場合、 **strtoumax**は0を返します。 **wcstoumax**は、値と同様を**strtoumax**に返します。 どちらの関数でも、オーバーフローまたはアンダーフローが発生した場合、 **errno**は**ERANGE**に設定されます。

リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

これらの各関数は、入力文字列*Strsource*を**uintmax_t**整数値に変換します。

**strtoumax**は、数値の一部として認識できない最初の文字で文字列*strsource*の読み取りを停止します。 これは、終端の null 文字である場合もあれば、*基数*以上の最初の数字の場合もあります。 ロケールの**LC_NUMERIC** category 設定によって、 *strsource*の小数点文字が認識されます。 詳細については、「[setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。 **strtoumax**と**wcstoumax**は現在のロケールを使用します。 **_strtoumax_l**と **_wcstoumax_l**は、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**Strtoumax**のワイド文字バージョンは**wcstoumax**;*Strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax**は、 *strsource*が次の形式の文字列を指すことを想定しています。

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

*空白*は、空白文字とタブ文字で構成される場合があります。これは無視されます。 *数字*は1桁以上の10進数です。 *文字*は、' a ' ~ ' z ' (または ' a ' ~ ' z ') の1つ以上の文字です。 この形式に一致しない文字を見つけるとスキャンを停止します。 *Base*が 2 ~ 36 の場合は、数値の基数として使用されます。 *Base*が0の場合、 *strsource*によって指定された文字列の最初の文字が、ベースを決定するために使用されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' 以外の場合、文字列は 8 進数と解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 'a' ～ 'z' (または 'A' ～ 'Z') の文字には、10 ～ 35 の値が割り当てられています。*基数*よりも小さい値が割り当てられている文字のみ許可されます。 基数の範囲外にある文字を最初に見つけた時点で、スキャンは停止されます。 たとえば、 *base*が0で、スキャンされた最初の文字が ' 0 ' の場合、8進数の整数と見なされ、' 8 ' または ' 9 ' の文字がスキャンを停止します。 **strtoumax**では、正符号 **+** () または負 **-** 符号 () のプレフィックスを使用できます。先頭の負符号は、戻り値が、変換された文字列の絶対値の2つの補数であることを示します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<stdlib.h> または \<wchar.h>|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h> または \<wchar.h>|

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
[strtoimax、_strtoimax_l、wcstoimax、_wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
