---
title: _scprintf、_scprintf_l、_scwprintf、_scwprintf_l
ms.date: 11/04/2016
api_name:
- _scprintf_l
- _scwprintf
- _scwprintf_l
- _scprintf
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
- scprintf
- _scprintf_l
- _scwprintf_l
- _scprintf
- scwprintf
- _scwprintf
- scprintf_l
- _sctprintf_l
- scwprintf_l
- _sctprintf
helpviewer_keywords:
- scprintf function
- sctprintf_l function
- scwprintf_l function
- _scwprintf_l function
- _sctprintf_l function
- sctprintf function
- _scwprintf function
- _scprintf_l function
- _sctprintf function
- scprintf_l function
- formatted text [C++]
- _scprintf function
- scwprintf function
ms.assetid: ecbb0ba6-5f4c-4ce6-a64b-144ad8b5fe92
ms.openlocfilehash: 8d7f682156d37538f6ac152e6d93814877631a5c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948805"
---
# <a name="_scprintf-_scprintf_l-_scwprintf-_scwprintf_l"></a>_scprintf、_scprintf_l、_scwprintf、_scwprintf_l

書式設定された文字列内の文字数を返します。

## <a name="syntax"></a>構文

```C
int _scprintf(
   const char *format [,
   argument] ...
);
int _scprintf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _scwprintf(
   const wchar_t *format [,
   argument] ...
);
int _scwprintf_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*argument*<br/>
省略可能な引数。

*locale*<br/>
使用するロケール。

詳細については、「 [printf 関数と wprintf 関数の書式指定フィールド](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」を参照してください。

## <a name="return-value"></a>戻り値

文字列が出力されたか、指定した書式設定コードを使用してファイルまたはバッファーに送信された場合は、生成される文字数を返します。 戻り値には、終端の NULL 文字は含まれません。 **_scwprintf**は、ワイド文字に対して同じ関数を実行します。

*Format*が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

各*引数*(存在する場合) は、*形式*で対応する書式指定に従って変換されます。 形式は通常の文字で構成され、 [printf](printf-printf-l-wprintf-wprintf-l.md)の*format*引数と同じ形式と機能を持ちます。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

> [!IMPORTANT]
> *format* にユーザー定義の文字列を指定しないでください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**sctprintf (_d)**|**_scprintf**|**_scprintf**|**_scwprintf**|
|**sctprintf_l (_d)**|**_scprintf_l**|**_scprintf_l**|**_scwprintf_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**scprintf**、 **scprintf_l (_d** )|\<stdio.h>|
|**_scwprintf**、 **_scwprintf_l**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt__scprintf.c

#define _USE_MATH_DEFINES

#include <stdio.h>
#include <math.h>
#include <malloc.h>

int main( void )
{
   int count;
   int size;
   char *s = NULL;

   count = _scprintf( "The value of Pi is calculated to be %f.\n",
                      M_PI);

   size = count + 1; // the string will need one more char for the null terminator
   s = malloc(sizeof(char) * size);
   sprintf_s(s, size, "The value of Pi is calculated to be %f.\n",
                      M_PI);
   printf("The length of the following string will be %i.\n", count);
   printf("%s", s);
   free( s );
}
```

```Output
The length of the following string will be 46.
The value of Pi is calculated to be 3.141593.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
