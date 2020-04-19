---
title: isascii、__isascii、iswascii
ms.date: 11/04/2016
api_name:
- iswascii
- __isascii
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
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: b7677819a4b138b08ed4ff97de38c091ce0e94fd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857789"
---
# <a name="isascii-__isascii-iswascii"></a>isascii、__isascii、iswascii

特定の文字が ASCII 文字かどうかを判断します。

## <a name="syntax"></a>構文

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、 **c**が ASCII 文字の特殊表現である場合は0以外の値を返します。 **c**が ASCII 文字 (0X00 から0x7f の範囲内) の場合、 **__isascii**は0以外の値を返します。 **c**が ASCII 文字のワイド文字表現である場合、 **iswascii**は0以外の値を返します。 これらの各ルーチンは、 **c**がテスト条件を満たしていない場合は0を返します。

## <a name="remarks"></a>Remarks

プリプロセッサマクロ _CTYPE_DISABLE_MACROS が定義されていない場合、 **__isascii**と**iswascii**の両方がマクロとして実装されます。

旧バージョンとの互換性を保つために、 **isascii**は[ &#95; &#95;、&#95; STDC](../../preprocessor/predefined-macros.md)が定義されていない場合、または0として定義されている場合にのみ、マクロとして実装それ以外の場合は未定義です。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**isascii**、 **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> または \<ctype.h>|
|**iswascii**|C: \<wctype.h>、\<ctype.h>、または \<wchar.h><br /><br /> C++: \<cwctype>、\<cctype>、\<wctype.h>、\<ctype.h>、または \<wchar.h>|

**Isascii**、 **__isascii**および**iswascii**の各関数は、Microsoft 固有の関数です。 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
