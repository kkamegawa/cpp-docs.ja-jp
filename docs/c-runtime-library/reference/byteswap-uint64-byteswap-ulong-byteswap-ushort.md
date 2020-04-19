---
title: _byteswap_uint64、_byteswap_ulong、_byteswap_ushort
ms.date: 11/04/2016
api_name:
- _byteswap_uint64
- _byteswap_ulong
- _byteswap_ushort
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- byteswap_ulong
- _byteswap_ulong
- byteswap_uint64
- _byteswap_ushort
- _byteswap_uint64
- byteswap_ushort
helpviewer_keywords:
- _byteswap_uint64 function
- byteswap_uint64 function
- swapping bytes
- byte swapping
- byteswap_ushort function
- _byteswap_ushort function
- bytes, swapping
- byteswap_ulong function
- _byteswap_ulong function
ms.assetid: 83bda211-f02f-4cf0-8a78-d6de1f175970
ms.openlocfilehash: 46ebc82919327ef5d51b760ae1aae15425910b4c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939427"
---
# <a name="_byteswap_uint64-_byteswap_ulong-_byteswap_ushort"></a>_byteswap_uint64、_byteswap_ulong、_byteswap_ushort

整数のバイトの順序を反転します。

## <a name="syntax"></a>構文

```C
unsigned short _byteswap_ushort ( unsigned short val );
unsigned long _byteswap_ulong ( unsigned long val );
unsigned __int64 _byteswap_uint64 ( unsigned __int64 val );
```

### <a name="parameters"></a>パラメーター

*val*<br/>
バイト順を反転する整数。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_byteswap_ushort**|\<stdlib.h>|
|**_byteswap_ulong**|\<stdlib.h>|
|**_byteswap_uint64**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_byteswap.c
#include <stdlib.h>

int main()
{
   unsigned __int64 u64 = 0x0102030405060708;
   unsigned long ul = 0x01020304;

   printf("byteswap of %I64x = %I64x\n", u64, _byteswap_uint64(u64));
   printf("byteswap of %Ix = %Ix", ul, _byteswap_ulong(ul));
}
```

```Output
byteswap of 102030405060708 = 807060504030201
byteswap of 1020304 = 4030201
```

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../../c-runtime-library/run-time-routines-by-category.md)<br/>
