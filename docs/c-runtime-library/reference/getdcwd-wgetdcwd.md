---
title: _getdcwd、_wgetdcwd
ms.date: 11/04/2016
api_name:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 3b67e04e914baf85545fcde63cf27c86bc15fac1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956025"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd、_wgetdcwd

指定されたドライブの現在の作業ディレクトリの完全なパスを取得します。

## <a name="syntax"></a>構文

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>パラメーター

*駆動*<br/>
ドライブを指定する負でない整数 (0 = 既定のドライブ、1 = A、2 = B など)。

指定されたドライブが使用できない場合、またはドライブの種類 (リムーバブルドライブ、固定ドライブ、CD-ROM ドライブ、RAM ディスクドライブ、ネットワークドライブなど) を特定できない場合は、無効なパラメーターハンドラーが呼び出されます。 詳細については、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」を参照してください。

*バッファー*<br/>
パスの格納場所または **NULL**。

**NULL**が指定されている場合、この関数は**malloc**を使用して少なくとも*maxlen*のサイズのバッファーを割り当てます。 **_getdcwd**の戻り値は、割り当てられたバッファーへのポインターです。 バッファーは、 **free**を呼び出してポインターを渡すことによって解放できます。

*maxlen*<br/>
パスの最大長を文字数で指定する0以外の正の整数。 **_getdcwd**の場合は**char** 、 **_wgetdcwd**の場合は**wchar_t**です。

*Maxlen*が0以下の場合は、無効なパラメーターハンドラーが呼び出されます。 詳細については、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」を参照してください。

## <a name="return-value"></a>戻り値

指定されたドライブの現在の作業ディレクトリの完全パスを表す文字列へのポインター、またはエラーを示す**NULL**。

*Buffer*が**NULL**として指定されていて、 *maxlen*文字を割り当てるためのメモリが不足している場合は、エラーが発生し、 **errno**は**ENOMEM**に設定されます。 終端の null 文字を含むパスの長さが*maxlen*を超えると、エラーが発生し、 **errno**は**ERANGE**に設定されます。 これらのエラー コードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Getdcwd**関数は、指定されたドライブ上の現在の作業ディレクトリの完全なパスを取得し、*バッファー*に格納します。 現在の作業ディレクトリがルートに設定されている場合、文字列は円記号 (\\) で終わります。 現在の作業ディレクトリがルート以外のディレクトリに設定されている場合、文字列は、円記号ではなく、ディレクトリの名前で終わります。

**_wgetdcwd**は、 **_getdcwd**のワイド文字バージョンであり、その*バッファー*パラメーターと戻り値はワイド文字列です。 それ以外の場合、 **_wgetdcwd**と **_getdcwd**は同じように動作します。

この関数は、スレッドセーフではない **GetFullPathName**に依存しますが、スレッドセーフです。 ただし、マルチスレッド アプリケーションでこの関数と [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)を両方とも呼び出した場合、スレッド セーフを侵害する可能性があります。

この関数のバージョン**が、スレッド**セーフではなく、他のスレッドによる干渉から保護されていない点を除いて、この関数と同じように動作します。 詳細については、「 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)」を参照してください。

**_Debug**と **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_getdcwd**と **_wgetdcwd**の呼び出しは **_getdcwd_dbg**と **_wgetdcwd_dbg**の呼び出しに置き換えられるため、メモリの割り当てをデバッグできます。 詳しくは[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[_getdrive](getdrive.md)の例をご覧ください。

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
