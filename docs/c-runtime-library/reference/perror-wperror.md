---
title: perror、_wperror
ms.date: 11/04/2016
api_name:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 755b638f320fcc583faecfe6aa82269e4e1b3d8f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951028"
---
# <a name="perror-_wperror"></a>perror、_wperror

エラー メッセージを印刷します。

## <a name="syntax"></a>構文

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>パラメーター

*message*<br/>
印刷する文字列メッセージ。

## <a name="remarks"></a>Remarks

エラーメッセージは、 **stderr**関数によって stderr に出力**されます**。 **_wperror**のワイド文字バージョン**です。** **_wperror**への*メッセージ*引数は、ワイド文字列です。 それ以外**では**、 **_wperror**との動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*メッセージ*は最初に出力され、その後にコロン、次にエラーを生成した最後のライブラリの呼び出しのシステムエラーメッセージ、最後に改行文字が出力されます。 *Message*が null ポインターまたは null 文字列へのポインターである場合、システムエラーメッセージのみ**が出力さ**れます。

エラー番号は、変数 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (ERRNO.H で定義) に格納されます。 システム エラー メッセージは、エラー番号順のメッセージの配列である変数 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) を使用してアクセスできます。 **_sys_errlist**のインデックスとして**errno**値を使用して、適切なエラーメッセージ**を出力し**ます。 変数[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)の値は、 **_sys_errlist**配列内の要素の最大数として定義されます。

正確な結果を得るには、ライブラリルーチンからエラーが返された直後に、エラーメッセージ**を呼び出します**。 それ以外の場合、後続の呼び出しで**errno**値が上書きされる可能性があります。

Windows オペレーティングシステムでは **、errno に列挙値が**表示されます。H は使用されていません。 これらの値は、UNIX オペレーティング システムで使用するために予約されたものです。 Windows オペレーティングシステムで使用される**errno**値の一覧については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 」を参照してください。 は、これらのプラットフォームで使用されていない**errno**値に対して空の文字列**を出力し**ます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**perror**|\<stdio.h> または \<stdlib.h>|
|**_wperror**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
