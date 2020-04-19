---
title: ispunct、iswpunct、_ispunct_l、_iswpunct_l
ms.date: 11/04/2016
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
- iswpunct
- _istpunct
- ispunct
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
ms.openlocfilehash: 54c51c612cf3b491b49d7e141df34ed5b4415520
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953703"
---
# <a name="ispunct-iswpunct-_ispunct_l-_iswpunct_l"></a>ispunct、iswpunct、_ispunct_l、_iswpunct_l

整数が区切り文字を表すかどうかを決定します。

## <a name="syntax"></a>構文

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
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

これらの各ルーチンは、 *c*が区切り文字の特殊表現である場合は0以外の値を返します。 **ispunct**は、空白文字以外の印刷可能な文字または**isalnum**が0以外の文字に対して0以外の値を返します。 **iswpunct**は、空白ワイド文字でも、 **iswalnum**が0以外のワイド文字でもない、印刷可能なワイド文字に対して0以外の値を返します。 これらの各ルーチンは、 *c*がテスト条件を満たしていない場合は0を返します。

**Ispunct**関数のテスト条件の結果は、ロケールの**LC_CTYPE**カテゴリの設定によって異なります。詳細については[、「setlocale、_wsetlocale](setlocale-wsetlocale.md) 」を参照してください。 **_L**サフィックスが付いていないこれらの関数のバージョンは、ロケールに依存する動作に現在のロケールを使用します。 **_l**サフィックスが付いているバージョンは、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*C*が EOF でない場合、または0から0xff までの範囲内にある場合、 **ispunct** **との動作は未定義**です。 デバッグ CRT ライブラリが使用され、 *c*がこれらの値のいずれでもない場合、関数はアサーションを発生させます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h> または \<wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
