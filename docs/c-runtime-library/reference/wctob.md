---
title: wctob
ms.date: 11/04/2016
api_name:
- wctob
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 151325b0d66e6d57156cdf94828ca1d4b151d437
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944937"
---
# <a name="wctob"></a>wctob

ワイド文字がマルチバイト文字に対応し、そのマルチバイト文字の表現を返すかどうかを指定します。

## <a name="syntax"></a>構文

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>パラメーター

*wchar*<br/>
変換される値。

## <a name="return-value"></a>戻り値

**Wctob**がワイド文字を正常に変換した場合、マルチバイト文字が1バイト長の場合にのみ、マルチバイト文字表現が返されます。 **Wctob**がマルチバイト文字に変換できないワイド文字を検出した場合、またはマルチバイト文字が1バイト長ではない場合は、-1 を返します。

## <a name="remarks"></a>Remarks

**Wctob**関数は、マルチバイト文字が1バイト長の場合に、 *wchar*に含まれるワイド文字を、戻り値**int**値で渡される対応するマルチバイト文字に変換します。

**Wctob**が失敗し、対応するマルチバイト文字が検出されなかった場合、関数は**errno**を**EILSEQ**に設定し、-1 を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、 **wcstombs**関数の動作を示しています。

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
