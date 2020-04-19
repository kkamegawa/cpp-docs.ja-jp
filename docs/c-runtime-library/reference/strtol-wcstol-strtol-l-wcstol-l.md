---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 01/14/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: 83054e1b31b56fda96bdea198ab34d65d633f335
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123930"
---
# <a name="opno-locstrtol-opno-locwcstol-opno-loc_strtol_l-opno-loc_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

文字列を**長**整数値に変換します。

## <a name="syntax"></a>構文

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*string*\
NULL で終わる変換対象の文字列。

*end_ptr*\
出力パラメーター。最後に解釈された文字の後の文字を指すように設定されます。 **NULL**の場合は無視されます。

*base*\
使用する基数。

*ロケール*\
使用するロケール。

## <a name="return-value"></a>戻り値

**strtol** 、 **wcstol** 、 **_strtol_l** 、および **_wcstol_l** は、*文字列*で表される値を返します。 変換できない場合は0を返します。 この表現でオーバーフローが発生すると、 **LONG_MAX** または **LONG_MIN** が返されます。

オーバーフローまたはアンダーフローが発生した場合、 **errno** は **ERANGE** に設定されます。 *String*が**NULL**の場合は **EINVAL** に設定されます。 または、 *base*が0以外で、2より小さいか、または36より大きい場合。 **ERANGE** 、 **EINVAL** 、およびその他のリターンコードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**strtol** 、 **wcstol** 、 **_strtol_l** 、および **_wcstol_l** 関数は、*文字列*を**long 型**に変換します。 これらは、数値の一部として認識されない最初の文字の*文字列*の読み取りを停止します。 終端の null 文字、または*基本*文字以上の最初の英数字を指定できます。

**wcstol** と **_wcstol_l** は **strtol** と **_strtol_l** のワイド文字バージョンです。 *文字列*引数はワイド文字列です。 これらの関数は **strtol** と同じように動作し、それ以外の場合は **_strtol_l** ます。 ロケールの **LC_NUMERIC** カテゴリの設定によって、*文字列*の小数点文字 (小数のマーカーまたは小数点) の認識が決まります。 関数 **strtol** および **wcstol** 現在のロケールを使用します。 **_strtol_l** と **_wcstol_l** 渡されたロケールを代わりに使用します。 詳細については、「[setlocale]」および「[ロケール](../../c-runtime-library/locale.md)」を参照してください。

*End_ptr*が**NULL**の場合は無視されます。 それ以外の場合は、スキャンを停止した文字へのポインターが*end_ptr*が指す位置に格納されます。 有効な数字が見つからない場合、または無効なベースが指定されている場合は、変換できません。 *文字列*の値は、 *end_ptr*が指す位置に格納されます。

**strtol** は、次の形式の文字列を指す*文字列*を想定しています。

> [*空白*][{ **+** &#124; **-** }][**0** [{ **x** &#124; **x** }]] [*英数字*]

角かっこ (`[ ]`) は、省略可能な要素を囲みます。 中かっこと縦棒 (`{ | }`) は、1つの要素の代替を囲みます。 *空白*は空白文字とタブ文字で構成され、無視されます。 *英数字*は、10進数または文字の ' a ' ~ ' z ' (または ' a ' ~ ' z ') です。 このフォームに収まらない最初の文字は、スキャンを停止します。 *Base*が 2 ~ 36 の場合は、数値の基数として使用されます。 *Base*が0の場合は、文字列が指す文字列の先頭の*文字が、* ベースを決定するために使用されます。 最初の文字が0で、2番目の文字が ' x ' または ' X ' でない場合、文字列は8進数の整数として解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 ' A ' ~ ' z ' (または ' A ' ~ ' Z ') の文字には、10 ~ 35 の値が割り当てられます。 スキャンでは、値が*基数*より小さい文字のみが許可されます。 基数の範囲外にある文字を最初に見つけた時点で、スキャンは停止されます。 たとえば、*文字列*が "01" で始まるとします。 *Base*が0の場合、スキャナーはそれが8進数の整数であると想定します。 ' 8 ' または ' 9 ' の文字があると、スキャンが停止します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> または \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> または \<wchar.h>|

**_strtol_l** 関数と **_wcstol_l** 関数は、標準 C ライブラリの一部ではなく、Microsoft 固有の関数です。 互換性の詳細については、「[互換性](../compatibility.md)」を参照してください。

## <a name="example"></a>使用例

[strtod](strtod-strtod-l-wcstod-wcstod-l.md)の例を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../data-conversion.md)の\
[ロケール](../locale.md)\
[localeconv](localeconv.md)\
[setlocale、_wsetlocale](setlocale-wsetlocale.md)\
[文字列から数値への値の関数](../string-to-numeric-value-functions.md)\
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)
