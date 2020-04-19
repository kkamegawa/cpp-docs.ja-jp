---
title: _memicmp、_memicmp_l
ms.date: 11/04/2016
api_name:
- _memicmp_l
- _memicmp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
ms.openlocfilehash: a463b9c79a76879311bb811b38e4aabcfd6e7226
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951835"
---
# <a name="_memicmp-_memicmp_l"></a>_memicmp、_memicmp_l

2 つのバッファーの文字を比較します (大文字と小文字を区別しない)。

## <a name="syntax"></a>構文

```C
int _memicmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int _memicmp_l(
   const void *buffer1,
   const void *buffer2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*buffer1*<br/>
最初のバッファー。

*buffer2*<br/>
2 番目のバッファー。

*count*<br/>
文字数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

戻り値は、バッファー間の関係を示しています。

|戻り値|buf1 と buf2 の最初の count バイトの関係|
|------------------|--------------------------------------------------------|
|< 0|*buffer1*未満*buffer2*。|
|0|*buffer1*は*buffer2*と同じです。|
|> 0|*buffer1*が*buffer2*を超えています。|
|**_NLSCMPERROR**|エラーが発生しました。|

## <a name="remarks"></a>Remarks

Buffer1**関数は、2**つのバッファーの最初の文字*数*をバイト単位で比較します。 比較では、大文字と小文字を区別しません。

*Buffer1*または*buffer2*のいずれかが null ポインターの場合、この関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は **_NLSCMPERROR**を返し、 **errno**を**EINVAL**に設定します。

memicmp は、ロケールに依存する動作に現在のロケールを使用します **(_d)** 代わりに渡されたロケールを使用することを除いて、% **_l**は同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_memicmp**|\<memory.h> または \<string.h>|
|**_memicmp_l**|\<memory.h> または \<string.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_memicmp.c
// This program uses _memicmp to compare
// the first 29 letters of the strings named first and
// second without regard to the case of the letters.

#include <memory.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   int result;
   char first[] = "Those Who Will Not Learn from History";
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";
   // Note that the 29th character is right here ^

   printf( "Compare '%.29s' to '%.29s'\n", first, second );
   result = _memicmp( first, second, 29 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else if( result > 0 )
      printf( "First is greater than second.\n" );
}
```

```Output
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'
First is equal to second.
```

## <a name="see-also"></a>関連項目

[バッファー操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
