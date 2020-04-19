---
title: toupper、_toupper、towupper、_toupper_l、_towupper_l
ms.date: 11/04/2016
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: e17f139789b2c37292764f2e4508b59cddd2c03e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957904"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper、_toupper、towupper、_toupper_l、_towupper_l

文字を大文字に変換します。

## <a name="syntax"></a>構文

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
変換する文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、可能であれば*c*のコピーを変換し、その結果を返します。

*C*がワイド文字で、 **iswlower**が0以外で、 [iswupper](isupper-isupper-l-iswupper-iswupper-l.md)が0以外の対応するワイド文字がある場合、 **towupper**は対応するワイド文字を返します。それ以外の場合、 **towupper**は*c*を変更せずに返します。

エラーを示す戻り値は予約されていません。

**Toupper**が予期した結果を得るためには、 [__ isascii](isascii-isascii-iswascii.md)と[islower](islower-iswlower-islower-l-iswlower-l.md)の両方が0以外の値を返す必要があります。

## <a name="remarks"></a>Remarks

これらの各ルーチンは、変換が可能で適切な場合に、指定した小文字を適宜大文字に変換します。 **Towupper**の大文字と小文字の変換は、ロケール固有です。 現在のロケールに関連する文字の大文字/小文字のみが変換されます。 **_L**サフィックスが付いていない関数は、現在設定されているロケールを使用します。 **_L**サフィックスを持つこれらの関数のバージョンは、ロケールをパラメーターとして受け取り、現在設定されているロケールの代わりにそれを使用します。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

**Toupper**が予期した結果を得るためには、 [__ isascii](isascii-isascii-iswascii.md)と[isupper](isupper-isupper-l-iswupper-iswupper-l.md)の両方が0以外の値を返す必要があります。

[データ変換ルーチン](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**上に移動 (_c)**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l**と **_towupper_l**はロケールに依存せず、直接呼び出すためのものではありません。 これらは、 **_totupper_l**による内部使用のために用意されています。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[to 系関数](../../c-runtime-library/to-functions.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
[to 系関数](../../c-runtime-library/to-functions.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
