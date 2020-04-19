---
title: rewind
ms.date: 11/04/2016
api_name:
- rewind
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
- rewind
helpviewer_keywords:
- rewind function
- repositioning file pointers
- file pointers [C++], repositioning
- file pointers [C++]
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
ms.openlocfilehash: 084a6f3d7e817498bffb510d865f4a32021e4ce8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949275"
---
# <a name="rewind"></a>rewind

ファイル ポインターをファイルの先頭に位置変更します。

## <a name="syntax"></a>構文

```C
void rewind(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="remarks"></a>Remarks

**Rewind**関数は、*ストリーム*に関連付けられたファイルポインターをファイルの先頭に再配置します。 **rewind** 関数の呼び出しは、次の関数の呼び出しと似ています。

**(void) fseek (** _stream_ **, 0L, SEEK_SET);**

ただし、 [fseek](fseek-fseeki64.md)とは異なり、**巻き戻し**はストリームのエラーインジケーターとファイルの終端インジケーターをクリアします。 また、 [fseek](fseek-fseeki64.md)とは異なり、 **rewind**はポインターが正常に移動されたかどうかを示す値を返しません。

キーボードバッファーをクリアするには、既定でキーボードに関連付けられているストリーム**stdin**で**rewind**を使用します。

Stream が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数はを返し、 **errno**は**EINVAL**に設定されます。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**rewind**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_rewind.c
/* This program first opens a file named
* crt_rewind.out for input and output and writes two
* integers to the file. Next, it uses rewind to
* reposition the file pointer to the beginning of
* the file and reads the data back in.
*/
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int data1, data2;

   data1 = 1;
   data2 = -37;

   fopen_s( &stream, "crt_rewind.out", "w+" );
   if( stream != NULL )
   {
      fprintf( stream, "%d %d", data1, data2 );
      printf( "The values written are: %d and %d\n", data1, data2 );
      rewind( stream );
      fscanf_s( stream, "%d %d", &data1, &data2 );
      printf( "The values read are: %d and %d\n", data1, data2 );
      fclose( stream );
   }
}
```

### <a name="output"></a>Output

```Output
The values written are: 1 and -37
The values read are: 1 and -37
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
