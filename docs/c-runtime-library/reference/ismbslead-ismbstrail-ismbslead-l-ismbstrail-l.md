---
title: _ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l
ms.date: 11/04/2016
api_name:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: 71a5d2a82c01a41f945ef3fa8c7652f846f05103
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953778"
---
# <a name="_ismbslead-_ismbstrail-_ismbslead_l-_ismbstrail_l"></a>_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l

マルチバイト文字の文字列の先頭バイトと末尾バイトについて状況依存のテストを実行し、指定された部分文字列のポインターが先頭バイトまたは末尾バイトを指しているかどうかを判断します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
文字列の先頭、または直前の既知の先頭バイトを指すポインター。

*current*<br/>
テストする、文字列内の位置を指すポインター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

文字が先行バイトの場合、 **_ismbslead**は-1 を返し、 **_ismbstrail**は、文字が末尾バイトの場合は-1 を返します。 入力文字列が有効であるものの、その文字が先頭バイトでも末尾バイトでもない場合、これらの関数は 0 を返します。 どちらかの引数が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

## <a name="remarks"></a>Remarks

**_ismbslead**と **_ismbstrail**は、文字列のコンテキストを考慮に入れるため、 **_ismbblead**と **_ismbbtrail**のバージョンよりも遅くなります。

これらの関数のうち、 **_l**サフィックスが付いているバージョンは、ロケールに依存する動作の場合、現在のロケールの代わりに渡されたロケールを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<mbctype.h> または \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|
|**_ismbstrail**|\<mbctype.h> または \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|
|**_ismbslead_l**|\<mbctype.h> または \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|
|**_ismbstrail_l**|\<mbctype.h> または \<mbstring.h>|\<ctype.h>、* \<limits.h>、\<stdlib.h>|

\* テスト条件のマニフェスト定数の場合。

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 系ルーチン](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 系ルーチン](../../c-runtime-library/ismbb-routines.md)<br/>
