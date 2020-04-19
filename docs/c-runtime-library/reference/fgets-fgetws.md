---
title: fgets、fgetws
ms.date: 07/11/2018
api_name:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 3f68bee181ebb20eb7a0a2eaca02a72c4dc03616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957400"
---
# <a name="fgets-fgetws"></a>fgets、fgetws

ストリームから文字列を取得します。

## <a name="syntax"></a>構文

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
データの格納場所。

*numChars*<br/>
読み取り対象の最大文字数。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

これらの関数はそれぞれ*str*を返します。 **NULL**は、エラーまたはファイルの終端状態を示すために返されます。 エラーが発生したかどうかを判断するには、 **feof**または**ferror**を使用します。 *Str*または*stream*が null ポインターであるか、 *numchars*が0以下の場合、この関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**NULL**を返します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Fgets**関数は、入力*ストリーム*引数から文字列を読み取り、 *str*に格納します。 **fgets**は、現在のストリームの位置から、最初の改行文字、ストリームの末尾、または読み取られた文字数が*numchars* -1 の範囲の文字を読み取ります。 *Str*に格納された結果に null 文字が追加されます。 改行文字を読み取ると、文字列に含まれます。

**fgetws**は、 **fgets**のワイド文字バージョンです。

**fgetws**は、*ストリーム*がテキストモードとバイナリモードのどちらで開かれているかに応じて、ワイド文字の引数*str*をマルチバイト文字の文字列またはワイド文字列として読み取ります。 Unicode およびマルチバイトのストリーム入出力におけるテキスト モードおよびバイナリ モードの使い方の詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」および「[テキスト モードとバイナリ モードの Unicode ストリーム入出力](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>入力: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
