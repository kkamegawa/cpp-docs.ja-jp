---
title: _strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l
ms.date: 11/04/2016
api_name:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
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
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
ms.openlocfilehash: 6d1645c33684f5a0fbabc2119592c39a7df97ca3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947133"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l

大文字小文字に関係なく、2 つの文字列の指定された数の文字を比較します。

> [!IMPORTANT]
> **_mbsnicmp**と **_mbsnicmp_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*string1*、 *string2*<br/>
Null で終わる比較対象の文字列。

*count*<br/>
比較する文字数

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

次のように、部分文字列間の関係を示します。

|戻り値|説明|
|------------------|-----------------|
|< 0|*string1* substring は*string2* substring より小さい値です。|
|0|*string1*部分文字列は、 *string2*部分文字列と同じです。|
|> 0|*string1* substring が*string2* substring を超えています。|

パラメーターの検証エラーが発生すると、これらの関数は **_NLSCMPERROR**と\< \<> mbstring.h > で定義されているを返します。

## <a name="remarks"></a>Remarks

**_Strnicmp**関数は、 *string1*と*string2*の最初の文字*数*のうち、最も多くを比較します。 比較は、各文字を小文字に変換することで、大文字小文字に関係なく行われます。 **_strnicmp**は、大文字と小文字を区別しない**strncmp**のバージョンです。 *カウント*文字を比較する前に、いずれかの文字列で終端の null 文字に到達すると、比較は終了します。 文字列が等しい場合、 *count*文字が比較される前にいずれかの文字列で終端の null 文字に到達すると、短い文字列の方が小さくなります。

ASCII 表の 91 から 96 の文字 ('['、'\\'、']'、'^'、'_'、および '\`') は、アルファベット文字より小さいものとして評価されます。 この順序は、 **stricmp**の順序と同じです。

**_wcsnicmp**と **_mbsnicmp**は、 **_strnicmp**のワイド文字バージョンとマルチバイト文字バージョンです。 **_Wcsnicmp**の引数はワイド文字列です。これらの **_mbsnicmp**はマルチバイト文字列です。 **_mbsnicmp**は、現在のマルチバイトコードページに従ってマルチバイト文字のシーケンスを認識し、エラーが発生した場合は **_NLSCMPERROR**を返します。 詳細については、「[コード ページ](../../c-runtime-library/code-pages.md)」をご覧ください。 それ以外では、これらの関数の動作は同じです。 これらの関数はロケール設定の影響を受けます。 **_l**サフィックスが付いていないバージョンは、ロケールに依存する動作に現在のロケールを使用します。 **_l**サフィックスが付いているバージョンでは、渡された*ロケール*が代わりに使用されます。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

これらのすべての関数では、パラメーターの検証が行われます。 *String1*または*string2*が null ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は **_NLSCMPERROR**を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strnicmp**、 **_strnicmp_l**|\<string.h>|
|**_wcsnicmp**、 **_wcsnicmp_l**|\<string.h> または \<wchar.h>|
|**_mbsnicmp**、 **_mbsnicmp_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) の例を参照してください。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
