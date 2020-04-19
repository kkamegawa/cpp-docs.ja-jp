---
title: isspace、iswspace、_isspace_l、_iswspace_l
ms.date: 11/04/2016
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: b01aaf29ff0cd3994c45433db9ff0b9f4ca7481c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953644"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace、iswspace、_isspace_l、_iswspace_l

整数が空白文字を表すかどうかを決定します。

## <a name="syntax"></a>構文

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
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

これらの各ルーチンは、 *c*が空白文字の特殊表現である場合は0以外の値を返します。 *c*が空白文字 (0x09 または 0x20) の場合、 **isspace**は0以外の値を返します。 **Isspace**関数のテスト条件の結果は、ロケールの**LC_CTYPE**カテゴリの設定によって異なります。詳細については[、「setlocale、_wsetlocale](setlocale-wsetlocale.md) 」を参照してください。 **_L**サフィックスが付いていないこれらの関数のバージョンは、ロケールに依存する動作に現在のロケールを使用します。 **_l**サフィックスが付いているバージョンは、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*c*が標準の空白文字に対応するワイド文字である場合、 **iswspace**は0以外の値を返します。

*C*が EOF でない場合、または 0 ~ 0xff の範囲内にある場合、 **isspace**と **_isspace_l**の動作は未定義です。 デバッグ CRT ライブラリが使用され、 *c*がこれらの値のいずれでもない場合、関数はアサーションを発生させます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<ctype.h> または \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
