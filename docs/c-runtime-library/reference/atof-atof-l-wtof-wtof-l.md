---
title: atof、_atof_l、_wtof、_wtof_l
ms.date: 04/05/2018
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: a624ae9f900395ed2117ed2bb89e2768c64daba9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939566"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof、_atof_l、_wtof、_wtof_l

文字列を double 型に変換します。

## <a name="syntax"></a>構文

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>パラメーター

*str*<br/>
変換対象の文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

各関数は、入力文字を数値として解釈することによって生成される**double**値を返します。 入力をその型の値に変換できない場合、戻り値は 0.0 になります。

範囲外のすべての場合、 **errno**は**ERANGE**に設定されます。 渡されたパラメーターが**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、0を返します。

## <a name="remarks"></a>Remarks

これらの関数は文字列を倍精度浮動小数点値に変換します。

入力文字列は、指定された型の数値として解釈できる文字シーケンスです。 関数は、数値の一部として認識できない文字に最初に遭遇した時点で入力文字列の読み取りを停止します。 この文字は、文字列を終了する null 文字 ('\0' または L'\0') である場合があります。

**Atof**と **_wtof**の*str*引数の形式は次のとおりです。

[*whitespace*] [*sign*] [*digits*] [ __.__ *digits*] [ {**e** &#124; **E** }[*sign*]*digits*]

*空白*はスペースまたはタブ文字で構成され、無視されます。*sign*は正符号 (+) またはマイナス記号 (-) です。と*数字*は、1桁以上の10進数です。 小数点の前に数字がない場合は、少なくとも 1 つの数字が小数点の後に必要です。 10進数の後には指数部を指定できます。指数部は、指数部の先頭文字 (**e**または**e**) と、必要に応じて符号付き10進整数で構成されます。

これらの関数の UCRT バージョンは、Fortran スタイル (**d**または**d**) の指数文字の変換をサポートしていません。 この非標準の拡張機能は、CRT の以前のバージョンでサポートされており、コードの互換性に影響する変更点がある可能性があります。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のロケールの代わりに渡された*ロケール*パラメーターを使用する点を除いて同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|------------------|---------------------|
|**atof**、 **_l**|C: \<math.h> または \<stdlib.h> C++: \<cstdlib>、\<stdlib.h>、\<cmath> または \<math.h>|
|**_wtof**、 **_wtof_l**|C: \<stdlib.h > または \<wchar.h > C++: \<cstdlib >、\<stdlib.h > または \<wchar.h >|

## <a name="example"></a>例

このプログラムは、 **atof**関数と **_b**関数を使用して、文字列として格納されている数値を数値に変換する方法を示します。

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
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
