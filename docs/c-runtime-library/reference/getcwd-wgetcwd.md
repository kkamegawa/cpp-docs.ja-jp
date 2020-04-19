---
title: _getcwd、_wgetcwd
description: C ランタイムライブラリ関数 _getcwd、_wgetcwd 現在の作業ディレクトリを取得します。
ms.date: 09/24/2019
api_name:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: 27cfdc1eb59c2de788bbe5963a6fccffcb62cba0
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274627"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd、_wgetcwd

現在の作業ディレクトリを取得します。

## <a name="syntax"></a>構文

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>パラメーター

*格納*\
パスの格納場所。

*maxlen*\
文字数でのパスの最大長: **_getcwd**の場合は**char** 、 **_wgetcwd**の場合は**wchar_t**です。

## <a name="return-value"></a>戻り値

*バッファー*へのポインターを返します。 **Null**の戻り値はエラーを示し、 **errno**は**ENOMEM**に設定されます。これは、 *maxlen*バイトを割り当てるためのメモリが不足していることを示します ( **NULL**引数が*バッファー*として指定されている場合)。または**ERANGE**。パスが*maxlen*文字を超えていることを示します。 *Maxlen*が0以下の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、この関数は無効なパラメーターハンドラーを呼び出します。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>コメント

**_Getcwd**関数は、既定のドライブの現在の作業ディレクトリの完全なパスを取得し、*バッファー*に格納します。 Integer 引数*maxlen*は、パスの最大長を指定します。 パスの長さ (終端の null 文字を含む) が*maxlen*を超えると、エラーが発生します。 *Buffer*引数には**NULL**を指定できます。パスを格納するために、少なくともサイズが*maxlen* (必要な場合にのみ) のバッファーが**malloc**を使用して自動的に割り当てられます。 このバッファーは、後で**free**を呼び出して、 **_getcwd**の戻り値 (割り当てられたバッファーへのポインター) を渡すことによって解放できます。

**_getcwd**は、現在の作業ディレクトリのパスを表す文字列を返します。 現在の作業ディレクトリがルートの場合、文字列は円記号 (`\`) で終わります。 現在の作業ディレクトリがルート以外のディレクトリの場合、文字列は、円記号ではなく、ディレクトリの名前で終わります。

**_wgetcwd**は、 **_getcwd**のワイド文字バージョンです。 **_wgetcwd**の*バッファー*引数と戻り値はワイド文字列です。 それ以外では、 **_wgetcwd**と **_getcwd**は同じように動作します。

**_Debug**と **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_getcwd**と **_wgetcwd**の呼び出しは **_getcwd_dbg**および **_wgetcwd_dbg**の呼び出しに置き換えられ、メモリ割り当てをデバッグできるようになります。 詳細については、「 [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)\
[_chdir、_wchdir](chdir-wchdir.md)\
[_mkdir、_wmkdir](mkdir-wmkdir.md)\
[_rmdir、_wrmdir](rmdir-wrmdir.md)
