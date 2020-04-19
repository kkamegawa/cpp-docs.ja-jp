---
title: _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l
ms.date: 11/04/2016
api_name:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
ms.openlocfilehash: c14da7158a3e15a74a01630a8a1b475d3e496de9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938969"
---
# <a name="_cprintf_s-_cprintf_s_l-_cwprintf_s-_cwprintf_s_l"></a>_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l

書式化してコンソールに出力します。 これらのバージョンの [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」にあるとおり、セキュリティが強化されています。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _cprintf_s(
   const char * format [,
   argument] ...
);
int _cprintf_s_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_s(
   const wchar * format [,
   argument] ...
);
int _cwprintf_s_l(
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

出力された文字数。

## <a name="remarks"></a>Remarks

これらの関数は、一連の文字と値を書式設定してコンソールに直接出力します。 **_putch**関数 ( **_cwprintf_s**の場合は **_putwch** ) を使用して文字を出力します。 各*引数*(存在する場合) は、対応する書式指定に従って変換および出力さ*れます。* 形式は、 [printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)関数の*format*パラメーターと同じ形式と機能を持ちます。 **Fprintf_s**、 **printf_s**、および**sprintf_s**関数とは異なり、出力時に、 **_cprintf_s**と **_cwprintf_s**はどちらもラインフィード文字をキャリッジリターンラインフィード (cr-lf) の組み合わせに変換しません。

重要な違いは、 **_cwprintf_s**では、Windows NT で使用されている場合に Unicode 文字が表示されることです。 **_Cprintf_s**とは異なり、 **_cwprintf_s**は現在のコンソールのロケールを使用します。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

> [!IMPORTANT]
> *format* にユーザー定義の文字列を指定しないでください。

セキュリティで保護されていないバージョン (「 [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)」を参照) と同様に、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、パラメーターを検証し、無効なパラメーターハンドラーを呼び出します ( *format*が null の場合)。pointer. これらの関数は、書式指定文字列自体の検証も行う点で、セキュリティが万全ではないバージョンと異なります。 未知の書式指定子や不適切な形式の書式指定子がある場合、これらの関数は無効なパラメーター ハンドラーを呼び出します。 どのような場合でも、実行の継続が許可された場合、関数は-1 を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_cprintf_s**、 **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**、 **_cwprintf_s_l**|\<conio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_cprintf_s.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
   int      i = -16, h = 29;
   unsigned u = 62511;
   char     c = 'A';
   char     s[] = "Test";

   /* Note that console output does not translate \n as
    * standard output does. Use \r\n instead.
    */
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)<br/>
[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
