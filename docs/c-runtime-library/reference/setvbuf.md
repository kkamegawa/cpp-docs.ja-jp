---
title: setvbuf
ms.date: 11/04/2016
api_name:
- setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 38b6474f550107a8edd941c7112ba98891ab3c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948179"
---
# <a name="setvbuf"></a>setvbuf

ストリームのバッファリングとバッファー サイズを制御します。

## <a name="syntax"></a>構文

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

*バッファー*<br/>
ユーザー割り当てのバッファー。

*モード*<br/>
バッファリングのモード。

*size*<br/>
バイト単位のバッファー サイズ。 許容範囲:2 < = *size* < = INT_MAX (2147483647)。 内部的には、 *size*に指定された値は、最も近い2の倍数に丸められます。

## <a name="return-value"></a>戻り値

処理が正常に終了した場合は 0 を返します。

*Stream*が**NULL**の場合、または*モード*または*サイズ*が有効な変更の範囲内にない場合は、「パラメーターの[検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は -1 を返し、**errno** を **EINVAL** に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Setvbuf**関数を使用すると、プログラムは*ストリーム*のバッファリングとバッファーサイズの両方を制御できます。 *ストリーム*は、開いた後に i/o 操作を実行していない開いているファイルを参照する必要があります。 *Buffer*が指す配列は、 **NULL**でない限り、バッファーとして使用されます。この場合、 **setvbuf**は、自動的に割り当てられ\*た長さ*サイズ*/2 2 バイトのバッファーを使用します。

モードは **_IOFBF**、 **_IOLBF**、または **_IONBF**である必要があります。 *Mode*が **_IOFBF**または **_IOLBF**の場合、*サイズ*はバッファーのサイズとして使用されます。 *Mode*が **_IONBF**の場合、ストリームはバッファーされません。*サイズ*と*バッファー*は無視されます。 *モード*とその意味の値は次のとおりです。

|*モード*値|説明|
|-|-|
| **_IOFBF** | フルバッファリングつまり、バッファーがバッファーとして使用さ*れ、* *サイズ*がバッファーのサイズとして使用されます。 *Buffer*が**NULL**の場合、自動的に割り当てられたバッファー*サイズ*のバイト長が使用されます。 |
| **_IOLBF** | 一部のシステムでは、行バッファリングします。 ただし、Win32 の場合、動作は **_IOFBF**フルバッファリングと同じです。 |
| **_IONBF** | *バッファーまたは* *サイズ*に関係なく、バッファーは使用されません。 |

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
