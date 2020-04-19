---
title: ungetc、ungetwc
ms.date: 11/04/2016
api_name:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: f3b6c6ed3fe8ff5976afa1da2ed437e25c923b99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957416"
---
# <a name="ungetc-ungetwc"></a>ungetc、ungetwc

ストリームに文字をプッシュ バックします。

## <a name="syntax"></a>構文

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
プッシュする文字。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

成功した場合、これらの各関数は、文字引数*c*を返します。 *C*をプッシュバックできない場合、または文字が読み取られなかった場合、入力ストリームは変更されず、 **ungetc**は**EOF**を返します。**ungetwc**は**WEOF**を返します。 *Stream*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **EOF**または**WEOF**が返され、 **errno**が**EINVAL**に設定されます。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Ungetc**関数は、文字*c*を*ストリーム*にプッシュし、ファイルの終端のインジケーターをクリアします。 ストリームは、読み取り用に開かれている必要があります。 *ストリーム*に対する後続の読み取り操作は、 *c*で始まります。 **Ungetc**を使用してストリームに**EOF**をプッシュしようとすると無視されます。

**Ungetc**によってストリームに配置された文字は、その文字がストリームから読み取られる前に**fflush**、 [fseek](fseek-fseeki64.md)、 **fsetpos**、または[rewind](rewind.md)が呼び出された場合、消去される可能性があります。 ファイル位置インジケーターの値は、文字がプッシュ バックされる前のファイル位置インジケーターの値になります。 ストリームに対応する外部のストレージは変更されません。 テキストストリームに対する**ungetc**の呼び出しが成功した場合、プッシュバックされたすべての文字が読み取りまたは破棄されるまで、ファイル位置インジケーターは指定されません。 バイナリストリームに対する**ungetc**の呼び出しが成功するたびに、ファイル位置インジケーターがデクリメントされます。呼び出しの前の値が0の場合、呼び出しの後に値が未定義になります。

2回の呼び出しの間に読み取りまたはファイル位置の操作を行わずに**ungetc**が2回呼び出された場合、結果は予測できません。 **Fscanf**を呼び出した後に、別の読み取り操作 ( **getc**など) が実行されていないと、 **ungetc**の呼び出しが失敗する可能性があります。 これは、 **fscanf**自体が**ungetc**を呼び出すためです。

**ungetwc**は、 **ungetc**のワイド文字バージョンです。 ただし、テキストストリームまたはバイナリストリームに対して成功した**ungetwc**呼び出しでは、プッシュバックされたすべての文字が読み取りまたは破棄されるまで、ファイル位置インジケーターの値は指定されません。

これらの関数はスレッド セーフであり、実行時に重要情報をロックします。 ロックしないバージョンについては、「[_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
