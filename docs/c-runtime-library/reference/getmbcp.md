---
title: _getmbcp
ms.date: 11/04/2016
api_name:
- _getmbcp
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
- _getmbcp
- getmbcp
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
ms.openlocfilehash: 0fb7ee6686de5d1c9d1df0efa7fb6b619aef0d7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955025"
---
# <a name="_getmbcp"></a>_getmbcp

現在のコード ページを取得します。

## <a name="syntax"></a>構文

```C
int _getmbcp( void );
```

## <a name="return-value"></a>戻り値

現在のマルチバイト コード ページを返します。 戻り値 0 は、シングル バイトのコード ページが使用中であることを示します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getmbcp**|\<mbctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_setmbcp](setmbcp.md)<br/>
