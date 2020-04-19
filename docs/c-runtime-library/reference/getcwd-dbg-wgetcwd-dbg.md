---
title: _getcwd_dbg、_wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: 3eb318b9b2faa8716abdd26eafa926c8072b5614
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955279"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg、_wgetcwd_dbg

[_getcwd、_wgetcwd](getcwd-wgetcwd.md) 関数のデバッグ バージョン (デバッグ中のみ使用可能)。

## <a name="syntax"></a>構文

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
パスの格納場所。

*maxlen*<br/>
文字数でのパスの最大長: **_getcwd_dbg**の場合は**char** 、 **_wgetcwd_dbg**の場合は**wchar_t**です。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

*バッファー*へのポインターを返します。 **Null**の戻り値はエラーを示し、 **errno**は**ENOMEM**に設定されます。これは、 *maxlen*バイトを割り当てるためのメモリが不足していることを示します ( **NULL**引数が*バッファー*として指定されている場合)。または**ERANGE**。パスが*maxlen*文字を超えていることを示します。

詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_Getcwd_dbg**関数と **_wgetcwd_dbg**関数は **_getcwd**および **_wgetcwd**と同じですが、 **_debug**が定義されている場合、これらの関数は**malloc**と **_malloc_dbg**のデバッグバージョンを使用する点が異なります。**NULL**が最初のパラメーターとして渡された場合は、メモリを割り当てます。 詳細については、「[_malloc_dbg](malloc-dbg.md)」をご覧ください。

多くの場合、これらの関数を明示的に呼び出す必要はありません。 代わりに、 **_CRTDBG_MAP_ALLOC**フラグを定義できます。 **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_getcwd**と **_wgetcwd**の呼び出しはそれぞれ **_getcwd_dbg**と **_wgetcwd_dbg**に再マップされ、 *blocktype*は **_NORMAL_BLOCK**に設定されます。 したがって、ヒープブロックを **_CLIENT_BLOCK**としてマークする場合を除き、これらの関数を明示的に呼び出す必要はありません。 詳細については、[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)に関する記事をご覧ください。

## <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
