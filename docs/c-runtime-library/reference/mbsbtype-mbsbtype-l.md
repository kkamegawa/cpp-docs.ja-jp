---
title: _mbsbtype、_mbsbtype_l
ms.date: 11/04/2016
api_name:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: c474cad9027b7914a08816346e38e954a7200bb5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952392"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype、_mbsbtype_l

文字列内のバイトの種類を返します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*mbstr*<br/>
マルチバイト文字のシーケンスのアドレス。

*count*<br/>
文字列の先頭からのバイト オフセット。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_mbsbtype**と **_mbsbtype_l**は、指定されたバイトに対するテストの結果を示す整数値を返します。 次の表のマニフェスト定数は、Mbctype.h で定義されています。

|戻り値|バイトの種類|
|------------------|---------------|
|**_MBC_SINGLE**0|1 バイト文字。 たとえば、コードページ932では、 **_mbsbtype**は、指定されたバイトが 0X20-0x7e または 0XA1-0xDF の範囲内にある場合に0を返します。|
|**_MBC_LEAD**スナップショット|マルチバイト文字の先行バイト。 たとえば、コードページ932では、指定されたバイトが 0x81 ~ 0x9F または 0xE0-0xFC の範囲内にある場合、 **_mbsbtype**は1を返します。|
|**_MBC_TRAIL**3|マルチバイト文字の後続バイト。 たとえば、コードページ932では、指定されたバイトが 0x40 ~ 0x7E または 0x80 ~ 0xFC の範囲内にある場合、 **_mbsbtype**は2を返します。|
|**_MBC_ILLEGAL**(-1)|*Mbstr*のオフセット*カウント*のバイトの前に**null**文字列、無効な文字、または null バイトが見つかりました。|

## <a name="remarks"></a>Remarks

**_Mbsbtype**関数は、マルチバイト文字列のバイトの種類を決定します。 関数は、 *mbstr*のオフセット*カウント*にあるバイトだけを調べ、指定されたバイトの前に無効な文字を無視します。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_L**サフィックスが付いていないこの関数のバージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_l**サフィックスが付いているバージョンは、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

入力文字列が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は **_MBC_ILLEGAL**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* 戻り値として使用されるマニフェスト定数の場合。

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[バイト分類](../../c-runtime-library/byte-classification.md)<br/>
