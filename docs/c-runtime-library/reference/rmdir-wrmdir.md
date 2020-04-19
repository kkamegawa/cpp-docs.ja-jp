---
title: _rmdir、_wrmdir
ms.date: 11/04/2016
api_name:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: 396e620bfabe240638dc070ff87582b16287ff60
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949214"
---
# <a name="_rmdir-_wrmdir"></a>_rmdir、_wrmdir

ディレクトリを削除します。

## <a name="syntax"></a>構文

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>パラメーター

*dirname*<br/>
削除されるディレクトリのパス。

## <a name="return-value"></a>戻り値

ディレクトリが正常に削除された場合、これらの関数はそれぞれ 0 を返します。 戻り値-1 はエラーを示し、 **errno**は次のいずれかの値に設定されます。

|errno の値|条件|
|-|-|
| **ENOTEMPTY** | 指定されたパスがディレクトリではないか、ディレクトリが空でない、またはディレクトリが現在の作業ディレクトリかルート ディレクトリのいずれかです。 |
| **ENOENT** | パスが無効です。 |
| **EACCES** | プログラムに、ディレクトリに対して開いているハンドルがあります。 |

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

Dirname**関数は、** *dirname*によって指定されたディレクトリを削除します。 ディレクトリは空である必要があり、現在の作業ディレクトリまたはルート ディレクトリではないことが必要です。

**_wrmdir**のワイド文字バージョン**です。** **_wrmdir**への*dirname*引数は、ワイド文字列です。 **_wrmdir**と**rmdir**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

「[_mkdir](mkdir-wmkdir.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
