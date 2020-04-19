---
title: setbuf
ms.date: 04/08/2019
api_name:
- setbuf
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
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: c6c78297b1818131dcfcb10f4f2eaadd752d8ef4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948277"
---
# <a name="setbuf"></a>setbuf

ストリーム バッファリングを制御します。 この関数は非推奨とされました。代わりに [setvbuf](setvbuf.md) をご使用ください。

## <a name="syntax"></a>構文

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

*バッファー*<br/>
ユーザー割り当てのバッファー。

## <a name="remarks"></a>Remarks

**Setbuf**関数は、*ストリーム*のバッファリングを制御します。 *ストリーム*引数は、読み取りまたは書き込みが行われていない開いているファイルを参照する必要があります。 *バッファー*引数が**NULL**の場合、ストリームはバッファーされません。 それ以外の場合、バッファーは長さ**BUFSIZ**の文字配列を指す必要があります。 **BUFSIZ**は、STDIO で定義されているバッファーサイズです。始め. 所定のストリームに対してシステムによって割り当てられた既定のバッファーではなく、ユーザーが指定したバッファーが I/O バッファー処理に使用されます。 **Stderr**ストリームは既定ではバッファリングされませんが、 **setbuf**を使用して、 **stderr**にバッファーを割り当てることができます。

**setbuf**は[setvbuf](setvbuf.md)に置き換えられました。これは、新しいコードの推奨されるルーチンです。 **Setvbuf**とは異なり、 **setbuf**にはエラーを報告する方法がありません。 また、 **setvbuf**では、バッファリングモードとバッファーサイズの両方を制御できます。 **setbuf**は、既存のコードとの互換性を維持するために存在します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
