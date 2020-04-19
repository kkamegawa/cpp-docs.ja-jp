---
title: clearerr_s
ms.date: 11/04/2016
api_name:
- clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 12e76ba5133d99ed2d45d7cf15bada2ad1c5c38b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939147"
---
# <a name="clearerr_s"></a>clearerr_s

ストリームのエラー インジケーターをリセットします。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [clearerr](clearerr.md) です。

## <a name="syntax"></a>構文

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**ファイル**構造へのポインター

## <a name="return-value"></a>戻り値

成功した場合は0。*Stream*が**NULL**の場合は、 **EINVAL** 。

## <a name="remarks"></a>Remarks

**Clearerr_s**関数は、*ストリーム*のエラーインジケーターとファイルの終端インジケーターをリセットします。 エラーインジケーターは自動的にクリアされません。指定されたストリームのエラーインジケーターが設定されると、そのストリームに対する操作は、 **clearerr_s**、 **clearerr**、 [fseek](fseek-fseeki64.md)、 **fsetpos**、または[rewind](rewind.md)が呼び出されるまでエラー値を返し続けます。

*Stream*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>入力

```Input
n
```

### <a name="output"></a>Output

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
