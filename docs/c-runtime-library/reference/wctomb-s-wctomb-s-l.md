---
title: wctomb_s、_wctomb_s_l
ms.date: 11/04/2016
api_name:
- _wctomb_s_l
- wctomb_s
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
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 329724ca0196e07397d4f0337a2bf0aa2db05c84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957892"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s、_wctomb_s_l

ワイド文字を対応するマルチバイト文字に変換します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [wctomb、_wctomb_l](wctomb-wctomb-l.md) です。

## <a name="syntax"></a>構文

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*この値*<br/>
バイト数、または結果を示すコード。

*mbchar*<br/>
マルチバイト文字のアドレス。

*sizeInBytes*<br/>
バッファー *mbchar*のサイズ。

*wchar*<br/>
ワイド文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

エラー条件

|*mbchar*|*sizeInBytes*|戻り値|*この値*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|変更されない|
|任意|>**INT_MAX**|**EINVAL**|変更されない|
|任意|小さすぎる|**EINVAL**|変更されない|

上記のいずれかのエラー条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **wctomb**は**einval**を返し、 **errno**を**einval**に設定します。

## <a name="remarks"></a>Remarks

**Wctomb_s**関数は、 *wchar*引数を対応するマルチバイト文字に変換し、その結果を*mbchar*に格納します。 任意のプログラムの任意のポイントからこの関数を呼び出すことができます。

Wctomb_s がワイド文字をマルチバイト文字に変換する場合、ワイド文字のバイト数 ( **MB_CUR_MAX**を超えることはありません) が、" " の*値*によって示される整数になります。 *Wchar*がワイド文字の null 文字 (L ' \ 0 ') の場合、 **wctomb_s**は、その*値*を1で塗りつぶします。 ターゲットポインター *mbchar*が**NULL**の場合、 **wctomb_s**は、"" の*値*に0を入れます。 現在のロケールで変換できない場合、wctomb_s は、" " の*値*に-1 を設定します。

**wctomb_s**は、ロケールに依存する情報に現在のロケールを使用します。 **_wctomb_s_l**は、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、 **wctomb**関数の動作を示しています。

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
