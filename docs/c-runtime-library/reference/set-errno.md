---
title: _set_errno
ms.date: 11/04/2016
api_name:
- _set_errno
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_errno
- _set_errno
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
ms.openlocfilehash: 09800276886ecf1c2fdd2ffee63ddcb8cc57f61e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948606"
---
# <a name="_set_errno"></a>_set_errno

**Errno**グローバル変数の値を設定します。

## <a name="syntax"></a>構文

```C
errno_t _set_errno( int error_value );
```

### <a name="parameters"></a>パラメーター

*error_value*<br/>
**Errno**の新しい値。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。

## <a name="remarks"></a>Remarks

使用できる値は Errno.h で定義します。 「[errno Constants](../../c-runtime-library/errno-constants.md)」(errno 定数) もご覧ください。

## <a name="example"></a>例

```C
// crt_set_errno.c
#include <stdio.h>
#include <errno.h>

int main()
{
   _set_errno( EILSEQ );
   perror( "Oops" );
}
```

```Output
Oops: Illegal byte sequence
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_set_errno**|\<stdlib.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_get_errno](get-errno.md)<br/>
[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
