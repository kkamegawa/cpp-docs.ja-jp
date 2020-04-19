---
title: _unlink、_wunlink
ms.date: 11/04/2016
api_name:
- _unlink
- _wunlink
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: 878a1b4aa009bc8528dfac1908ed26c7e3b269ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957392"
---
# <a name="_unlink-_wunlink"></a>_unlink、_wunlink

ファイルを削除します。

## <a name="syntax"></a>構文

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
削除するファイルの名前。

## <a name="return-value"></a>戻り値

正常に終了した場合、これらの各関数は 0 を返します。 それ以外の場合、この関数は-1 を返し、 **errno**を**EACCES**に設定します。これは、パスが読み取り専用のファイルまたはディレクトリを指定しているか、ファイルまたはパスが見つからないことを示す**ENOENT**に設定されていることを意味します。

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Unlink**関数は、 *filename*によって指定されたファイルを削除します。 **_wunlink**のワイド文字バージョン**です。** **_wunlink**の*filename*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**tunlink (_c)**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_unlink**|\<io.h> および \<stdio.h>|
|**_wunlink**|\<io.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="code-example"></a>コード例

このプログラムは、_unlink を使用して CRT_UNLINK.TXT を削除します。

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crt_unlinktxt"></a>入力: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>出力例

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove、_wremove](remove-wremove.md)<br/>
