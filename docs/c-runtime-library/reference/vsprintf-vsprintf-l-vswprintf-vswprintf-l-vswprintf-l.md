---
title: vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、__vswprintf_l
ms.date: 09/03/2019
api_name:
- _vswprintf_l
- _vsprintf_l
- vsprintf
- vswprintf
- __vswprintf_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vstprintf
- vswprintf
- _vstprintf
- vsprintf
- __vswprintf_l
- _vsprintf_l
- _vswprintf_l
- vswprintf_l
helpviewer_keywords:
- __vswprintf_l function
- _vstprintf_l function
- formatted text
- vstprintf_l function
- _vswprintf_l function
- vsprintf_l function
- buffers, avoiding overruns
- buffer overruns
- vswprintf_l function
- buffers, buffer overruns
- vstprintf function
- _vsprintf_l function
- vswprintf function
- vsprintf function
- _vstprintf function
ms.assetid: b8ef1c0d-58f9-4a18-841a-f1a989e1c29b
ms.openlocfilehash: 9efb30428a146ec72c48d68ec411b21ca5bfef79
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945339"
---
# <a name="vsprintf-_vsprintf_l-vswprintf-_vswprintf_l-__vswprintf_l"></a>vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、__vswprintf_l

引数リストへのポインターを使用して、書式付き出力を書き込みます。 これらの関数にはセキュリティが強化されたバージョンがあります。「[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int vsprintf(
   char *buffer,
   const char *format,
   va_list argptr
);
int _vsprintf_l(
   char *buffer,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vswprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
int __vswprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsprintf(
   char (&buffer)[size],
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int vswprintf(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vswprintf_l(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>パラメーター

*格納*\
出力の格納位置。

*数*\
この関数のワイド文字列バージョンで格納する最大文字数。

*形式*\
書式の指定。

*argptr*\
引数リストへのポインター。

*国*\
使用するロケール。

## <a name="return-value"></a>戻り値

**vsprintf**と**vswprintf**は、書き込まれた文字数を返します。終端の null 文字は含まれません。出力エラーが発生した場合は、負の値が返されます。 *Buffer*または*format*が null ポインターの場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

これらの各関数は、引数リストへのポインターを受け取り、指定されたデータを書式設定して、*バッファー*が指すメモリに書き込みます。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

> [!IMPORTANT]
> **Vsprintf**を使用すると、書き込まれる文字数を制限することはできません。つまり、この関数を使用するコードでは、バッファーオーバーランが発生しやすくなります。 代わりに [_vsnprintf](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) を使用するか、または [_vscprintf](vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md) を呼び出して、必要なバッファーの大きさを決定します。 また、*形式*がユーザー定義の文字列ではないことを確認します。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

**vswprintf**は ISO C 規格に準拠しています。これには、 **size_t**型の2番目のパラメーター *count*が必要です。 古い非標準の動作を強制するには、 **_CRT_NON_CONFORMING_SWPRINTFS**を定義します。 以前の動作は将来のバージョンではない可能性があるため、新しい準拠の動作を使用するようにコードを変更する必要があります。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**vstprintf (_l)**|**vsprintf**|**vsprintf**|**vswprintf**|
|**vstprintf_l (_d)**|**_vsprintf_l**|**_vsprintf_l**|**_vswprintf_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**vsprintf**、 **_vsprintf_l**|\<stdio.h> および \<stdarg.h>|\<varargs.h>*|
|**vswprintf**、 **_vswprintf_l**|\<stdio.h> または \<wchar.h>、および \<stdarg.h>|\<varargs.h>*|

\* UNIX V との互換性用。

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_vsprintf.c
// compile with: cl /W4 crt_vsprintf.c
// This program uses vsprintf to write to a buffer.
// The size of the buffer is determined by _vscprintf.

#define _CRT_SECURE_NO_WARNINGS
#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void test( char const * const format, ... )
{
    va_list args;
    int     len;
    char    *buffer;

    // retrieve the variable arguments
    va_start( args, format );

    len = _vscprintf( format, args ) // _vscprintf doesn't count
                                + 1; // terminating '\0'

    buffer = (char*)malloc( len * sizeof(char) );
    if ( 0 != buffer )
    {
        vsprintf( buffer, format, args ); // C4996
        // Note: vsprintf is deprecated; consider using vsprintf_s instead
        puts( buffer );

        free( buffer );
    }
    va_end( args );
}

int main( void )
{
   test( "%d %c %d", 123, '<', 456 );
   test( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)\
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)\
[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)\
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)\
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)\
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)\
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)
