---
title: fgetc、fgetwc
ms.date: 11/04/2016
api_name:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: 92f44c65802f3baed37078574577bf108bbcd09a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940891"
---
# <a name="fgetc-fgetwc"></a>fgetc、fgetwc

ストリームから単一の文字を読み取ります。

## <a name="syntax"></a>構文

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

**fgetc**は、 **int**として読み取られた文字を返すか、または**EOF**を返してエラーまたはファイルの末尾を示します。 **fgetwc**は、読み取った文字に対応するワイド文字を[wint_t](../../c-runtime-library/standard-types.md)として返します。または、ファイルのエラーまたは終了を示す**WEOF**を返します。 どちらの関数でも、 **feof**または**ferror**を使用して、エラーとファイルの終端の条件を区別します。 読み取りエラーが発生すると、ストリームのエラー インジケーターが設定されます。 *Stream*が**NULL**の場合、 **fgetc**および**fgetwc**は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、 **EOF**を返します。

## <a name="remarks"></a>Remarks

これらの各関数は、*ストリーム*に関連付けられているファイルの現在位置から1文字を読み取ります。 関数は、次の文字 (定義されている場合) を指すように、関連ファイルのポインターをインクリメントします。 ストリームがファイルの末尾にある場合、ストリームのファイルの末尾を示すインジケーターが設定されます。

**fgetc**は**getc**に相当しますが、関数およびマクロとしてではなく、関数としてのみ実装されます。

**fgetwc**は、 **fgetc**のワイド文字バージョンです。*ストリーム*がテキストモードとバイナリモードのどちらで開かれているかに応じて、 **c**はマルチバイト文字またはワイド文字として読み取られます。

**_nolock** サフィックスが付いているバージョンは同じものですが、他のスレッドによる干渉から保護されない点が異なります。

テキスト モードとバイナリ モードのワイド文字とマルチバイト文字の処理の詳細については、「[Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)」 (テキスト モードとバイナリ モードの Unicode ストリーム入出力) を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetctxt"></a>入力: crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
