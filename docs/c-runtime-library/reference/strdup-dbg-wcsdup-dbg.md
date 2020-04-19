---
title: _strdup_dbg、_wcsdup_dbg
ms.date: 11/04/2016
api_name:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
ms.openlocfilehash: 9f7d4fd8781269ee37f7515fdcab72e5195fdf00
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958200"
---
# <a name="_strdup_dbg-_wcsdup_dbg"></a>_strdup_dbg、_wcsdup_dbg

**Malloc**のデバッグバージョンを使用する[_strdup と _wcsdup](strdup-wcsdup-mbsdup.md)のバージョン。

## <a name="syntax"></a>構文

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*strSource*<br/>
NULL で終わる元の文字列。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
割り当て操作を要求したソースファイル名へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

これらの各関数は、コピーされた文字列の格納場所へのポインターを返すか、ストレージを割り当てることができない場合は**NULL**を返します。

## <a name="remarks"></a>Remarks

**_Strdup_dbg**関数と **_wcsdup_dbg**関数は **_strdup**および **_wcsdup**と同じですが、 **_debug**が定義されている場合、これらの関数は**malloc**, **_malloc_dbg**のデバッグバージョンを使用してを割り当てます。複製された文字列のメモリ。 **_Malloc_dbg**のデバッグ機能の詳細については、 [_malloc_dbg](malloc-dbg.md)を参照してください。

多くの場合、これらの関数を明示的に呼び出す必要はありません。 代わりに、フラグ **_CRTDBG_MAP_ALLOC**を定義できます。 **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_strdup**と **_wcsdup**の呼び出しはそれぞれ **_strdup_dbg**と **_wcsdup_dbg**に再マップされ、 *blocktype*は **_NORMAL_BLOCK**に設定されます。 したがって、ヒープブロックを **_CLIENT_BLOCK**としてマークする場合を除き、これらの関数を明示的に呼び出す必要はありません。 ブロック型の詳細については、[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)に関する記事をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strdup_dbg**、 **_wcsdup_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのデバッグ バージョン。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup、_wcsdup、_mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
