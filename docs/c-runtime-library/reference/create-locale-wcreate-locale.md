---
title: _create_locale、_wcreate_locale
ms.date: 11/04/2016
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 58274b63a09847fb8593247bd2777cfa19935510
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473829"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale、_wcreate_locale

ロケール オブジェクトを作成します。

## <a name="syntax"></a>構文

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>パラメーター

*category*<br/>
カテゴリ。

*locale*<br/>
ロケールの指定子。

## <a name="return-value"></a>戻り値

有効な*ロケール*と*カテゴリ*が指定されている場合、は、指定されたロケール設定を **_locale_t**オブジェクトとして返します。 プログラムの現在のロケール設定は変更されません。

## <a name="remarks"></a>コメント

**_Create_locale**関数を使用すると、特定の地域固有の設定を表すオブジェクトを作成できます。これは、多くの CRT 関数のロケール固有のバージョン ( **_l**サフィックスを持つ関数) で使用します。 動作は**setlocale**に似ていますが、指定されたロケール設定を現在の環境に適用するのではなく、設定が返される **_locale_t**構造に保存される点が異なります。 **_Locale_t**構造体は、不要になったときに[_free_locale](free-locale.md)を使用して解放する必要があります。

**_wcreate_locale**は **_create_locale**のワイド文字バージョンです。 **_wcreate_locale**する*locale*引数は、ワイド文字列です。 **_wcreate_locale**と **_create_locale**は同じように動作します。

*Category*引数は、影響を受けるロケール固有の動作の部分を指定します。 *Category*に使用されるフラグと、影響を与えるプログラムの部分は、次の表のようになります。

| *カテゴリ*フラグ | 影響 |
|-----------------|---------|
| **LC_ALL** |次に示すように、すべてのカテゴリです。 |
| **LC_COLLATE** |**Strcoll 系**、 **_stricoll**、 **wcscoll**、 **_wcsicoll**、 **strxfrm**、 **_strncoll**、 **_strnicoll**、 **_wcsncoll**、 **_wcsnicoll**、および**wcsxfrm**の各関数。 |
| **LC_CTYPE** | 文字処理関数 (影響を受けない**isdigit**、 **isxdigit**、 **mbstowcs**、および**mbtowc**を除く)。 |
| **LC_MONETARY** | **Localeconv**関数によって返される通貨書式情報。 |
| **LC_NUMERIC** | 書式設定された出力ルーチン ( **printf**など) の場合は小数点文字、データ変換ルーチンの場合は、 **localeconv**によって返される通貨以外の書式設定情報の場合は。 小数点文字に加えて、 **LC_NUMERIC**桁区切り記号と、 [localeconv](localeconv.md)によって返されるグループ化コントロール文字列を設定します。 |
| **LC_TIME** | **Strftime**関数と**wcsftime**関数。 |

この関数は、 *category*および*locale*パラメーターを検証します。 Category パラメーターが、前の表に示した値のいずれでもない場合、または*locale*が**null**の場合、関数は**null**を返します。

*Locale*引数は、ロケールを指定する文字列へのポインターです。 *Locale*引数の形式の詳細については、「[ロケール名、言語、および国/地域識別文字列](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)」を参照してください。

*Locale*引数は、ロケール名、言語文字列、言語文字列と国/地域コード、コードページ、言語文字列、国/地域コード、およびコードページを受け取ることができます。 使用できるロケール名、言語、国/地域コード、およびコードページのセットには、Windows NLS API でサポートされているものがすべて含まれています。 **_Create_locale**でサポートされているロケール名のセットについては、「[ロケール名、言語、および国/地域識別文字列](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)」を参照してください。 **_Create_locale**でサポートされている言語および国/地域識別文字列は、「[言語識別文字列](../../c-runtime-library/language-strings.md)」および「[国/地域識別文字列](../../c-runtime-library/country-region-strings.md)」に記載されています。

ロケール設定の詳細については、「[setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。

この関数の以前の名前 (2 つの先頭のアンダースコア) は非推奨とされています。 **__create_locale** 。

## <a name="requirements"></a>要件

|ルーチン|必須ヘッダー|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>参照

[ロケール名、言語、および国/地域識別文字列](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[言語識別文字列](../../c-runtime-library/language-strings.md)<br/>
[Country/Region Strings](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
