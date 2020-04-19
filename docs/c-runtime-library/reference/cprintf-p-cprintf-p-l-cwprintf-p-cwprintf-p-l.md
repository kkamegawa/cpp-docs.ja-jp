---
title: _cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l
ms.date: 11/04/2016
api_name:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
ms.openlocfilehash: a02de28a61812147c192495c4794830f85567a10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942645"
---
# <a name="_cprintf_p-_cprintf_p_l-_cwprintf_p-_cwprintf_p_l"></a>_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l

書式化してコンソールに出力します。書式指定文字列で位置指定パラメーターをサポートしています。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _cprintf_p(
   const char * format [,
   argument] ...
);
int _cprintf_p_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_p(
   const wchar * format [,
   argument] ...
);
int _cwprintf_p_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*argument*<br/>
省略可能なパラメーター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

出力した文字数。エラーが発生した場合は負の値を返します。

## <a name="remarks"></a>Remarks

これらの関数は、 **_putch**関数と **_putwch**関数を使用して文字を出力することで、一連の文字および値を書式設定し、コンソールに直接出力します。 各*引数*(存在する場合) は、対応する書式指定に従って変換および出力さ*れます。* 形式は、 [printf_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)関数の*format*パラメーターと同じ形式と機能を持ちます。 **_Cprintf_p**と**cprintf_s**の違いは、 **_cprintf_p**は位置指定パラメーターをサポートしている点です。これにより、書式設定文字列で引数を使用する順序を指定できます。 詳細については、「[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**Fprintf_p**、 **printf_p**、および**sprintf_p**関数とは異なり、出力時に、 **_cprintf_p**と **_cwprintf_p**はどちらもラインフィード文字をキャリッジリターンラインフィード (cr-lf) の組み合わせに変換しません。 重要な違いは、 **_cwprintf_p**では、Windows NT で使用されている場合に Unicode 文字が表示されることです。 **_Cprintf_p**とは異なり、 **_cwprintf_p**は現在のコンソールのロケール設定を使用します。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

> [!IMPORTANT]
> *format* にユーザー定義の文字列を指定しないでください。

また、 **_cprintf_s**や **_cwprintf_s**のように、これらは入力ポインターと書式指定文字列を検証します。 *Format*または*引数*が**NULL**の場合、または書式指定文字列に無効な書式指定文字が含まれている場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_p**|**_cprintf_p**|**_cprintf_p**|**_cwprintf_p**|
|**_tcprintf_p_l**|**_cprintf_p_l**|**_cprintf_p_l**|**_cwprintf_p_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_cprintf_p**、 **_cprintf_p_l**|\<conio.h>|
|**_cwprintf_p**、 **_cwprintf_p_l**|\<conio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_cprintf_p.c
// This program displays some variables to the console
// using the _cprintf_p function.

#include <conio.h>

int main( void )
{
    int         i = -16,
                h = 29;
    unsigned    u = 62511;
    char        c = 'A';
    char        s[] = "Test";

    // Note that console output does not translate
    // \n as standard output does. Use \r\n instead.
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",
                h, i, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)<br/>
[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
