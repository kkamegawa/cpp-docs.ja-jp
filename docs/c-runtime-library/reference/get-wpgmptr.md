---
title: _get_wpgmptr
ms.date: 11/04/2016
api_name:
- _get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 0cd2dc9c2f82d3dc49a17dc438157233c50b3261
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955570"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

**_Wpgmptr**グローバル変数の現在の値を取得します。

## <a name="syntax"></a>構文

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>パラメーター

*pValue*<br/>
**_Wpgmptr**変数の現在の値を格納する文字列へのポインター。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 *PValue*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

## <a name="remarks"></a>Remarks

プログラムに**wmain ()** や**wmain ()** などのワイドエントリポイントがある場合にのみ、 **_get_wpgmptr**を呼び出します。 **_Wpgmptr**グローバル変数には、プロセスに関連付けられている実行可能ファイルへの完全パスがワイド文字列として含まれています。 詳細については、「[_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_get_pgmptr](get-pgmptr.md)<br/>
