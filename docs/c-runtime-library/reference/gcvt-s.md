---
title: _gcvt_s
ms.date: 04/05/2018
api_name:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: da36641f6a3ba8dc1da0894aedbfa390d2e796ae
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625048"
---
# <a name="_gcvt_s"></a>_gcvt_s

浮動小数点値を文字列に変換します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_gcvt](gcvt.md) です。

## <a name="syntax"></a>構文

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
変換の結果を格納するバッファー。

*sizeInBytes*<br/>
バッファーのサイズ。

*value*<br/>
変換する値。

*digits*<br/>
格納されている有効桁数。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。 無効なパラメーターのためにエラーが発生した場合 (無効な値については次の表を参照)、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明するように、無効なパラメーター ハンドラーが呼び出されます。 実行を継続できる場合は、エラー コードが返されます。 エラー コードは、Errno.h で定義されています。 これらのエラーの一覧については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

### <a name="error-conditions"></a>エラー条件

|*バッファー*|*sizeInBytes*|*value*|*digits*|Return|*バッファー*内の値|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|任意|任意|任意|**EINVAL**|変更されません。|
|Not **NULL** (有効なメモリを指す)|ゼロ|任意|任意|**EINVAL**|変更されません。|
|Not **NULL** (有効なメモリを指す)|任意|任意|>= *Sizeinbytes*|**EINVAL**|変更されません。|

**セキュリティ上の問題**

*バッファー*が有効なメモリを指しておらず、かつが**NULL**でない場合、 **_gcvt_s**はアクセス違反を生成する可能性があります。

## <a name="remarks"></a>Remarks

**_Gcvt_s**関数は、浮動小数点*値*を文字列に変換します。これには、小数点と可能な符号バイトが含まれています。また、*バッファー*に文字列を格納します。 *バッファー*は、変換後の値と、自動的に追加される終端の null 文字を格納するのに十分な大きさである必要があります。 長さ **_CVTBUFSIZE**のバッファーは、任意の浮動小数点値に対して十分です。 *数字*+ 1 のバッファーサイズが使用されている場合、関数はバッファーの末尾を上書きしないため、この操作に十分なバッファーを指定してください。 **_gcvt_s**は、10進数形式で*桁*を生成しようとします。 そうでない場合は、指数形式*で数字が生成さ*れます。 後続のゼロは、変換時に非表示にできます。

C++ では、テンプレートのオーバーロードによってこの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

この関数のデバッグバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
