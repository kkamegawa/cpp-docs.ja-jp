---
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: f58c23050fe89f84f283c3784a7c0cee72637bf2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957539"
---
# <a name="tmpfile"></a>tmpfile

一時ファイルを作成します。 セキュリティが強化されたバージョンが提供されたため、この関数は非推奨とされました。「[tmpfile_s](tmpfile-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>戻り値

成功した場合、 **tmpfile**はストリームポインターを返します。 それ以外の場合は、 **NULL**ポインターを返します。

## <a name="remarks"></a>Remarks

**Tmpfile**関数は、一時ファイルを作成し、そのストリームへのポインターを返します。 一時ファイルはルート ディレクトリに作成されます。 ルート ディレクトリ以外のディレクトリに一時ファイルを作成するには、[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) または [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) を [fopen](fopen-wfopen.md) と共に使用します。

ファイルを開くことができない場合、 **tmpfile**は**NULL**ポインターを返します。 この一時ファイルは、ファイルが閉じられたとき、プログラムが正常に終了したとき、または **_rmtmp**が呼び出されたときに自動的に削除されます。これは、現在の作業ディレクトリが変更されていないことを前提としています。 一時ファイルは、 **w + b** (バイナリ読み取り/書き込み) モードで開かれます。

TMP_MAX を超える場合、エラーが発生することがあります (「STDIO」を参照してください)。H) **tmpfile**を使用してを呼び出します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

> [!NOTE]
> この例では、Windows Vista を管理者権限で実行する必要があります。

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
