---
title: mbstowcs、_mbstowcs_l
ms.date: 11/04/2016
api_name:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 3df851b08edfa9dfe5bf9b42b9abfd45a8939606
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952033"
---
# <a name="mbstowcs-_mbstowcs_l"></a>mbstowcs、_mbstowcs_l

マルチバイト文字のシーケンスを、対応するワイド文字のシーケンスに変換します。 これらの関数のセキュリティを強化したバージョンについては、「[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*wcstr*<br/>
ワイド文字のシーケンスのアドレス。

*mbstr*<br/>
null で終了するマルチバイト文字のシーケンスのアドレス。

*count*<br/>
変換するマルチバイト文字の最大数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**Mbstowcs**がソース文字列を正常に変換した場合は、変換されたマルチバイト文字の数を返します。 *Wcstr*引数が**NULL**の場合、関数は、変換先文字列の必要なサイズ (ワイド文字) を返します。 **Mbstowcs**で無効なマルチバイト文字が検出されると、-1 が返されます。 戻り値が*count*の場合、ワイド文字の文字列は null で終了しません。

> [!IMPORTANT]
> *Wcstr*と*mbstr*が重複しないようにし、その*カウント*に変換するマルチバイト文字数が正しく反映されていることを確認します。

## <a name="remarks"></a>Remarks

**Mbstowcs**関数は、 *mbstr*が指すマルチバイト文字の*最大数を*、現在のロケールによって決定される対応するワイド文字の文字列に変換します。 結果のワイド文字列は、 *wcstr*によって表されるアドレスに格納されます。 結果は、 [mbtowc](mbtowc-mbtowc-l.md)の一連の呼び出しに似ています。 **Mbstowcs**が1バイトの null 文字 (' \ 0 ') を検出する前または*カウント*が発生した場合は、null 文字をワイド文字の null 文字 (L ' \ 0 ') に変換して停止します。 したがって、 *wcstr*のワイド文字文字列は、変換中に null 文字が検出された場合にのみ null で終了します。 *Wcstr*と*mbstr*が指すシーケンスが重なっている場合、動作は未定義です。

*Wcstr*引数が**null**の場合、 **mbstowcs**は、null 終端文字を含まない、変換によって生成されるワイド文字数を返します。 正しい値を返すには、ソース文字列が null で終わっている必要があります。 結果のワイド文字列を null で終了する必要がある場合は、戻り値に 1 を追加します。

*Mbstr*引数が**NULL**の場合、または*count*が**INT_MAX**> 場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、errno は**EINVAL**に設定され、この関数は-1 を返します。

**mbstowcs**は、ロケールに依存する動作に現在のロケールを使用します。 **_mbstowcs_l**は、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
