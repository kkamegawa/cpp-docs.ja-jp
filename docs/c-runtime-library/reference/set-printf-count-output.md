---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948417"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

[Printf、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)の各関数で **% n**形式のサポートを有効または無効にします。

## <a name="syntax"></a>構文

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>パラメーター

*enable*<br/>
**% N**のサポートを有効にする0以外の値。 **% n**のサポートを無効にする場合は0。

## <a name="property-valuereturn-value"></a>プロパティ値/戻り値

この関数を呼び出す前の **% n**のサポートの状態: **% n**のサポートが有効になっている場合は0以外、無効になっている場合は0。

## <a name="remarks"></a>Remarks

セキュリティ上の理由から、 **printf**とそのすべてのバリエーションでは、 **% n**書式指定子のサポートは既定で無効になっています。 **Printf**形式の指定で **% n**が発生した場合、既定の動作では、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 0以外の引数を指定して **_set_printf_count_output**を呼び出すと、printf 関数[と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)に記述されているように、 **printf**関数が **% n**を解釈します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>関連項目

[_get_printf_count_output](get-printf-count-output.md)<br/>
