---
title: _ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
ms.date: 11/04/2016
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 6a64a0d9be83733fa5482eee84ce6576dd32c221
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953791"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l

マルチバイト文字が小文字または大文字であるかどうかをチェックします。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする文字。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各ルーチンでは、文字がテスト条件を満たす場合に 0 以外の値が返され、テスト条件を満たさない場合に 0 が返されます。 *C*< = 255 で、対応する **_ismbb**ルーチンが存在する場合 (たとえば、 **_ismbcalnum**が **_ismbbalnum**に対応している場合)、結果は対応する **_ismbb**ルーチンの戻り値になります。

## <a name="remarks"></a>Remarks

これらの各関数は特定の条件で特定のマルチバイト文字をテストします。

**_L**サフィックスを持つこれらの関数のバージョンは、ロケールに依存する動作に現在のロケールではなく渡されたロケールを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

|ルーチン|テスト条件|コード ページ 932 の例|
|-------------|--------------------|---------------------------|
|**_ismbclower**|小文字の英字|*C*が ASCII 小文字の英文字の1バイト表現である場合に限り、0以外の値を返します。0x61 < =*c*< = 0x7a.|
|**_ismbclower_l**|小文字の英字|*C*が ASCII 小文字の英文字の1バイト表現である場合に限り、0以外の値を返します。0x61 < =*c*< = 0x7a.|
|**_ismbcupper**|大文字の英字|*C*が ASCII 大文字の英文字の1バイト表現である場合にのみ、0以外の値を返します。0x41 < =*c*< = 0x5a。|
|**_ismbcupper_l**|大文字の英字|*C*が ASCII 大文字の英文字の1バイト表現である場合にのみ、0以外の値を返します。0x41 < =*c*< = 0x5a。|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 系ルーチン](../../c-runtime-library/ismbc-routines.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 系ルーチン](../../c-runtime-library/ismbb-routines.md)<br/>
