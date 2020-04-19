---
title: _mbbtype、_mbbtype_l
ms.date: 11/04/2016
api_name:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: ba4311921a0924d3f447feb1929a81ae1d816604
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952723"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype、_mbbtype_l

前のバイトに基づいて、バイトの種類を返します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テスト対象の文字。

*type*<br/>
テストするバイトの種類。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_mbbtype**は、文字列内のバイトの型を返します。 この決定は、コントロールのテスト条件を提供する*型*の値によって指定された、状況に依存します。 *type*は、文字列内の前のバイトの型です。 次の表のマニフェスト定数は、Mbctype.h で定義されています。

|*型*の値|**_mbbtype**のテスト|戻り値|*c*|
|---------------------|--------------------------|------------------|---------|
|1 以外の値|有効な 1 バイトまたは先頭バイト|**_MBC_SINGLE**0|1バイト (0x20-0x7E、0xA1-0xDF)|
|1 以外の値|有効な 1 バイトまたは先頭バイト|**_MBC_LEAD**スナップショット|マルチバイト文字の先頭バイト (0x81-0x9F、0xE0-0xFC)|
|1 以外の値|有効な 1 バイトまたは先頭バイト|**_MBC_ILLEGAL**<br /><br /> ( -1)|無効な文字 (0x20-0x7E、0xA1-0xDF、0x81-0x9F、0xE0-0xFC を除く)|
|1|有効な末尾バイト|**_MBC_TRAIL**3|マルチバイト文字の末尾バイト (0x40-0x7E、0x80-0xFC)|
|1|有効な末尾バイト|**_MBC_ILLEGAL**<br /><br /> ( -1)|無効な文字 (0x20-0x7E、0xA1-0xDF、0x81-0x9F、0xE0-0xFC を除く)|

## <a name="remarks"></a>Remarks

**_Mbbtype**関数は、マルチバイト文字のバイトの種類を決定します。 *Type*の値が1以外の任意の値の場合、 **_mbbtype**は、有効な1バイト文字、またはマルチバイト文字の先頭バイトをテストします。 *Type*の値が1の場合、 **_mbbtype**はマルチバイト文字の有効な末尾バイトをテストします。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。詳細については[、「setlocale、_wsetlocale](setlocale-wsetlocale.md) 」を参照してください。 この関数の **_mbbtype**バージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_mbbtype_l**バージョンは、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

以前のバージョンでは、 **_mbbtype**には**chkctype**という名前が付けられていました。 新しいコードの場合は、代わりに **_mbbtype**を使用してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 戻り値として使用されるマニフェスト定数の定義。

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[バイト分類](../../c-runtime-library/byte-classification.md)<br/>
