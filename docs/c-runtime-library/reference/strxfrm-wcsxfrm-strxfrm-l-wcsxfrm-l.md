---
title: strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
ms.date: 11/04/2016
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 411fe3a5a6f66614f0a22e0f623b73685a6e0844
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957606"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l

ロケール固有の情報に基づいて文字列を変換します。

## <a name="syntax"></a>構文

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*strDest*<br/>
対象文字列。

*strSource*<br/>
ソース文字列。

*count*<br/>
*Strdest*に挿入する最大文字数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

変換された文字列の長さを返します。終端の null 文字は含まれません。 戻り値が*count*以上の場合、 *strdest*の内容は予測できません。 エラーが発生すると、各関数は**errno**を設定し、 **INT_MAX**を返します。 無効な文字の場合、 **errno**は**EILSEQ**に設定されます。

## <a name="remarks"></a>Remarks

**Strxfrm**関数は、 *strsource*が指す文字列を、 *strsource*に格納されている新しい照合形式に変換します。 Null 文字を含む*count*文字を超える文字は変換されず、結果の文字列に格納されます。 変換は、ロケールの**LC_COLLATE** category 設定を使用して行われます。 **LC_COLLATE**の詳細については、「 [setlocale](setlocale-wsetlocale.md)」を参照してください。 **strxfrm**は、ロケールに依存する動作に現在のロケールを使用します。 **_strxfrm_l**は、現在のロケールの代わりに渡されたロケールを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

変換後、2つの変換された文字列を使用して**strcmp**を呼び出すと、元の2つの文字列に適用される**strcoll 系**への呼び出しと同じ結果が得られます。 **Strcoll 系**と**stricoll**の場合と同様に、 **strxfrm**では、マルチバイト文字列が必要に応じて自動的に処理されます。

**wcsxfrm**は、 **strxfrm**のワイド文字バージョンです。**wcsxfrm**の文字列引数はワイド文字ポインターです。 **Wcsxfrm**の場合、文字列変換の後、2つの変換された文字列を使用して**wcscmp**を呼び出すと、元の2つの文字列に適用される**wcscoll**の呼び出しと同じ結果が得られます。 それ以外では、 **wcsxfrm**と**strxfrm**は同じように動作します。 **wcsxfrm**は、ロケールに依存する動作に現在のロケールを使用します。 **_wcsxfrm_l**は、現在のロケールの代わりに渡されたロケールを使用します。

これらの関数では、パラメーターの検証が行われます。 *Strsource*が null ポインターの場合、または*Strsource*が**null**ポインターである場合 (count がゼロの場合を除く)、または*count*が**INT_MAX**より大きい場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、 **INT_MAX**を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

"C" ロケールでは、文字セット (ASCII 文字セット) 内の文字の順序は、辞書式文字順序と同じです。 ただし、その他のロケールでは、文字セット内の文字の順序が辞書式文字順序と異なる場合があります。 たとえば、特定のヨーロッパロケールでは、文字 ' a ' (値 0x61) が文字 ' &\#x00E4; ' の前に置かれます。文字セット内では (値 0xE4)、文字 ' ä ' は文字 ' a ' 辞書式の前に置かれます。

文字セットと辞書式文字順序が異なるロケールでは、元の文字列に対して**strxfrm**を使用し、結果の文字列で**strcmp**を使用して、現在のロケールに従って辞書式文字列比較を生成します。**LC_COLLATE**カテゴリ設定。 したがって、上記のロケールで辞書式2つの文字列を比較するには、元の文字列で**strxfrm**を使用し、結果の文字列で**strcmp**を使用します。 また、元の文字列で**strcmp**ではなく**strcoll 系**を使用することもできます。

**strxfrm**は、基本的に**LCMAP_SORTKEY**と[LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)のラッパーです。

次の式の値は、ソース文字列の**strxfrm**変換を保持するために必要な配列のサイズです。

`1 + strxfrm( NULL, string, 0 )`

"C" ロケールの場合のみ、 **strxfrm**は次のようになります。

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> または \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
