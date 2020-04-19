---
title: _fcvt
ms.date: 04/05/2018
api_name:
- _fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a90f8510e734c8459867d323eccccc75e94983d1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941326"
---
# <a name="_fcvt"></a>_fcvt

浮動小数点数を文字列に変換します。 この関数のセキュリティが強化されたバージョンについては、「[_fcvt_s](fcvt-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *_fcvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>パラメーター

*value*<br/>
変換される数値。

*count*<br/>
小数点以下の桁数。

*dec*<br/>
格納された小数点位置を指すポインター。

*sign*<br/>
格納された符号インジケーターを指すポインター。

## <a name="return-value"></a>戻り値

**fcvt**は、数字の文字列へのポインターを返します (エラーの場合は**NULL** )。

## <a name="remarks"></a>Remarks

**(_C)** 関数は、浮動小数点数を null で終わる文字列に変換します。 *値*パラメーターは、変換される浮動小数点数です。 *値*の数字を文字列として格納し、null 文字 (' \ 0 ') を追加します ( **_c** )。 *Count*パラメーターは、小数点の後に格納する桁数を指定します。 余分な数字は、*カウント*するために丸められます。 有効桁数が*カウント*よりも小さい場合は、文字列に0が埋め込まれます。

**Fcvt**によって返される合計桁数は、 **_CVTBUFSIZE**を超えることはありません。

文字列には数字だけが格納されます。 小数点の位置と*値*の符号は*dec*から取得でき、呼び出しの後に符号を付けます。 *Dec*パラメーターは整数値を指します。この整数値は、文字列の先頭に対する小数点の位置を示します。 0 または負の整数値は、小数点が文字列の先頭より左にあることを示します。 パラメーター *sign*は、*値*の符号を示す整数を指します。 Value が正で、*値*が負の場合は0以外の値に設定されて*いる場合、* 整数は0に設定されます。

この場合、 **ecvt**と**fcvt**の違いは、 *count*パラメーターの解釈です。 **ecvt**は、出力文字列の合計桁数として*count*を解釈します **。一方、** *count*は、小数点の後の桁数として解釈されます。

この変換には、静的に割り当てられた単一のバッファー**を使用し**ます **(_c** )。 これらのルーチンを呼び出すたびに、前の呼び出しの結果は破棄されます。

この関数は、パラメーターを検証します。 *Dec*または*sign*が**NULL**の場合、または*count*が0の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、 **NULL**が返されます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
