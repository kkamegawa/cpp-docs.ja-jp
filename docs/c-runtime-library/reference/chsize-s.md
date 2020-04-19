---
title: _chsize_s
ms.date: 11/04/2016
api_name:
- _chsize_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 7250f0b570ae9a4b2478bad09ee7b0044068d972
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939175"
---
# <a name="_chsize_s"></a>_chsize_s

ファイル サイズを変更します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_chsize](chsize.md) です。

## <a name="syntax"></a>構文

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルを参照するファイル記述子。

*size*<br/>
バイト単位のファイルの新しい長さ。

## <a name="return-value"></a>戻り値

ファイルサイズが正常に変更された場合、 **_chsize_s**は値0を返します。 0以外の戻り値は、エラーを示します。指定したファイルがアクセスに対してロックされている場合、戻り値は**EACCES** 、指定されたファイルが読み取り専用**であるか**、または記述子が無効である場合は ENOSPC、デバイス **に領域が残っていない場合はになります。** Size が0未満の場合は EINVAL。 **errno**が同じ値に設定されています。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Chsize_s**関数は、 *fd*に関連付けられているファイルを*size*によって指定された長さに拡張または切り捨てます。 ファイルは、書き込みを許可するモードで開かれている必要があります。 ファイルが拡張される場合は、null 文字 ('\0') が追加されます。 ファイルが切り捨てられる場合、短くなったファイルの末尾からファイルの元の長さまでのすべてのデータは失われます。

**_chsize_s**は、ファイルサイズとして64ビット整数を受け取るため、4 GB を超えるファイルサイズを処理できます。 **_chsize**は、32ビットのファイルサイズに制限されています。

この関数は、パラメーターを検証します。 *Fd*が有効なファイル記述子でないか、またはサイズが0未満の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
