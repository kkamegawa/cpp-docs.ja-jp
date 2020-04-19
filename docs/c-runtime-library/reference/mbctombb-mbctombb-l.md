---
title: _mbctombb、_mbctombb_l
ms.date: 11/04/2016
api_name:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
ms.openlocfilehash: b449dfae04f875c819f34422b9a0ae92e2b8a7c2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952527"
---
# <a name="_mbctombb-_mbctombb_l"></a>_mbctombb、_mbctombb_l

2 バイト マルチバイト文字を、対応する 1 バイト マルチバイト文字に変換します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
変換するマルチバイト文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

成功した場合、 **_mbctombb**と **_mbctombb_l**は、 *c*に対応する1バイト文字を返します。それ以外の場合は、 *c*を返します。

## <a name="remarks"></a>Remarks

**_Mbctombb**関数と **_mbctombb_l**関数は、指定されたマルチバイト文字を、対応する1バイトのマルチバイト文字に変換します。 文字は、変換対象の範囲 0x20 ~ 0x7E または0xDF 内の1バイト文字に対応する必要があります。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_L**サフィックスが付いていないこの関数のバージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_l**サフィックスが付いているバージョンは、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

以前のバージョンでは、 **_mbctombb**は**zentohan**と呼ばれていました。 代わりに **_mbctombb**を使用してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbctombb**|\<mbstring.h>|
|**_mbctombb_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc、_mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
