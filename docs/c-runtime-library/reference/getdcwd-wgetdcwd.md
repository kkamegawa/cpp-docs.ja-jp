---
title: _getdcwd、_wgetdcwd
ms.date: 11/04/2016
apiname:
- _getdcwd
- _wgetdcwd
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 464a254775d9a1d2488247d6dafb4b85cd763f10
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702935"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd、_wgetdcwd

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

*ドライブ*<br/>
ドライブを指定する負でない整数 (0 = 既定のドライブ、1 = A、2 = B など)。

指定したドライブが使用できない場合、またはドライブの種類 (たとえば、リムーバブル、固定、CD-ROM、RAM、ディスクまたはネットワーク ドライブ) 決定できない無効なパラメーター ハンドラーが呼び出されます。 詳細については、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」を参照してください。

*バッファー*<br/>
パスの格納場所または **NULL**。

場合**NULL**を指定すると、この関数は、少なくとものバッファーを割り当てます*maxlen*を使用してサイズ**malloc**、および戻り値の **_getdcwd**、割り当てられたバッファーへのポインターです。 呼び出すことによって、バッファーを解放できる**無料**ポインターに渡すとします。

*maxlen*<br/>
文字数で、パスの最大長を指定する 0 以外の場合正の整数: **char**の **_getdcwd**と**wchar_t**の **_wgetdcwd**.

場合*maxlen*以下が 0 の場合、無効なパラメーター ハンドラーが呼び出されます。 詳細については、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」を参照してください。

## <a name="return-value"></a>戻り値

指定したドライブ上の現在の作業ディレクトリの完全なパスを表す文字列へのポインターまたは**NULL**エラーを示します。

場合*バッファー*として指定されて**NULL**が不足しているメモリを割り当てることがあると*maxlen*文字、エラーが発生し、 **errno**は設定**ENOMEM**します。 終端の null 文字を含むパスの長さを超えるかどうか*maxlen*、エラーが発生して**errno**に設定されている**ERANGE**します。 これらのエラー コードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Getdcwd**関数は、指定したドライブ上の現在の作業ディレクトリの完全なパスを取得しに格納*バッファー*します。 現在の作業ディレクトリがルートに設定されている場合、文字列は円記号 (\\) で終わります。 現在の作業ディレクトリがルート以外のディレクトリに設定されている場合、文字列は、円記号ではなく、ディレクトリの名前で終わります。

**_wgetdcwd**のワイド文字バージョンは、 **_getdcwd**、およびその*バッファー*パラメーターと戻り値はワイド文字の文字列。 それ以外の場合、 **_wgetdcwd**と **_getdcwd**動作は同じです。

この関数は、スレッドセーフではない **GetFullPathName**に依存しますが、スレッドセーフです。 マルチ スレッド アプリケーションは、この両方の関数を呼び出す場合、スレッド セーフを侵害するただし、および[GetFullPathNameA](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)します。

この関数のバージョン、 **_nolock**サフィックスの動作と同じこの関数はスレッド セーフではなく、他のスレッドによる干渉から保護されない点が異なります。 詳細については、「 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)」を参照してください。

ときに **_DEBUG**と **_CRTDBG_MAP_ALLOC**への呼び出しで定義されている **_getdcwd**と **_wgetdcwd** への呼び出しによって置き換えられます **_getdcwd_dbg**と **_wgetdcwd_dbg**メモリ割り当てをデバッグできるようにします。 詳しくは[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)をご覧ください。

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
