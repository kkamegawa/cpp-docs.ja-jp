---
title: _printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l
ms.date: 11/04/2016
api_name:
- _printf_p
- _wprintf_p
- _printf_p_l
- _wprintf_p_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wprintf_p
- _wprintf_p
- printf_p_l
- _printf_p
- printf_p
- _wprintf_p_l
- _printf_p_l
- wprintf_p_l
helpviewer_keywords:
- printf_p function
- printf_p_l function
- wprintf_p function
- wprintf_p_l function
- _tprintf_p_l function
- _wprintf_p function
- _wprintf_p_l function
- _printf_p function
- tprintf_p_l function
- _printf_p_l function
ms.assetid: 1b7e9ef9-a069-45db-af9d-c2730168322e
ms.openlocfilehash: 555739fbcdd3503461d7b831660a94602f244aa3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950266"
---
# <a name="_printf_p-_printf_p_l-_wprintf_p-_wprintf_p_l"></a>_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l

標準出力ストリームに書式付きで出力します。書式指定文字列でのパラメーターの使用順序を指定できます。

## <a name="syntax"></a>構文

```C
int _printf_p(
   const char *format [,
   argument]...
);
int _printf_p_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int _wprintf_p(
   const wchar_t *format [,
   argument]...
);
int _wprintf_p_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*argument*<br/>
省略可能な引数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

出力した文字数を返します。エラーが発生した場合は負の値を返します。

## <a name="remarks"></a>Remarks

**_Printf_p**関数は、一連の文字と値を書式設定し、標準出力ストリームである**stdout**に出力します。 *書式*指定文字列の後に引数を指定する場合は、*書式*指定文字列に引数の出力形式を決定する仕様が含まれている必要があります (「 [printf_p 位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」を参照してください)。

**_Printf_p**と**printf_s**の違いは、 **_printf_p**は位置指定パラメーターをサポートしている点です。これにより、書式設定文字列で引数を使用する順序を指定できます。 詳細については、「[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**_wprintf_p**は、 **_printf_p**のワイド文字バージョンです。ストリームが ANSI モードで開かれている場合、これらは同じように動作します。 **_printf_p**は、現在 UNICODE ストリームへの出力をサポートしていません。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

> [!IMPORTANT]
> *format* にユーザー定義の文字列を指定しないでください。

*Format*または*引数*が**NULL**の場合、または書式指定文字列に無効な書式指定文字が含まれている場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、 **_printf_p**関数と **_wprintf_p**関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf_p**|**_printf_p**|**_printf_p**|**_wprintf_p**|
|**_tprintf_p_l**|**_printf_p_l**|**_printf_p_l**|**_wprintf_p_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_printf_p**、 **_printf_p_l**|\<stdio.h>|
|**_wprintf_p**、 **_wprintf_p_l**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_printf_p.c
// This program uses the _printf_p and _wprintf_p
// functions to choose the order in which parameters
// are used.

#include <stdio.h>

int main( void )
{
   // Positional arguments
   _printf_p( "Specifying the order: %2$s %3$s %1$s %4$s %5$s.\n",
              "little", "I'm", "a", "tea", "pot");

   // Resume arguments
   _wprintf_p( L"Reusing arguments: %1$d %1$d %1$d %1$d\n", 10);

   // Width argument
   _printf_p("Width specifiers: %1$*2$s", "Hello\n", 10);
}
```

```Output
Specifying the order: I'm a little tea pot.
Reusing arguments: 10 10 10 10
Width specifiers:     Hello
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
