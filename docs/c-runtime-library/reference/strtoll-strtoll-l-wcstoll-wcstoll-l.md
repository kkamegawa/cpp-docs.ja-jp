---
title: strtoll、_strtoll_l、wcstoll、_wcstoll_l
ms.date: 11/04/2016
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: 152efb26f0a2e9a312654e37a95bee15f386aa9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946446"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll、_strtoll_l、wcstoll、_wcstoll_l

文字列を**long** **型**の値に変換します。

## <a name="syntax"></a>構文

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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

**strtoll**では、文字列*strtoll*で表される値が返されます。ただし、オーバーフローが発生する場合を除きます。この場合、 **LLONG_MAX**または**LLONG_MIN**が返されます。 この関数は、変換を実行できない場合には 0 を返します。 **wcstoll** **は、** と同様に値を返します。

**LLONG_MAX**と**LLONG_MIN**は、制限で定義されています。始め.

*Strsource*が**NULL**であるか、*ベース*が0以外で、2より大きいか、または36を超える場合、 **errno**は**EINVAL**に設定されます。

リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Strtoll**関数は、 *strtoll*を**long** **型**に変換します。 どちらの関数も、数値の一部として認識できない最初の文字で文字列*Strsource*の読み取りを停止します。 これは、終端の null 文字である場合もあれば、*基数*以上の最初の数字の場合もあります。 **wcstoll**は、ワイド文字バージョンの**strtoll**です。*Strsource*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

ロケールの**LC_NUMERIC**カテゴリの設定によって、 *strsource*の小数点文字が認識されます。詳細については、「 [setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。 **_L**サフィックスが付いていない関数は、現在のロケールを使用します。 **_strtoll_l**と **_wcstoll_l**は、渡されたロケールを代わりに使用する点を除いて、サフィックスが付いていない対応する関数と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*Endptr*が**NULL**でない場合は、スキャンを停止した文字へのポインターが*endptr*が指す位置に格納されます。 変換を実行できない場合 (有効な数字が見つからなかった場合、または無効な base を指定した場合)、 *Strsource*の値は*endptr*が指す位置に格納されます。

**strtoll**では、 *strtoll*が次の形式の文字列を指す必要があります。

> [*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [*digits*  &#124; *letters*]

*空白*は空白文字とタブ文字で構成される場合があり、これらは無視されます。*数字*は1桁以上の10進数です。*文字*は、' a ' ~ ' z ' (または ' a ' ~ ' z ') の1つ以上の文字です。 この形式に一致しない文字を見つけるとスキャンを停止します。 *Base*が 2 ~ 36 の場合は、数値の基数として使用されます。 *Base*が0の場合、 *strsource*によって指定された文字列の最初の文字が、ベースを決定するために使用されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' 以外の場合、文字列は 8 進数と解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 'a' ～ 'z' (または 'A' ～ 'Z') の文字には、10 ～ 35 の値が割り当てられています。*基数*よりも小さい値が割り当てられている文字のみ許可されます。 基数の範囲外にある文字を最初に見つけた時点で、スキャンは停止されます。 たとえば、 *base*が0で、スキャンされた最初の文字が ' 0 ' の場合、8進数の整数と見なされ、' 8 ' または ' 9 ' の文字がスキャンを停止します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtoll**、 **_strtoll_l**|\<stdlib.h>|
|**wcstoll**、 **_wcstoll_l**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[文字列を数値に変換する関数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
