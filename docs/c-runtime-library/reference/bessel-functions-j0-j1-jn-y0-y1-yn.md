---
title: 'Bessel 系関数: _j0、_j1、_jn、_y0、_y1、_yn'
ms.date: 04/05/2018
api_name:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 5420b34846998cdbcb4814d8319274f1a3516d91
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939459"
---
# <a name="bessel-functions-_j0-_j1-_jn-_y0-_y1-_yn"></a>Bessel 系関数: _j0、_j1、_jn、_y0、_y1、_yn

0、1、または n の順序の、最初または 2 番目の種類の Bessel 関数を計算します。 Bessel 系関数は電磁波理論の数学でよく使用されます。

## <a name="syntax"></a>構文

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

*n*<br/>
Bessel 系関数の整数順序。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、値が*x*のベッセル関数を返します。 *X*が**負の値**に設定さ**れている**場合、このルーチン**は** **errno**を**EDOM**に設定し、 **_DOMAIN**エラーメッセージを**stderr**に出力して、 **_HUGE_VAL**を返します。 **_Matherr**を使用して、エラー処理を変更できます。

## <a name="remarks"></a>Remarks

**J0**、 **j1**、および **_** の各ルーチンは、最初の種類のベッセル関数を返します: orders 0、1、および n。

|入力|SEH 例外|Matherr 例外|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|**無効です**|**_DOMAIN**|

**1 番** **目のルーチンでは、** 2 番目の種類のベッセル関数 (orders 0、1、 **n) が**返されます。

|入力|SEH 例外|Matherr 例外|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|**無効です**|**_DOMAIN**|
|± 0|**ゼロ除算**|**通知 (_R)**|
|&#124;x&#124; < 0.0|**無効です**|**_DOMAIN**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**j0**、 **j1** **、_、&** **y0**、_ **y1** **、(** _d)|\<cmath> (C++), \<math.h> (C, C++)|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>
