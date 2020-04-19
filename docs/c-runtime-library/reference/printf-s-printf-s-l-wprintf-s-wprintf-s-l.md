---
title: printf_s、_printf_s_l、wprintf_s、_wprintf_s_l
ms.date: 11/04/2016
api_name:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
- wprintf_s
- printf_s
helpviewer_keywords:
- wprintf_s function
- tprintf_s function
- _tprintf_s function
- printf_s_l function
- printf_s function
- _printf_s_l function
- printf function, format specification fields
- printf function, using
- _tprintf_s_l function
- wprintf_s_l function
- formatted text [C++]
- tprintf_s_l function
- _wprintf_s_l function
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
ms.openlocfilehash: f8b324b5f3c23b324bdcd43e3529ad3a3d4d6847
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950183"
---
# <a name="printf_s-_printf_s_l-wprintf_s-_wprintf_s_l"></a>printf_s、_printf_s_l、wprintf_s、_wprintf_s_l

標準出力ストリームに書式付きで出力します。 これらのバージョンの [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」にあるとおり、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
int printf_s(
   const char *format [,
   argument]...
);
int _printf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf_s(
   const wchar_t *format [,
   argument]...
);
int _wprintf_s_l(
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

**Printf_s**関数は、一連の文字と値を書式設定し、標準出力ストリームである**stdout**に出力します。 *書式*指定文字列の後に引数を指定する場合、*書式*指定文字列には引数の出力形式を決定する仕様が含まれている必要があります。

**Printf_s**と**printf**の主な違いは、 **printf_s**では書式指定文字列が有効な書式指定文字であることを確認するのに対し、 **printf**では書式指定文字列が null ポインターであるかどうかのみをチェックするためです。 いずれかのチェックが失敗した場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**を**EINVAL**に設定します。

**Errno**とエラーコードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

**printf_s**と**fprintf_s**は同じように動作しますが、 **printf_s**は、type**ファイル**の出力先ではなく**stdout**に出力を書き込みます。 詳細については、「[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)」を参照してください。

**wprintf_s**は、 **printf_s**のワイド文字バージョンです。*format*は、ワイド文字列です。 ストリームが ANSI モードで開かれている場合、 **wprintf_s**と**printf_s**は同じように動作します。 **printf_s**は、現在 UNICODE ストリームへの出力をサポートしていません。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_Unicode が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

*Format*引数は、通常の文字、エスケープシーケンス、および (引数が*形式*の場合) 書式指定形式で構成されます。 通常の文字とエスケープシーケンスは、外観の順に**stdout**にコピーされます。 たとえば、次の関数を呼び出します。

```C
printf_s("Line one\n\t\tLine two\n");
```

この例では、次のように出力されます。

```Output
Line one
        Line two
```

[書式指定](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)は必ずパーセント記号 ( **%** ) で始まり、左から右に読み取られます。 **Printf_s**が最初の書式指定 (存在する場合) を検出すると、最初の引数の値を*書式*の後に変換し、それに応じて出力します。 2 番目の書式指定を見つけると、2 番目の引数を変換して出力します。 書式指定よりも引数の数が多い場合、余分な引数は無視されます。 書式指定より引数が少ないと、結果は予測できません。

> [!IMPORTANT]
> *format* にユーザー定義の文字列を指定しないでください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**printf_s**、 **_printf_s_l**|\<stdio.h>|
|**wprintf_s**、 **_wprintf_s_l**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_printf_s.c
/* This program uses the printf_s and wprintf_s functions
* to produce formatted output.
*/

#include <stdio.h>

int main( void )
{
   char   ch = 'h', *string = "computer";
   int    count = -9234;
   double fp = 251.7366;
   wchar_t wch = L'w', *wstring = L"Unicode";

   /* Display integers. */
   printf_s( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",
           count, count, count );

   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   /* Display in different radixes. */
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   /* Display characters. */

   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);

   /* Display strings. */

   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",
   string, string, wstring, wstring);
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",
       string, string, wstring, wstring);

   /* Display real numbers. */
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );

   /* Display pointer. */
   printf_s( "\nAddress as:   %p\n", &count);

}
```

### <a name="sample-output"></a>出力例

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF78
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
