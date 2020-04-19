---
title: _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
ms.date: 11/04/2016
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 4c00ae3ff845dfbc3daf4a3ea6ce5c34c43e475f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947295"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l

指定されたカウント内で文字数またはバイト数を返します。

> [!IMPORTANT]
> **_mbsnbcnt**、 **_mbsnbcnt_l**、 **_mbsnccnt**、および **_mbsnccnt_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
調査する文字列。

*count*<br/>
*Str*で調べる文字数またはバイト数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_mbsnbcnt**と **_mbsnbcnt_l**は、 *str*のマルチバイト文字の最初の*カウント*で見つかったバイト数を返します。 **_mbsnccnt**と **_mbsnccnt_l**は、 *str* *の最初のバイト数で*見つかった文字数を返します。 *Str*の検査が完了する前に null 文字が検出されると、null 文字の前に見つかったバイト数または文字数が返されます。 *Str*が*カウント*文字またはバイト数未満で構成されている場合は、文字列の文字数またはバイト数を返します。 *Count*が0未満の場合は、0を返します。 以前のバージョンでは、これらの関数には**size_t**ではなく**int**型の戻り値がありました。

**_strncnt**は、1バイトの文字列*str*の*最初のバイト数の*文字数を返します。 **_wcsncnt**は、ワイド文字の文字列*str*の*最初の文字数の*文字数を返します。

## <a name="remarks"></a>Remarks

**_mbsnbcnt**と **_mbsnbcnt_l**は、 *str*のマルチバイト文字の最初の*カウント*で見つかったバイト数をカウントします。 **_mbsnbcnt**と **_mbsnbcnt_l**は **、mtob を置換し**、 **mtob**の代わりに使用する必要があります。

**_mbsnccnt**と **_mbsnccnt_l**は、 *str* *の最初のバイト数で*見つかった文字数をカウントします。 **_Mbsnccnt**と **_mbsnccnt_l**が2バイト文字の2番目のバイトで null 文字を検出した場合、最初のバイトも null と見なされ、返されたカウント値には含まれません。 **_mbsnccnt**と **_mbsnccnt_l**は **、btom の**代わりに使用する必要が**あります。**

*Str*が**NULL**ポインターまたは*count*が0の場合、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 **errno**は**EINVAL**に設定され、関数は0を返します。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|ルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|N/A|
|**_wcsncnt**|N/A|N/A|**_mbsnbcnt**|
|**_wcsncnt**|N/A|N/A|**_mbsnccnt**|
|N/A|N/A|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Output

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
