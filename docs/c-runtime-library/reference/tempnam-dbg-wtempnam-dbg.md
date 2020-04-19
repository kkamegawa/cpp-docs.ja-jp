---
title: _tempnam_dbg、_wtempnam_dbg
ms.date: 11/04/2016
api_name:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 73642730995ac5c0b47519fac64b30400d47767c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946246"
---
# <a name="_tempnam_dbg-_wtempnam_dbg"></a>_tempnam_dbg、_wtempnam_dbg

デバッグバージョンの**malloc**, **_malloc_dbg**を使用する、 [_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)の関数バージョン。

## <a name="syntax"></a>構文

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*エイリアス*<br/>
TMP 環境変数がない場合、または TMP が有効なディレクトリではない場合にファイル名で使用されるパス。

*prefix*<br/>
**_Tempnam**によって返される名前の前に付加される文字列。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
割り当て操作を要求したソースファイル名へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

各関数は、生成された名前へのポインター、またはエラーが発生した場合は**NULL**を返します。 TMP 環境変数で指定されている無効なディレクトリ名と*dir*パラメーターに無効なディレクトリ名が指定されていると、エラーが発生する可能性があります。

> [!NOTE]
> **無料** **_tempnam_dbg**と **_wtempnam_dbg**によって割り当てられたポインターに対して、(または**free_dbg**) を呼び出す必要があります。

## <a name="remarks"></a>Remarks

**_Tempnam_dbg**関数と **_wtempnam_dbg**関数は、 **_tempnam**および **_wtempnam**と同じですが、 **_debug**が定義されている場合、これらの関数は**malloc**および **_malloc_dbg**のデバッグバージョンを使用します。**NULL**が最初のパラメーターとして渡された場合は、メモリを割り当てます。 詳細については、「[_malloc_dbg](malloc-dbg.md)」をご覧ください。

多くの場合、これらの関数を明示的に呼び出す必要はありません。 代わりに、フラグ **_CRTDBG_MAP_ALLOC**を定義できます。 **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_tempnam**と **_wtempnam**の呼び出しはそれぞれ **_tempnam_dbg**と **_wtempnam_dbg**に再マップされ、 *blocktype*は **_NORMAL_BLOCK**に設定されます。 したがって、ヒープブロックを **_CLIENT_BLOCK**としてマークする場合を除き、これらの関数を明示的に呼び出す必要はありません。 詳細については、[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)に関する記事をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_tempnam_dbg**、 **_wtempnam_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
