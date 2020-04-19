---
title: tmpfile_s
ms.date: 11/04/2016
api_name:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 64107f26fa651739f4d5bdd7521b15d9d458df65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946055"
---
# <a name="tmpfile_s"></a>tmpfile_s

一時ファイルを作成します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [tmpfile](tmpfile.md) です。

## <a name="syntax"></a>構文

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>パラメーター

*pFilePtr*<br/>
ストリームに生成されたポインターのアドレスを格納するポインターのアドレスです。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|*pFilePtr*|**戻り値**|**内容**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|変更されない|

上記のパラメーターの検証エラーが発生した場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**einval**に設定され、戻り値は**einval**になります。

## <a name="remarks"></a>Remarks

**Tmpfile_s**関数は、一時ファイルを作成し、そのストリームへのポインターを*pfileptr*引数に格納します。 一時ファイルはルート ディレクトリに作成されます。 ルート ディレクトリ以外のディレクトリに一時ファイルを作成するには、[tmpnam_s](tmpnam-s-wtmpnam-s.md) または [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) を [fopen](fopen-wfopen.md) と共に使用します。

ファイルを開くことができない場合、 **tmpfile_s**は*pfileptr*パラメーターに**NULL**を書き込みます。 この一時ファイルは、ファイルが閉じられたとき、プログラムが正常に終了したとき、または **_rmtmp**が呼び出されたときに自動的に削除されます。これは、現在の作業ディレクトリが変更されていないことを前提としています。 一時ファイルは、 **w + b** (バイナリ読み取り/書き込み) モードで開かれます。

**TMP_MAX_S**を超える場合、エラーが発生することがあります (「STDIO」を参照してください)。H) **tmpfile_s**を使用してを呼び出します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

> [!NOTE]
> この例では、Windows で実行するために管理者特権が必要になる場合があります。

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
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
