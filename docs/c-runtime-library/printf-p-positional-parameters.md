---
title: printf_p の位置指定パラメーター
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
ms.openlocfilehash: 156baa1a91931199ebca5f6200e239aa944fee1e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944050"
---
# <a name="printf_p-positional-parameters"></a>printf_p の位置指定パラメーター

位置指定パラメータを使用すると、書式指定文字列のフィールドに代入する引数を番号で指定することができます。 次の位置指定パラメーター `printf` 関数を使用できます。

| 位置指定以外の printf 関数 | 対応する位置指定パラメーター |
|---|---|
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf、_vprintf_l、vwprintf、_vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、\__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>位置指定パラメーターの指定方法

### <a name="parameter-indexing"></a>パラメーターのインデックス作成

既定では、位置指定の書式設定がない場合、位置指定関数の動作は、位置指定でないものと同じです。 書式設定する位置指定パラメーターは、書式指定子の先頭で `%n$` を使用して指定します。ここで、`n` は、パラメーター リストでの書式設定するパラメーターの位置を示します。 パラメーターの位置を示す値は、書式指定文字列の後の最初の引数を表す 1 から始まります。 書式指定子の残りの部分には、`printf` の書式指定子と同じルールが適用されます。 書式指定子の詳細については、[「書式指定構文: printf 関数と wprintf 関数」](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) をご覧ください。

位置指定の書式設定の例を次に示します。

```C
_printf_p("%1$s %2$s", "November", "10");
```

出力は次のとおりです。

```
November 10
```

使用する数値の順序は、引数の順序と一致している必要はありません。 たとえば、次の書式指定文字列は有効です。

```C
_printf_p("%2$s %1$s", "November", "10");
```

出力は次のとおりです。

```
10 November
```

従来の書式指定文字列とは異なり、位置指定パラメーターを書式指定文字列内に複数回使用できます。 たとえば、オブジェクトに適用された

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

出力は次のとおりです。

```
10 times 10 is 100
```

書式指定文字列のどこかに、すべての引数を必ず 1 回以上使用する必要があります。 1 つの書式指定文字列で使用できる位置指定パラメータの最大数は、`_ARGMAX` で指定されます。

### <a name="width-and-precision"></a>幅と精度

`*n$` を使用して位置指定パラメーターを幅指定子または有効桁数指定子として指定できます。ここで、`n` は、パラメーター リストでの幅指定パラメーターまたは有効桁数のパラメーターの位置を示します。 幅または有効桁数の値は、\* シンボルの直後に指定する必要があります。 たとえば、オブジェクトに適用された

```C
_printf_p("%1$*2$s","Hello", 10);
```

or

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>位置指定引数とそれ以外の引数の混在

同一の書式指定文字列では、位置指定パラメーターと位置指定以外のパラメーターは混在できません。 位置指定の書式を使用する場合は、すべての書式指定子で位置指定の書式設定を使用する必要があります。 ただし、位置指定以外のパラメーターを含む書式指定文字列では、`printf_p` および関連する関数は、位置指定以外のパラメーターを引き続きサポートします。

## <a name="example"></a>例

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>関連項目

[書式指定構文: printf 関数と wprintf 関数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
