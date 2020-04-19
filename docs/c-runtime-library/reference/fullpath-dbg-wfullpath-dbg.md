---
title: _fullpath_dbg、_wfullpath_dbg
ms.date: 11/04/2016
api_name:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
ms.openlocfilehash: 9271e26bcf4a78ff8d2e4fcf108f1e483c22c1d7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956310"
---
# <a name="_fullpath_dbg-_wfullpath_dbg"></a>_fullpath_dbg、_wfullpath_dbg

[_Wfullpath](fullpath-wfullpath.md)のバージョン。 **malloc**のデバッグバージョンを使用してメモリを割り当てます。

## <a name="syntax"></a>構文

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*absPath*<br/>
絶対パス名または完全パス名を格納しているバッファーへのポインター、または**NULL**。

*relPath*<br/>
相対パス名。

*maxLength*<br/>
絶対パス名バッファー (*Abspath*) の最大長。 この長さは、 **_wfullpath**の場合はバイト単位**ですが、** の場合はワイド文字 (**wchar_t**) になります。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

各関数は、絶対パス名 (*Abspath*) を格納しているバッファーへのポインターを返します。 エラーが発生した場合 (たとえば、 *relPath*で渡された値に有効でないドライブ文字が含まれている場合や見つからない場合、または作成された絶対パス名 (*abspath*) の長さが*maxLength*よりも大きい場合)、関数はを返します **。NULL**。

## <a name="remarks"></a>Remarks

**_Fullpath_dbg**関数と **_wfullpath_dbg**関数は、および **_wfullpath**と同じですが、 **_debug**が定義されている場合、これらの関数は**malloc**, **_malloc_dbg**, のデバッグ**バージョンを使用**する点が異なります。**NULL**が最初のパラメーターとして渡された場合にメモリを割り当てる場合は。 **_Malloc_dbg**のデバッグ機能の詳細については、 [_malloc_dbg](malloc-dbg.md)を参照してください。

多くの場合、これらの関数を明示的に呼び出す必要はありません。 代わりに、 **_CRTDBG_MAP_ALLOC**フラグを定義できます。 **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_wfullpath**への呼び出しはそれぞれ **_fullpath_dbg**と **_Wfullpath_dbg** **に再**マップされ、 *blocktype*は **_NORMAL_BLOCK**に設定されます。 したがって、ヒープブロックを **_CLIENT_BLOCK**としてマークする場合を除き、これらの関数を明示的に呼び出す必要はありません。 詳細については、[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)に関する記事をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
