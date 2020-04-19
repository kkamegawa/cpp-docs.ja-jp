---
title: _fpclass、_fpclassf
ms.date: 04/05/2018
api_name:
- _fpclass
- _fpclassf
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: db95453a44f6a55d4bf98638351dcda4bd8377c9
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857841"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass、_fpclassf

引数の浮動小数点の分類を示す値を返します。

## <a name="syntax"></a>構文

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
テストする浮動小数点値。

## <a name="return-value"></a>戻り値

**_Fpclass**関数と **_fpclassf**関数は、引数*x*の浮動小数点分類を示す整数値を返します。 分類には、\<float.h> で定義された次のいずれかの値が含まれる場合があります。

|Value|説明|
|-----------|-----------------|
|**_FPCLASS_SNAN**|シグナル型 NaN|
|**_FPCLASS_QNAN**|クワイエット型 NaN|
|**_FPCLASS_NINF**|負の無限大 (-INF)|
|**_FPCLASS_NN**|正規化された負の 0 以外の値|
|**_FPCLASS_ND**|正規化されない負の値|
|**_FPCLASS_NZ**|負のゼロ (-0)|
|**_FPCLASS_PZ**|正のゼロ (+0)|
|**_FPCLASS_PD**|正規化された正の値|
|**_FPCLASS_PN**|正規化された正の 0 以外の値|
|**_FPCLASS_PINF**|正の無限大 (+INF)|

## <a name="remarks"></a>Remarks

**_Fpclass**関数と **_fpclassf**関数は、Microsoft 固有の関数です。 [fpclassify](fpclassify.md) によく似ていますが、引数に関するより詳細な情報を返します。 **_Fpclassf**関数は、x64 プラットフォーム用にコンパイルされた場合にのみ使用できます。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**_fpclass**、 **_fpclassf**|\<float.h>|

互換性と適合性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>