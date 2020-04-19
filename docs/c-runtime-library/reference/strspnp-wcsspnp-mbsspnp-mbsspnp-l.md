---
title: _strspnp、_wcsspnp、_mbsspnp、_mbsspnp_l
ms.date: 11/04/2016
api_name:
- _mbsspnp
- _wcsspnp
- _mbsspnp_l
- _strspnp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsspnp
- _mbsspnp
- strspnp
- _ftcsspnp
- _mbsspnp_l
- wcsspnp
- mbsspnp_l
- _wcsspnp
- _strspnp
- mbsspnp
helpviewer_keywords:
- _strspnp function
- _wcsspnp function
- _mbsspnp_l function
- strspnp function
- mbsspnp function
- wcsspnp function
- _mbsspnp function
- mbsspnp_l function
- _tcsspnp function
- tcsspnp function
ms.assetid: 1ce18100-2edd-4c3b-af8b-53f204d80233
ms.openlocfilehash: af80f4970e5aad4355b0287c901f130809cc4f79
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946679"
---
# <a name="_strspnp-_wcsspnp-_mbsspnp-_mbsspnp_l"></a>_strspnp、_wcsspnp、_mbsspnp、_mbsspnp_l

指定した一方の文字列の文字のうち、もう一方の文字列にはない最初の文字へのポインターを返します。

> [!IMPORTANT]
> **_mbsspnp**と **_mbsspnp_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *_strspnp(
   const char *str,
   const char *charset
);
wchar_t *_wcsspnp(
   const unsigned wchar_t *str,
   const unsigned wchar_t *charset
);
unsigned char *_mbsspnp(
   const unsigned char *str,
   const unsigned char *charset
);
unsigned char *_mbsspnp_l(
   const unsigned char *str,
   const unsigned char *charset,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
NULL で終わる検索対象の文字列。

*集合*<br/>
NULL で終わる文字セット。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_strspnp**、 **_wcsspnp**、および **_mbsspnp**は、 *charset* *内の*文字セットに属さない最初の文字へのポインターを返します。 これらの各関数は、 *str*が*charset*からのすべての文字で構成されている場合、 **NULL**を返します。 これらのルーチンでは、エラーを示す戻り値は予約されていません。

## <a name="remarks"></a>Remarks

**_Mbsspnp**関数は、 *charset*の文字セットに属さない、 *str*の最初の文字であるマルチバイト文字へのポインターを返します。 **_mbsspnp**は、現在使用中の[マルチバイトコードページ](../../c-runtime-library/code-pages.md)に従ってマルチバイト文字のシーケンスを認識します。 検索には、終端の NULL 文字は含まれません。

*Str*または*charset*が null ポインターの場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsspnp**|**_strspnp**|**_mbsspnp**|**_wcsspnp**|

**_strspnp**と **_wcsspnp**は、 **_mbsspnp**の1バイト文字とワイド文字バージョンです。 **_strspnp**と **_wcsspnp**は、それ以外の場合は **_mbsspnp**と同じように動作します。これらは、このマッピングに対してのみ提供され、その他の理由では使用できません。 詳細については、「[Using Generic-Text Mappings](../../c-runtime-library/using-generic-text-mappings.md)」(汎用テキスト マップの使用) および「[Generic-Text Mappings](../../c-runtime-library/generic-text-mappings.md)」(汎用テキスト マップ) をご覧ください。

**_mbsspnp_l**は、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbsspnp**|\<mbstring.h>|
|**_strspnp**|\<tchar.h>|
|**_wcsspnp**|\<tchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_mbsspnp.c
#include <mbstring.h>
#include <stdio.h>

int main( void ) {
   const unsigned char string1[] = "cabbage";
   const unsigned char string2[] = "c";
   unsigned char *ptr = 0;
   ptr = _mbsspnp( string1, string2 );
   printf( "%s\n", ptr);
}
```

### <a name="output"></a>Output

```Output
abbage
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
