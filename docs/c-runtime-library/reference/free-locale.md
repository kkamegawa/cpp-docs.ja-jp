---
title: _free_locale
ms.date: 11/04/2016
api_name:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 31a8e3191c5e370acb00aaf12e21f0c712c51dd1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956757"
---
# <a name="_free_locale"></a>_free_locale

ロケール オブジェクトを解放します。

## <a name="syntax"></a>構文

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*locale*<br/>
解放するロケール オブジェクト。

## <a name="remarks"></a>Remarks

**_Free_locale**関数は、 **_get_current_locale**または**locale**の呼び出しから取得したロケールオブジェクトを解放するために使用されます。

この関数の以前の**名前 (2 つの先頭**のアンダースコア) は非推奨とされました。

## <a name="requirements"></a>必要条件

|**ルーチン**|必須ヘッダー|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
