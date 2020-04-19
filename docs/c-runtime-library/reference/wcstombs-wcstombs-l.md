---
title: wcstombs、_wcstombs_l
ms.date: 11/04/2016
api_name:
- wcstombs
- _wcstombs_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: e4aa09ec8e6d97762d39e63aa05b0eb0cc159d17
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945122"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs、_wcstombs_l

ワイド文字のシーケンスを、対応するマルチバイト文字のシーケンスに変換します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*mbstr*<br/>
マルチバイト文字のシーケンスのアドレス。

*wcstr*<br/>
ワイド文字のシーケンスのアドレス。

*count*<br/>
マルチバイト出力文字列に格納できる最大バイト数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**Wcstombs**がマルチバイト文字列を正常に変換した場合は、終端の null (存在する場合) を除いて、マルチバイト出力文字列に書き込まれたバイト数を返します。 *Mbstr*引数が**NULL**の場合、 **wcstombs**は、コピー先の文字列の必要なサイズをバイト単位で返します。 **Wcstombs**がマルチバイト文字に変換できないワイド文字を検出した場合、型**size_t**にキャストされた-1 を返し、 **errno**を**EILSEQ**に設定します。

## <a name="remarks"></a>Remarks

**Wcstombs**関数は、 *wcstr*が指すワイド文字列を対応するマルチバイト文字に変換し、結果を*mbstr*配列に格納します。 *Count*パラメーターは、マルチバイト出力文字列 (つまり、 *mbstr*のサイズ) に格納できる最大バイト数を示します。 通常、ワイド文字列を変換するときに必要になるバイト数は不明です。 出力文字列の 1 バイトだけを必要とするワイド文字もあれば、2 バイトを必要とする文字もあります。 入力文字列内のワイド文字ごとに、マルチバイト出力文字列に2バイト (ワイド文字の null を含む) がある場合、結果は確実に一致します。

**Wcstombs**が、 *count*の前または後に、ワイド文字の null 文字 (L ' \ 0 ') を検出すると、それを8ビットの0に変換して停止します。 このため、 *mbstr*のマルチバイト文字列は、 **wcstombs**が変換中にワイド文字の null 文字を検出した場合にのみ、null で終了します。 *Wcstr*と*mbstr*が指すシーケンスが重なり合う場合、 **wcstombs**の動作は未定義になります。

*Mbstr*引数が**NULL**の場合、 **wcstombs**は、コピー先の文字列の必要なサイズをバイト単位で返します。

**wcstombs**は、そのパラメーターを検証します。 *Wcstr*が**NULL**の場合、または*count*が**INT_MAX**より大きい場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は**errno**を**EINVAL**に設定し、-1 を返します。

**wcstombs**は、ロケールに依存する動作に現在のロケールを使用します。 **_wcstombs_l**は、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、 **wcstombs**関数の動作を示しています。

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
