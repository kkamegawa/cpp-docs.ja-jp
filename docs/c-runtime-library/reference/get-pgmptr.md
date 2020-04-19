---
title: _get_pgmptr
ms.date: 11/04/2016
api_name:
- _get_pgmptr
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
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: 4f9a3b19cc7eb1870b87ec46b7923987ec646e32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955764"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

**_Pgmptr**グローバル変数の現在の値を取得します。

## <a name="syntax"></a>構文

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>パラメーター

*pValue*<br/>
**_Pgmptr**変数の現在の値を格納する文字列へのポインター。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 *PValue*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

## <a name="remarks"></a>Remarks

**Main ()** または**WinMain ()** のように、プログラムに狭いエントリポイントがある場合にのみ、 **_get_pgmptr**を呼び出します。 **_Pgmptr**グローバル変数には、プロセスに関連付けられている実行可能ファイルへの完全パスが含まれています。 詳細については、「[_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[_get_wpgmptr](get-wpgmptr.md)<br/>
