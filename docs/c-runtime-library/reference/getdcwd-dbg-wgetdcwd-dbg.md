---
title: _getdcwd_dbg、_wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 8eb22f3716102c1b63b483e493eb44ac99228004
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955229"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg、_wgetdcwd_dbg

[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md) 関数のデバッグ バージョン (デバッグ中のみ使用可能)。

## <a name="syntax"></a>構文

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*駆動*<br/>
ディスク ドライブの名前。

*バッファー*<br/>
パスの格納場所。

*maxlen*<br/>
文字数でのパスの最大長: **_getdcwd_dbg**の場合は**char** 、 **_wgetdcwd_dbg**の場合は**wchar_t**です。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

*バッファー*へのポインターを返します。 **Null**の戻り値はエラーを示し、 **errno**は**ENOMEM**に設定されます。これは、 *maxlen*バイトを割り当てるためのメモリが不足していることを示します ( **NULL**引数が*バッファー*として指定されている場合)。または**ERANGE**。パスが*maxlen*文字を超えていることを示します。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_Getdcwd_dbg**関数と **_wgetdcwd_dbg**関数は **_getdcwd**および **_wgetdcwd**と同じですが、 **_debug**が定義されている場合、これらの関数は**malloc**と **_malloc_dbg**のデバッグバージョンを使用する点が異なります。**NULL**が*バッファー*パラメーターとして渡された場合にメモリを割り当てます。 詳細については、「[_malloc_dbg](malloc-dbg.md)」をご覧ください。

多くの場合、これらの関数を明示的に呼び出す必要はありません。 代わりに、 **_CRTDBG_MAP_ALLOC**フラグを定義できます。 **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_getdcwd**と **_wgetdcwd**の呼び出しはそれぞれ **_getdcwd_dbg**と **_wgetdcwd_dbg**に再マップされ、 *blocktype*は **_NORMAL_BLOCK**に設定されます。 したがって、ヒープブロックを **_CLIENT_BLOCK**としてマークする場合を除き、これらの関数を明示的に呼び出す必要はありません。 詳細については、[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)に関する記事をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
