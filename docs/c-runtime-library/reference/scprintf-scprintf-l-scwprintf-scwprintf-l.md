---
title: "_scprintf、_scprintf_l、_scwprintf、_scwprintf_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _scprintf_l
- _scwprintf
- _scwprintf_l
- _scprintf
apilocation:
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
apitype: DLLExport
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
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 2b99a80cc4d64ffd4e88225b8de0952a1c81ad87
ms.lasthandoff: 02/24/2017

---
# <a name="scprintf-scprintfl-scwprintf-scwprintfl"></a>_scprintf、_scprintf_l、_scwprintf、_scwprintf_l
書式設定された文字列内の文字数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
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
  
#### <a name="parameters"></a>パラメーター  
 `format`  
 書式指定文字列。  
  
 `argument`  
 省略可能な引数。  
  
 `locale`  
 使用するロケール。  
  
 詳細については、[書式の指定](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)に関する記事をご覧ください。  
  
## <a name="return-value"></a>戻り値  
 文字列が出力されたか、指定した書式設定コードを使用してファイルまたはバッファーに送信された場合は、生成される文字数を返します。 戻り値には、終端の NULL 文字は含まれません。 `_scwprintf` は、ワイド文字に対して同じ機能を果たします。  
  
 `format` が `NULL` ポインターである場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は -1 を返し、`errno` を `EINVAL` に設定します。  
  
 エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。  
  
## <a name="remarks"></a>コメント  
 各 `argument` (指定されている場合) は、`format` 中の対応する書式指定に応じて変換されます。 format は通常の文字で構成し、その形式と機能は [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 関数の `format` 引数と同じです。  
  
 これらの関数のうち `_l` サフィックスが付けられたバージョンは、現在のスレッド ロケールの代わりに渡されたロケール パラメーターを使用する点を除いて同じです。  
  
> [!IMPORTANT]
>  `format` にユーザー定義の文字列を指定しないでください。  
  
### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ  
  
|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sctprintf`|`_scprintf`|`_scprintf`|`_scwprintf`|  
|`_sctprintf_l`|`_scprintf_l`|`_scprintf_l`|`_scwprintf_l`|  
  
## <a name="requirements"></a>要件  
  
|ルーチン|必須ヘッダー|  
|-------------|---------------------|  
|`_scprintf`, `_scprintf_l`|\<stdio.h>|  
|`_scwprintf`, `_scwprintf_l`|\<stdio.h> または \<wchar.h>|  
  
 互換性について詳しくは、概要の「[互換性](../../c-runtime-library/compatibility.md)」をご覧ください。  
  
## <a name="example"></a>例  
  
```  
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
 [ストリーム入出力](../../c-runtime-library/stream-i-o.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、_sscanf_l、swscanf、_swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 系関数](../../c-runtime-library/vprintf-functions.md)