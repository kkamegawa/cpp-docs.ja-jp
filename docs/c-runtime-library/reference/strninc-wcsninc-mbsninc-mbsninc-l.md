---
title: _strninc、_wcsninc、_mbsninc、_mbsninc_l
ms.date: 11/04/2016
api_name:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
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
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
ms.openlocfilehash: b03ca4c9515bd2c70a1ce2574850e23b3add44c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947071"
---
# <a name="_strninc-_wcsninc-_mbsninc-_mbsninc_l"></a>_strninc、_wcsninc、_mbsninc、_mbsninc_l

文字列ポインターを**n**文字だけ進めます。

> [!IMPORTANT]
> **_mbsninc**と **_mbsninc_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *_strninc(
   const char *str,
   size_t count
);
wchar_t *_wcsninc(
   const wchar_t *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
ソース文字列。

*count*<br/>
文字列ポインターをインクリメントする文字数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、 *str*が*カウント*文字によってインクリメントされた後の*str*へのポインターを返します。指定されたポインターが**null**の場合は**null**になります。 *Count*が*str*の文字数以上の場合、結果は未定義になります。

## <a name="remarks"></a>Remarks

**_Mbsninc**関数は、マルチバイト文字を*カウント*することで*str*をインクリメントします。 **_mbsninc**は、現在使用中の[マルチバイトコードページ](../../c-runtime-library/code-pages.md)に従ってマルチバイト文字のシーケンスを認識します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsninc**|**_strninc**|**_mbsninc**|**_wcsninc**|

**_strninc**と **_wcsninc**は、 **_mbsninc**の1バイト文字の文字列とワイド文字列バージョンです。 **_wcsninc**と **_strninc**はこのマッピングに対してのみ提供され、それ以外の場合は使用できません。 詳細については、「[Using Generic-Text Mappings](../../c-runtime-library/using-generic-text-mappings.md)」(汎用テキスト マップの使用) および「[Generic-Text Mappings](../../c-runtime-library/generic-text-mappings.md)」(汎用テキスト マップ) をご覧ください。

**_mbsninc_l**は、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbsninc**|\<mbstring.h>|
|**_mbsninc_l**|\<mbstring.h>|
|**_strninc**|\<tchar.h>|
|**_wcsninc**|\<tchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec、_wcsdec、_mbsdec、_mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc、_wcsinc、_mbsinc、_mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
