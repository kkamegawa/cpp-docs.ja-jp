---
title: isupper、_isupper_l、iswupper、_iswupper_l
ms.date: 11/04/2016
api_name:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
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
- isupper
- _istupper
- iswupper
helpviewer_keywords:
- istupper function
- iswupper function
- isupper_l function
- _isupper_l function
- iswupper_l function
- _istupper function
- _iswupper_l function
- isupper function
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
ms.openlocfilehash: 558373d845b88d8959651d0a76e24af80cb6fa5e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953619"
---
# <a name="isupper-_isupper_l-iswupper-_iswupper_l"></a>isupper、_isupper_l、iswupper、_iswupper_l

整数が大文字を表すかどうかを決定します。

## <a name="syntax"></a>構文

```C
int isupper(
   int c
);
int _isupper_l (
   int c,
   _locale_t locale
);
int iswupper(
   wint_t c
);
int _iwsupper_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、 *c*が特殊文字の特殊表現である場合は0以外の値を返します。 *c*が大文字 (a-z) の場合、 **isupper**は0以外の値を返します。 **iswupper**は、 *c*が大文字に対応するワイド文字の場合、または*c*が実装定義のワイド文字セットの1つであり、 **iswcntrl**、 **iswdigit**、**およびのいずれでもない場合に、0以外の値を返します。iswpunct**、または**iswspace**が0以外である。 これらの各ルーチンは、 *c*がテスト条件を満たしていない場合は0を返します。

**_L**サフィックスが付いているこれらの関数のバージョンでは、ロケールに依存する動作に現在のロケールではなく渡されたロケールを使用します。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*C*が EOF でない場合、または 0 ~ 0xff の範囲内にある場合、 **isupper**と **_isupper_l**の動作は未定義です。 デバッグ CRT ライブラリが使用され、 *c*がこれらの値のいずれでもない場合、関数はアサーションを発生させます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**istupper (_c)**|**isupper**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswupper**|
|**_istupper_l**|**_isupper_l**|[_ismbclower、_ismbclower_l、_ismbcupper、 _ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**isupper**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**iswupper**|\<ctype.h> または \<wchar.h>|
|**_iswupper_l**|\<ctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
