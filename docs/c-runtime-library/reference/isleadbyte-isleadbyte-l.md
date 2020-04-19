---
title: isleadbyte、_isleadbyte_l
ms.date: 11/04/2016
api_name:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 6b853dcea82c2afea91b2e0545d253786c88ae5e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954309"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte、_isleadbyte_l

文字がマルチバイト文字の先行バイトかどうかを判定します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数。

## <a name="return-value"></a>戻り値

引数がテスト条件を満たしている場合、 **isリードバイト**は0以外の値を返します。そうでない場合は0を返します。 "C" ロケールと1バイト文字セット (SBCS) のロケールでは、 **isリードバイト**は常に0を返します。

## <a name="remarks"></a>Remarks

**Isリードバイト**マクロは、引数がマルチバイト文字の最初のバイトの場合、0以外の値を返します。 **isリードバイト**は、-1 (**EOF**) から**UCHAR_MAX** (0xff) までの任意の整数引数に対して意味のある結果を生成します。

**Isリードバイト**の予期される引数の型は**int**です。符号付き文字が渡された場合、コンパイラはそれを符号拡張によって整数に変換することで、予測できない結果が発生する可能性があります。

**_L**サフィックスが付いたこの関数のバージョンは、ロケールに依存する動作に現在のロケールではなく渡されたロケールを使用する点を除いて同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|常に false を返します|**_isleadbyte**|常に false を返します|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[バイト分類](../../c-runtime-library/byte-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_ismbb 系ルーチン](../../c-runtime-library/ismbb-routines.md)<br/>
