---
title: feof
ms.date: 11/04/2016
api_name:
- feof
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: cf6cfdb63689f5d69cc45dd407ecc6b08a7a7a73
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941142"
---
# <a name="feof"></a>feof

ストリームのファイルの末尾をテストします。

## <a name="syntax"></a>構文

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

**Feof**関数は、読み取り操作がファイルの末尾を越えて読み取ろうとした場合、0以外の値を返します。それ以外の場合は0を返します。 ストリームポインターが**NULL**の場合、関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、 **feof**は0を返します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Feof**ルーチン (関数とマクロの両方として実装されます) は、*ストリーム*の末尾が渡されたかどうかを判断します。 ファイルの終わりが渡されると、読み取り操作は、ストリームが閉じられるか、または[rewind](rewind.md)、 **fsetpos**、 [fseek](fseek-fseeki64.md)、または**clearerr**が呼び出されるまで、ファイルの終端のインジケーターを返します。

たとえば、ファイルに10バイトが含まれていて、ファイルから10バイトを読み取った場合、 **feof**は0を返します。これは、ファイルポインターがファイルの末尾にある場合でも、末尾を越えて読み取ろうとしていないためです。 11番目のバイトを読み取った後にのみ、 **feof**は0以外の値を返します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**feof**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crt_feoftxt"></a>入力: crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
