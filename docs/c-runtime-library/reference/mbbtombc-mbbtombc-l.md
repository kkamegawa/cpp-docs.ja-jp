---
title: _mbbtombc、_mbbtombc_l
ms.date: 11/04/2016
api_name:
- _mbbtombc_l
- _mbbtombc
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 244e603a3234b755d19a1c1d0738e8c22d74b8e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952734"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc、_mbbtombc_l

1 バイトのマルチバイト文字を、対応する 2 バイトのマルチバイト文字に変換します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
変換する 1 バイト文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_Mbbtombc**が*c*を正常に変換した場合は、マルチバイト文字を返します。それ以外の場合は、 *c*を返します。

## <a name="remarks"></a>Remarks

**_Mbbtombc**関数は、指定された1バイトのマルチバイト文字を、対応する2バイトのマルチバイト文字に変換します。 変換する文字は、0x20 ~ 0x7E または 0xA1 ~ 0xDF の範囲内である必要があります。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。詳細については[、「setlocale、_wsetlocale](setlocale-wsetlocale.md) 」を参照してください。 この関数のバージョンは同じですが、 **_mbbtombc**では、このロケールに依存する動作に現在のロケールを使用し、 **_mbbtombc_l**は渡されたロケールパラメーターを代わりに使用する点が異なります。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

以前のバージョンでは、 **_mbbtombc**には**hantozen**という名前が付けられていました。 新しいコードの場合は、 **_mbbtombc**を使用します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>
