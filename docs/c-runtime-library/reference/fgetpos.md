---
title: fgetpos
ms.date: 11/04/2016
api_name:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 27d25b29f656d1df889e5f83857ca437f609a07a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940840"
---
# <a name="fgetpos"></a>fgetpos

ストリームのファイル位置インジケーターを取得します。

## <a name="syntax"></a>構文

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
対象のストリーム。

*po*<br/>
位置インジケーターのストレージ。

## <a name="return-value"></a>戻り値

成功した場合、 **fgetpos**は0を返します。 エラーが発生した場合、0以外の値を返し、 **errno**に次のマニフェスト定数のいずれかを設定します (STDIO で定義されています)。H):**EBADF**。指定されたストリームが有効なファイルポインターではない、アクセスできない、または**EINVAL**であることを意味します。これは、*ストリーム*値または*pos*の値が無効であることを意味します (いずれかが null ポインターの場合など)。 *Stream*または*pos*が**NULL**ポインターの場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、関数は無効なパラメーターハンドラーを呼び出します。

## <a name="remarks"></a>Remarks

**Fgetpos**関数は、*ストリーム*引数のファイル位置インジケーターの現在の値を取得し、 *pos*が指すオブジェクトに格納します。**Fsetpos**関数は、後で*pos*に格納されている情報を使用して、 **fgetpos**が呼び出された時点の*ストリーム*引数のポインターをその位置にリセットできます。 *Pos*値は内部形式で格納され、 **fgetpos**と**fsetpos**でのみ使用されます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetpostxt"></a>入力: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>出力: crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
