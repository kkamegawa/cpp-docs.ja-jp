---
title: _mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l
ms.date: 11/04/2016
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: 6bf1109cfba93042bd00acde4812706c1bbf7a01
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952586"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l

日本工業標準 (JIS: Japan Industry Standard) 文字と Japan Microsoft (JMS) 文字の間を変換します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
変換する文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

日本語のロケールで、これらの関数は変換された文字を返すか、または変換可能でない場合は 0 を返します。 日本語以外のロケールで、これらの関数は、渡された文字を返します。

## <a name="remarks"></a>Remarks

**_Mbcjistojms**関数は、日本の業界標準 (JIS) 文字を Microsoft の漢字 (シフト JIS) 文字に変換します。 この文字は、先行バイトと後続バイトの範囲が 0x21-0x7E の場合にのみ変換されます。 先行バイトまたは評価バイトがこの範囲外の場合、 **errno**は**EILSEQ**に設定されます。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

**_Mbcjmstojis**関数は、シフト jis 文字を jis 文字に変換します。 文字は、先行バイトが 0x81 ~ 0x9F または 0xE0-0xFC の範囲にあり、後続バイトが 0x40 ~ 0x7E または 0x80-0xFC の範囲内にある場合にのみ変換されます。 その範囲の一部のコード ポイントには割り当てられた文字がないため、変換できないことに注意してください。

値*c*は、変換対象の文字の先行バイトを表し、下位の8ビットが後続バイトを表す16ビット値である必要があります。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

以前のバージョンでは、 **_mbcjistojms**と **_mbcjmstojis**はそれぞれ**jistojms**と**jmstojis**と呼ばれていました。 代わりに、 **_mbcjistojms**、 **_mbcjistojms_l**、 **_mbcjmstojis** 、および **_mbcjmstojis_l**を使用する必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb 系ルーチン](../../c-runtime-library/ismbb-routines.md)<br/>
