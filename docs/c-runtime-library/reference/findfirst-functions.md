---
title: _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
ms.date: 11/04/2016
apiname:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: 47a1d7301b59a942a1af860f310e1f1f9da12ec7
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703143"
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64

指定されたファイルに一致するファイル名の最初のインスタンスに関する情報を提供、 *filespec*引数。

## <a name="syntax"></a>構文

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>パラメーター

*filespec*<br/>
ターゲット ファイルの指定 (ワイルドカード文字を含めることができます)。

*fileinfo*<br/>
ファイル情報バッファー。

## <a name="return-value"></a>戻り値

成功した場合、 **_findfirst**ファイルまたは一致するファイルのグループを識別する一意の検索のハンドルを返します、 *filespec*仕様で、後続の呼び出しで使用できる[_findnext](findnext-functions.md)または[_findclose](findclose.md)します。 それ以外の場合、 **_findfirst** -1 を返し**errno**値は次のいずれかにします。

| errno の値 | 条件 |
|-|-|
| **EINVAL** | 無効なパラメーター: *filespec*または*fileinfo*が**NULL**します。 または、オペレーティング システムが予期しないエラーを返しました。 |
| **ENOENT** | 一致しないファイルの指定。 |
| **ENOMEM** | メモリ不足です。 |
| **EINVAL** | 無効なファイル名の指定または指定されたファイル名が超えて**MAX_PATH**します。 |

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーター ハンドラーを呼び出します。

## <a name="remarks"></a>Remarks

呼び出す必要があります[_findclose](findclose.md)いずれかで完了した後、 **_findfirst**または[_findnext](findnext-functions.md)関数 (または任意のバリアント)。 呼び出すと、アプリケーション内でこれらの関数が使用しているリソースが解放されます。

これらの関数がのバリエーション、 **w**プレフィックスはワイド文字バージョンは、それ以外の場合、対応する 1 バイト関数と同じです。

これらの関数のバリエーションは、32 ビットや 64 ビットの時刻型と、32 ビットや 64 ビットのファイル サイズをサポートします。 最初の数値のサフィックス (**32**または**64**) は、時刻型のサイズを示す 2 つ目のサフィックスは**i32**または**i64**を示し、かどうか、ファイルのサイズは 32 ビットまたは 64 ビット整数として表されます。 32 ビットと 64 ビットの時刻型とファイル サイズをサポートするバージョンについては、次の表を参照してください。 **I32**または**i64**のでこれは時の型のサイズと同じ場合、サフィックスは省略されます **_findfirst64**も 64 ビット ファイルの長さをサポートし、 **_findfirst32** 32 ビットのファイル長のみをサポートします。

これらの関数を使用して、さまざまな形式の **_finddata_t**用の構造、 *fileinfo*パラメーター。 構造体の詳細については、「[ファイル名検索関数](../../c-runtime-library/filename-search-functions.md)」を参照してください。

64 ビットの時刻型を使用するバリエーションでは、3000 年 12 月 31 日 23:59:59 (UTC) までのファイルの作成日を表現できます。 32 ビットの時刻型を使用するバリエーションでは、2038 年 1 月 18 日 23:59:59 (UTC) までの日付のみを表現できます。 これらの関数の日付範囲の下限は、いずれも 1970 年 1 月 1 日の午前 0 時です。

時間のサイズを明示的に指定するバージョンを使用する特定の理由がない限り **_findfirst**または **_wfindfirst** 3 GB を超えるファイル サイズをサポートする必要がある場合、または、 **_findfirsti64**または **_wfindfirsti64**します。 これらの関数はすべて 64 ビットの時刻型です。 以前のバージョンでは、これらの関数は 32 ビットの時刻型を使用していました。 アプリケーションの互換性に影響する変更の場合は、定義 **_USE_32BIT_TIME_T**古い動作に戻す。 場合 **_USE_32BIT_TIME_T**が定義されている **_findfirst**、 **_finfirsti64**、およびそれに対応する Unicode バージョンが 32 ビットの時刻を使用します。

### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>_findfirst の時刻型とファイル長型のバリエーション

|関数|**_USE_32BIT_TIME_T**定義されているか。|時刻型|ファイル長型|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**、 **_wfindfirst**|未定義|64 ビット|32 ビット|
|**_findfirst**、 **_wfindfirst**|定義済み|32 ビット|32 ビット|
|**_findfirst32**, **_wfindfirst32**|マクロ定義の影響を受けない|32 ビット|32 ビット|
|**_findfirst64**、 **_wfindfirst64**|マクロ定義の影響を受けない|64 ビット|64 ビット|
|**_findfirsti64**、 **_wfindfirsti64**|未定義|64 ビット|64 ビット|
|**_findfirsti64**、 **_wfindfirsti64**|定義済み|32 ビット|64 ビット|
|**_findfirst32i64**、 **_wfindfirst32i64**|マクロ定義の影響を受けない|32 ビット|64 ビット|
|**_findfirst64i32**, **_wfindfirst64i32**|マクロ定義の影響を受けない|64 ビット|32 ビット|

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> または \<wchar.h>|
|**_wfindfirst32**|\<io.h> または \<wchar.h>|
|**_wfindfirst64**|\<io.h> または \<wchar.h>|
|**_wfindfirsti64**|\<io.h> または \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> または \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[システム コール](../../c-runtime-library/system-calls.md)<br/>
[ファイル名検索関数](../../c-runtime-library/filename-search-functions.md)<br/>
