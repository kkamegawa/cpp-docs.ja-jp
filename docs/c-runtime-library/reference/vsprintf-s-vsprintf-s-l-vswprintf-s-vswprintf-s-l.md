---
title: vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l
ms.date: 09/12/2019
api_name:
- _vswprintf_s_l
- vsprintf_s
- vswprintf_s
- _vsprintf_s_l
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
- vswprintf_s
- vsprintf_s
- _vstprintf_s
helpviewer_keywords:
- _vstprintf_s_l function
- vsprintf_s_l function
- _vstprintf_s function
- vswprintf_s function
- vstprintf_s function
- vstprintf_s_l function
- vswprintf_s_l function
- vsprintf_s function
- _vsprintf_s_l function
- formatted text [C++]
- _vswprintf_s_l function
ms.assetid: 60e90518-57f0-4f1b-b732-f62a69702833
ms.openlocfilehash: 84e85885acf671b49e1e3226234a1d3337577768
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945269"
---
# <a name="vsprintf_s-_vsprintf_s_l-vswprintf_s-_vswprintf_s_l"></a>vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l

引数リストへのポインターを使用して、書式付き出力を書き込みます。 これらの関数は、「 [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの[vsprintf \_、_vsprintf_l、vswprintf、_vswprintf_l、_vswprintf_l](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)です。

## <a name="syntax"></a>構文

```C
int vsprintf_s(
   char *buffer,
   size_t numberOfElements,
   const char *format,
   va_list argptr
);
int _vsprintf_s_l(
   char *buffer,
   size_t numberOfElements,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vswprintf_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_s_l(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsprintf_s(
   char (&buffer)[size],
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int vswprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
出力の格納位置。

*numberOfElements*<br/>
*バッファー*のサイズ (文字単位)。

*format*<br/>
書式の指定。

*argptr*<br/>
引数リストへのポインター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**vsprintf_s**と**vswprintf_s**は、書き込まれた文字数を返します。終端の null 文字は含まれません。出力エラーが発生した場合は、負の値が返されます。 *バッファー*または*形式*が null ポインターの場合、 *numberofelements*がゼロの場合、または書式指定文字列に無効な書式指定文字が含まれている場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

これらの各関数は、引数リストへのポインターを受け取り、指定されたデータを書式設定して、*バッファー*が指すメモリに書き込みます。

**vswprintf_s**は、 **Vswprintf**の ISO C 標準に準拠しています。これには、 **size_t**型の2番目のパラメーター *count*が必要です。

これらの関数は、セキュリティ保護されたバージョンが位置指定パラメーターをサポートする点を除いて、セキュリティが万全でないバージョンと同じです。 詳細については、「[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

でC++は、これらの関数の使用はテンプレートのオーバーロードによって簡略化されています。 オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 また、セキュリティで保護されていない関数を、対応するセキュリティで保護された関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**vstprintf_s (_l)**|**vsprintf_s**|**vsprintf_s**|**vswprintf_s**|
|**_vstprintf_s_l**|**_vsprintf_s_l**|**_vsprintf_s_l**|**_vswprintf_s_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**vsprintf_s**、 **_vsprintf_s_l**|\<stdio.h> および \<stdarg.h>|\<varargs.h>*|
|**vswprintf_s**、 **_vswprintf_s_l**|\<stdio.h> または \<wchar.h>、および \<stdarg.h>|\<varargs.h>*|

\* UNIX V との互換性用。

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_vsprintf_s.c
// Compile with: cl /W4 crt_vsprintf_s.c
// This program uses vsprintf_s to write to a buffer.
// The size of the buffer is determined by _vscprintf.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void test( char const * const format, ... )
{
   va_list args;
   int len;
   char * buffer;

   va_start( args, format );
   len = _vscprintf( format, args ) // _vscprintf doesn't count
                               + 1; // terminating '\0'
   buffer = (char *) malloc( len * sizeof(char) );
   if ( NULL != buffer )
   {
      vsprintf_s( buffer, len, format, args );
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

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)
