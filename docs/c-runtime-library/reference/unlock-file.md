---
title: _unlock_file
ms.date: 11/04/2016
api_name:
- _unlock_file
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
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: 2983408f066ea00c0b7ab111d9a6349700ecaece
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957476"
---
# <a name="_unlock_file"></a>_unlock_file

他のプロセスがアクセスできるようにファイルのロックを解除します。

## <a name="syntax"></a>構文

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>パラメーター

*file*<br/>
ファイル ハンドルです。

## <a name="remarks"></a>Remarks

**_Unlock_file**関数は、 *file*によって指定されたファイルのロックを解除します。 ファイルのロックを解除すると、他のプロセスがそのファイルにアクセスできるようになります。 以前に*ファイル*ポインターで**呼び出されていない限り、** この関数を呼び出すことはできません。 ロックされていないファイルで **_unlock_file**を呼び出すと、デッドロックが発生する可能性があります。 例については、「[_lock_file](lock-file.md)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
