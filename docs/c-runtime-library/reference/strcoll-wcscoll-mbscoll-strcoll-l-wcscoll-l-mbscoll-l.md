---
title: strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l
ms.date: 11/04/2016
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 7519b8f41d77ed668bb7da1e8ced18ee13c0a5bf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957888"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l

現在のロケールまたは指定された LC_COLLATE 変換状態カテゴリを使用して、文字列を比較します。

> [!IMPORTANT]
> **_mbscoll**と **_mbscoll_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*string1*、 *string2*<br/>
Null で終わる比較対象の文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各関数は、次のように、 *string1*と*string2*の関係を示す値を返します。

|戻り値|string1 と string2 との関係|
|------------------|----------------------------------------|
|< 0|*string1*が*string2*未満|
|0|*string1*と*string2*の同一|
|> 0|*string1*が*string2*より大きい|

これらの各関数は、エラーが発生したときに **_NLSCMPERROR**を返します。 **_NLSCMPERROR**を使用するには、いずれかの文字列を指定します。H または MBSTRING.H。始め. *string1*または*string2*が**NULL**の場合、または照合シーケンスのドメイン外のワイド文字コードが含まれている場合、 **wcscoll**は失敗する可能性があります。 エラーが発生すると、 **wcscoll**は**errno**を**EINVAL**に設定することがあります。 **Wcscoll**の呼び出しでエラーが発生していないかどうかを確認するには、 **errno**を0に設定し、 **wcscoll**を呼び出した後に**errno**を確認します。

## <a name="remarks"></a>Remarks

これらの各関数は、現在使用中のコードページに従って、 *string1*と*string2*の大文字と小文字を区別した比較を実行します。 これらの関数は、現在のコード ページの文字セット順序と辞書式文字順序との間に相違点があり、この違いが文字列比較に関係がある場合にのみ使用します。

これらのすべての関数では、パラメーターの検証が行われます。 *String1*または*string2*が null ポインターの場合、または*count*が**INT_MAX**より大きい場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は **_NLSCMPERROR**を返し、 **errno**を**EINVAL**に設定します。

各ロケールには文字を並べ替えるための異なる規則があるため、2 つの文字列の比較は、ロケールに依存する操作となります。 **_L**サフィックスが付いていないこれらの関数のバージョンは、このロケールに依存する動作に現在のスレッドのロケールを使用します。 **_l**サフィックスが付いているバージョンは、現在のロケールの代わりにパラメーターとして渡されたロケールを使用することを除いて、サフィックスが付いていない対応する関数と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>、\<string.h>|
|**_mbscoll**、 **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>、\<string.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ロケール](../../c-runtime-library/locale.md)<br/>
[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
