---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: b67abb58f4d62c7c54b61d1b1699f09c1bd51b40
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957314"
---
# <a name="_set_output_format"></a>_set_output_format

書式付き I/O 関数で使用する出力形式をカスタマイズします。

> [!IMPORTANT]
>  これは古い関数です。 Visual Studio 2015 以降、CRT で使用できません。

## <a name="syntax"></a>構文

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>パラメーター

*format*<br/>
[in] 使用する書式を表す値。

## <a name="return-value"></a>戻り値

以前の出力形式。

## <a name="remarks"></a>解説

`_set_output_format` は、[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) などの書式付き I/O 関数の出力を構成する場合に使用します。 現時点では、この関数で変更できる書式設定規則は、浮動小数点数の出力の指数部に表示される桁数のみです。

既定では、 `printf_s`、 `wprintf_s`、およびそれに関連する Visual C++ 標準ライブラリ関数によって出力される浮動小数点数の指数部は、指数部の値を表すために 3 桁が必要でない場合でも、3 桁で出力されます。 値が 3 桁になるように 0 が埋め込まれます。 `_set_output_format` を使用すると、指数部の大きさによって 3 桁目が必要になる場合を除いて、浮動小数点数の指数部が 2 桁のみで出力されるように動作を変更できます。

2 桁の指数部を有効にするには、次の例に示されているとおり、パラメーター `_TWO_DIGIT_EXPONENT`を指定してこの関数を呼び出します。 2 桁の指数部を無効にするには、引数 0 を指定してこの関数を呼び出します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

互換性の詳細については、「C ランタイム ライブラリ」の「 [互換性](../c-runtime-library/compatibility.md) 」を参照してください。

## <a name="example"></a>例

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>関連項目

[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
