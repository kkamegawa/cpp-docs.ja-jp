---
title: fputs、fputws
ms.date: 11/04/2016
api_name:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
ms.openlocfilehash: 7470901fda72e74caea12758bed4f23fcc087a33
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956911"
---
# <a name="fputs-fputws"></a>fputs、fputws

ストリームに文字列を書き込みます。

## <a name="syntax"></a>構文

```C
int fputs(
   const char *str,
   FILE *stream
);
int fputws(
   const wchar_t *str,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
出力する文字列。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

これらの関数は、正常に終了した場合に 0 以上の値を返します。 エラーが発生した場合、 **fputs**と**fputws**は**EOF**を返します。 *Str*または*stream*が null ポインターの場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、 **fputs**は**EOF**を返し、 **fputws**は**WEOF**を返します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

これらの各関数は、 *str*を現在の位置の出力*ストリーム*にコピーします。 **fputws**は、ワイド文字の引数*str*を、*ストリームがテキスト*モードとバイナリモードのどちらで開かれているかに応じて、マルチバイト文字列またはワイド文字列として*ストリーム*にコピーします。 どちらの関数も、終端の null 文字をコピーしません。

ストリームが ANSI モードで開かれている場合、2 つの関数の動作は同じになります。 **fputs**は、現在 UNICODE ストリームへの出力をサポートしていません。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputts**|**fputs**|**fputs**|**fputws**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fputs**|\<stdio.h>|
|**fputws**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール (**stdin**、 **stdout**、 **stderr**) に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fputs.c
// This program uses fputs to write
// a single line to the stdout stream.

#include <stdio.h>

int main( void )
{
   fputs( "Hello world from fputs.\n", stdout );
}
```

```Output
Hello world from fputs.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
