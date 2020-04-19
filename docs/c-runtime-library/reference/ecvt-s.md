---
title: _ecvt_s
ms.date: 04/05/2018
api_name:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: a37508c293ee72934a8580f822878f27031b864b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624383"
---
# <a name="_ecvt_s"></a>_ecvt_s

**倍精度浮動**小数点数を文字列に変換します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_ecvt](ecvt.md) です。

## <a name="syntax"></a>構文

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー (_l)*<br/>
変換の結果である数字の文字列へのポインターが格納されます。

*サイズ (_S)*<br/>
バッファーのサイズ (バイト単位)。

*_Value*<br/>
変換される数値。

*カウント (_l)*<br/>
格納する桁数。

*Dec (_s)*<br/>
格納された小数点位置。

*署名 (_l)*<br/>
変換後の数値の符号。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。 障害が発生した場合、戻り値はエラー コードを示します。 エラー コードは、Errno.h で定義されています。 詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

パラメーターが次の表の無効な値の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、この関数は無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

### <a name="error-conditions"></a>エラー条件

|*バッファー (_l)*|*サイズ (_S)*|_Value|_Count|_Dec|_Sign|戻り値|*バッファー*内の値|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|任意|任意|任意|任意|任意|**EINVAL**|変更されません。|
|Not **NULL** (有効なメモリを指す)|<=0|任意|任意|任意|任意|**EINVAL**|変更されません。|
|任意|任意|任意|任意|**NULL**|任意|**EINVAL**|変更されません。|
|任意|任意|任意|任意|任意|**NULL**|**EINVAL**|変更されません。|

## <a name="security-issues"></a>セキュリティ上の問題

*バッファー*が有効なメモリを指しておらず、かつが**NULL**でない場合、 **ecvt_s**はアクセス違反を生成することがあります。

## <a name="remarks"></a>Remarks

関数は、浮動小数点数を文字列に変換**します。** *_Value*パラメーターは、変換される浮動小数点数です。 この関数は、最大*数*の *_Value*を文字列として格納し、null 文字 (' \ 0 ') を追加します。 *_Value*の桁数が*Count*を超えている場合は、下位の数字が丸められます。 *Count*の桁数よりも小さい場合は、文字列に0が埋め込まれます。

文字列には数字だけが格納されます。 小数点の位置と *_Value*の符号は、呼び出しの後に、 *Dec*と*sign*から取得できます。 *Dec*パラメーターは、文字列の先頭に対する小数点の位置を示す整数値をポイントします。 0 または負の整数値は、最初の桁の左側に小数点があることを示します。 *Sign*パラメーターは、変換後の数値の符号を示す整数を指します。 整数値が 0 の場合、数値は正の値です。 それ以外の場合、数値は負の値です。

長さ **_CVTBUFSIZE**のバッファーは、浮動小数点値に対して十分です。

このパラメーターの**解釈は、** *Count*パラメーターの解釈に含ま**れてい**ます。 出力文字列の合計桁数として*カウント* **を解釈する (_s** **)。一方、** 小数点の後の桁数として *カウント*を解釈します。

C++ では、テンプレートのオーバーロードによってこの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

この関数のデバッグバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

## <a name="requirements"></a>［要件］

|機能|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
