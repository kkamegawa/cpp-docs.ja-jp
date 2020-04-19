---
title: atoll、_atoll_l、_wtoll、_wtoll_l
ms.date: 11/04/2016
api_name:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
ms.openlocfilehash: f1b5fca9c3428bce26a8a40cf8271760fa97b10b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939475"
---
# <a name="atoll-_atoll_l-_wtoll-_wtoll_l"></a>atoll、_atoll_l、_wtoll、_wtoll_l

文字列に変換を**long** **long**整数。

## <a name="syntax"></a>構文

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
変換対象の文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

各関数を返します、**long** **long**入力文字を数字として解釈することによって生成される値。 **Atoll**の戻り値は、入力をその型の値に変換できない場合は0になります。

大きな正の整数値によるオーバーフローの場合、 **atoll**は**LLONG_MAX**を返し、負の整数値が大きいオーバーフローの場合は**LLONG_MIN**を返します。

範囲外のすべての場合、 **errno**は**ERANGE**に設定されます。 渡されたパラメーターが**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、0を返します。

## <a name="remarks"></a>Remarks

これらの関数は文字の文字列を変換、**long** **long**整数値。

入力文字列は、指定された型の数値として解釈できる文字シーケンスです。 関数は、数値の一部として認識できない文字に最初に遭遇した時点で入力文字列の読み取りを停止します。 この文字は、文字列を終了する null 文字 ('\0' または L'\0') である場合があります。

**Atoll**の*str*引数の形式は次のとおりです。

> [*空白*][*sign*][*数字*]

*空白*はスペースまたはタブ文字で構成され、無視されます。*sign*は正符号 (+) またはマイナス記号 (-) です。と*数字*は、1桁以上の数字です。

**_wtoll**は、ワイド文字列をパラメーターとして受け取る点を除いて、 **atoll**と同じです。

**_L**サフィックスが付いているこれらの関数のバージョンは、現在のロケールの代わりに渡されたロケールパラメーターを使用する点を除いて、このサフィックスが付いていないバージョンと同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**atoll**|**atoll**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|--------------|---------------------|
|**atoll**、 **_atoll_l**|\<stdlib.h>|
|**_wtoll**、 **_wtoll_l**|\<stdlib.h> または \<wchar.h>|

## <a name="example"></a>例

このプログラムは、 **atoll**関数を使用して、文字列として格納されている数値を数値に変換する方法を示しています。

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
Overflow condition occurred.
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
