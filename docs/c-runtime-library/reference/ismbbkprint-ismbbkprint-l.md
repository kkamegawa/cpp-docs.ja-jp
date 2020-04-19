---
title: _ismbbkprint、_ismbbkprint_l
ms.date: 11/04/2016
api_name:
- _ismbbkprint
- _ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
ms.openlocfilehash: e2417718d7cb90e8032cfe9dad903d6610dc6ae7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954112"
---
# <a name="_ismbbkprint-_ismbbkprint_l"></a>_ismbbkprint、_ismbbkprint_l

特定のマルチバイト文字が区切り記号かどうかを判定します。

## <a name="syntax"></a>構文

```C
int _ismbbkprint(
   unsigned int c
);
int _ismbbkprint_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

整数*c*が非 ascii テキストまたは非 ascii 区切り記号の場合、 **_ismbbkprint**は0以外の値を返します。それ以外の場合は0を返します。 たとえば、コードページ932でのみ、 **_ismbbkprint**はカタカナの英数字またはカタカナの句読点 (範囲:0xA1 - 0xDF) をテストします。 **_ismbbkprint**は、ロケールに依存する文字設定に現在のロケールを使用します。 **_ismbbkprint_l**は、渡されたロケールを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_ismbbkprint**|\<mbctype.h>|
|**_ismbbkprint_l**|\<mbctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[バイト分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 系ルーチン](../../c-runtime-library/ismbb-routines.md)<br/>
