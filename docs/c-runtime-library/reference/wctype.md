---
title: wctype
ms.date: 11/04/2016
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: f77082bbcc5f3cd9d82fb40993c3ac678e7e7ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957800"
---
# <a name="wctype"></a>wctype

ワイド文字のコードの分類規則を決定します。

## <a name="syntax"></a>構文

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>パラメーター

*property*<br/>
プロパティ文字列。

## <a name="return-value"></a>戻り値

現在のロケールの**LC_CTYPE**カテゴリが、プロパティ文字列*プロパティ*と一致する名前を持つ分類規則を定義していない場合、この関数は0を返します。 それ以外の場合、[towctrans](towctrans.md) への後続の呼び出しに対する 2 番目の引数として使用するのに適した 0 以外の値を返します。

## <a name="remarks"></a>Remarks

この関数では、ワイド文字のコードの分類規則を決定します。 次の呼び出しのペアの動作はすべてのロケールで同じです (ただし、実装によって、"C" ロケールであっても追加の分類規則を定義できます)。

|関数|同等なもの|
|--------------|-------------|
|iswalnum (c)|iswctype(c, wctype( "alnum" ) )|
|iswalpha (c)|iswctype(c, wctype( "alpha" ) )|
|iswcntrl (c)|iswctype(c, wctype( "cntrl" ) )|
|iswdigit (c)|iswctype(c, wctype( "digit" ) )|
|iswgraph (c)|iswctype(c, wctype( "graph" ) )|
|iswlower (c)|iswctype(c, wctype( "lower" ) )|
|iswprint (c)|iswctype(c, wctype( "print" ) )|
|iswpunct (c)|iswctype(c, wctype( "punct" ) )|
|iswspace (c)|iswctype(c, wctype( "space" ) )|
|iswupper (c)|iswctype(c, wctype( "upper" ) )|
|iswxdigit (c)|iswctype(c, wctype( "xdigit" ) )|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
