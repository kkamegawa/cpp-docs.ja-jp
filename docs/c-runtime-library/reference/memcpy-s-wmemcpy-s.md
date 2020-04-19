---
title: memcpy_s、wmemcpy_s
ms.date: 11/04/2016
api_name:
- memcpy_s
- wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 8078590df6950201ef81356ba6c28173e80572ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952800"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s、wmemcpy_s

バッファー間でバイトをコピーします。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [memcpy、wmemcpy](memcpy-wmemcpy.md) です。

## <a name="syntax"></a>構文

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>パラメーター

*dest*<br/>
コピー先のバッファー。

*destSize*<br/>
コピー先バッファーのサイズ。memcpy_s の場合はバイト単位、wmemcpy_s の場合はワイド文字列 (wchar_t) 単位です。

*src*<br/>
コピー元のバッファー。

*count*<br/>
コピーする文字数。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|*dest*|*destSize*|*src*|*count*|戻り値|*Dest*の内容|
|------------|----------------|-----------|---|------------------|------------------------|
|任意|任意|任意|0|0|変更されない|
|**NULL**|任意|任意|0 以外|**EINVAL**|変更されない|
|任意|任意|**NULL**|0 以外|**EINVAL**|*dest*はゼロになります|
|任意|< *数*|任意|0 以外|**ERANGE**|*dest*はゼロになります|

## <a name="remarks"></a>Remarks

**memcpy_s**は、 *src*から*dest*に*カウント*バイトをコピーします。**wmemcpy_s**は、*数*のワイド文字 (2 バイト) をコピーします。 コピー元とコピー先が重複する場合、 **memcpy_s**の動作は未定義です。 重複する領域を処理するには、 **memmove_s**を使用します。

これらの関数では、パラメーターの検証が行われます。 *Count*が0以外で、 *dest*または*src*が null ポインターであるか、または*destsize*が*count*より小さい場合、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**EINVAL**または**ERANGE**を返し、 **errno**を戻り値に設定します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> または \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>関連項目

[バッファー操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
