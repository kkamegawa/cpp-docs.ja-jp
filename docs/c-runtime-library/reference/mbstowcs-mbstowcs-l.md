---
title: mbstowcs、_mbstowcs_l
ms.date: 11/04/2016
apiname:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 18e86ce359ff3b384ff8ef7dd5977d3be8d4785f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702766"
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs、_mbstowcs_l

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

場合**mbstowcs**元の文字列を変換が正常に変換されたマルチバイト文字の数を返します。 場合、 *wcstr*引数が**NULL**、コピー先の文字列のワイド文字) の「必要なサイズを返します。 場合**mbstowcs**無効なマルチバイト文字が検出された-1 を返します。 戻り値が場合*カウント*、ワイド文字の文字列が null で終わっていません。

> [!IMPORTANT]
> いることを確認*wcstr*と*mbstr*重複しないと*数*変換するマルチバイト文字の数を正確に反映します。

## <a name="remarks"></a>Remarks

**Mbstowcs**関数はの最大数に変換*カウント*がマルチバイト文字が指す*mbstr*は対応するワイド文字の文字列に現在のロケールによって決まります。 結果として得られるワイド文字の文字列で表されるアドレスにある格納*wcstr*します。 結果は、一連の呼び出しに似ています[mbtowc](mbtowc-mbtowc-l.md)します。 場合**mbstowcs**前に、か、1 バイトの null 文字 ('\0') が発生した*カウント*null 文字をワイド文字の null 文字 (L '\0') および停止変換が発生します。 したがって、ワイド文字の文字列で*wcstr*は null 終端 null 文字が変換中に発生した場合にのみです。 によって、シーケンスを指している場合*wcstr*と*mbstr*重なっているため、の動作は未定義です。

場合、 *wcstr*引数が**NULL**、 **mbstowcs** null 終端文字を含まない、変換によって得られるワイド文字の数を返します。 正しい値を返すには、ソース文字列が null で終わっている必要があります。 結果のワイド文字列を null で終了する必要がある場合は、戻り値に 1 を追加します。

場合、 *mbstr*引数が**NULL**、または*カウント*は > **INT_MAX** 」の説明に従って、無効なパラメーターハンドラーが呼び出されます[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 Errno に設定されて実行の継続が許可された場合**EINVAL**関数は-1 を返します。

**mbstowcs**ロケールに依存する動作に現在のロケールを使用 **_mbstowcs_l**代わりに渡されたロケールを使用すると同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

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
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
