---
title: strcat、wcscat、_mbscat
ms.date: 11/04/2016
api_name:
- _mbscat
- wcscat
- strcat
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
ms.openlocfilehash: 973c54c18e941b29526cb3e9b1cadb98f6582c4a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958273"
---
# <a name="strcat-wcscat-_mbscat"></a>strcat、wcscat、_mbscat

文字列を追加します。 これらの関数にはセキュリティが強化されたバージョンがあります、「[strcat_s、wcscat_s、_mbscat_s](strcat-s-wcscat-s-mbscat-s.md)」をご覧ください。

> [!IMPORTANT]
> **_mbscat_s**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>パラメーター

*strDestination*<br/>
NULL で終わる追加先の文字列。

*strSource*<br/>
NULL で終わる元の文字列。

## <a name="return-value"></a>戻り値

これらの各関数は、変換先文字列 (*strdestination*) を返します。 エラーを示す戻り値は予約されていません。

## <a name="remarks"></a>Remarks

**Strcat**関数は、 *Strsource*を*strsource*に追加し、結果の文字列を null 文字で終了します。 *Strsource*の最初の文字は、 *strsource*の終端の null 文字を上書きします。 コピー元とコピー先の文字列が重なり合っている場合、 **strcat**の動作は未定義です。

> [!IMPORTANT]
> **Strcat**は*strdestination*を追加する前に、 *strdestination*に十分な領域があるかどうかを確認しないため、バッファーオーバーランの可能性があります。 代わりに [strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) の使用を検討してください。

**wcscat**と **_mbscat**は、 **strcat**のワイド文字バージョンとマルチバイト文字バージョンです。 **Wcscat**の引数と戻り値はワイド文字列です。これらの **_mbscat**はマルチバイト文字列です。 それ以外では、これらの関数の動作は同じです。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<string.h> または \<wchar.h>|
|**_mbscat**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[strcpy](strcpy-wcscpy-mbscpy.md) に関する記事の例をご覧ください。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
