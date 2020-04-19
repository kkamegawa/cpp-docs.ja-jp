---
title: _atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l
ms.date: 04/05/2018
api_name:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
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
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
ms.openlocfilehash: 3f3b164042006cab22d0dfd9a7968e2d2e494f5c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943624"
---
# <a name="_atodbl-_atodbl_l-_atoldbl-_atoldbl_l-_atoflt-_atoflt_l"></a>_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l

文字列を double ( **_atodbl**)、long double ( **_b**)、または float ( **_b**) に変換します。

## <a name="syntax"></a>構文

```C
int _atodbl( _CRT_DOUBLE * value, char * str );
int _atodbl_l ( _CRT_DOUBLE * value, char * str, locale_t locale );
int _atoldbl( _LDOUBLE * value, char * str );
int _atoldbl_l ( _LDOUBLE * value, char * str, locale_t locale );
int _atoflt( _CRT_FLOAT * value, const char * str );
int _atoflt_l( _CRT_FLOAT * value, const char * str, locale_t locale );
```

### <a name="parameters"></a>パラメーター

*value*<br/>
文字列を浮動小数点値に変換することで生成される double 型、long double 型、または float 型の値。 これらの値は構造体でラップされます。

*str*<br/>
浮動小数点値に変換するために解析する文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

処理が正常に終了した場合は 0 を返します。 考えられるエラーコードは、ヘッダーファイル\<の math. h > で定義されている**アンダーフロー**またはオーバーフローです (_s)

## <a name="remarks"></a>Remarks

これらの関数は、文字列を浮動小数点値に変換します。 これらの関数と**atof**ファミリの関数の違いは、これらの関数は浮動小数点コードを生成せず、ハードウェア例外を発生させないことです。 代わりに、エラー状態がエラー コードとして報告されます。

文字列に浮動小数点値として有効な解釈がない場合、*値*は0に設定され、戻り値は0になります。

**_L**サフィックスが付いているこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡された*ロケール*パラメーターを使用する点を除いて、サフィックスが付いていないバージョンと同じです。

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|
|--------------|---------------------|
|**_atodbl**、( **_e**)、 **atoflt**<br /><br /> _atoflt_l、 **_atodbl_l**、|\<stdlib.h>|

## <a name="example"></a>例

```C
// crt_atodbl.c
// Uses _atodbl to convert a string to a double precision
// floating point value.

#include <stdlib.h>
#include <stdio.h>

int main()
{
   char str1[256] = "3.141592654";
   char abc[256] = "abc";
   char oflow[256] = "1.0E+5000";
   _CRT_DOUBLE dblval;
   _CRT_FLOAT fltval;
   int retval;

   retval = _atodbl(&dblval, str1);

   printf("Double value: %lf\n", dblval.x);
   printf("Return value: %d\n\n", retval);

   retval = _atoflt(&fltval, str1);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // A non-floating point value: returns 0.
   retval = _atoflt(&fltval, abc);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // Overflow.
   retval = _atoflt(&fltval, oflow);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   return 0;
}
```

```Output
Double value: 3.141593
Return value: 0

Float value: 3.141593
Return value: 0

Float value: 0.000000
Return value: 0

Float value: inf
Return value: 3
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
