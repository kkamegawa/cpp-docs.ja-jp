---
title: unexpected (CRT)
ms.date: 11/04/2016
api_name:
- unexpected
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
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 796f5ddbf8467656b5430de1d504f162d891864d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957818"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

**Set_unexpected**を使用して、指定した**終了**または関数を呼び出します。

## <a name="syntax"></a>構文

```C
void unexpected( void );
```

## <a name="remarks"></a>Remarks

**予期**しないルーチンは、現在の例外処理のC++実装では使用されません。 既定では、**予期しない**呼び出しは**終了**します。 この既定の動作を変更するには、カスタムの終了関数を作成し、引数として関数の名前を指定して**set_unexpected**を呼び出します。 **予期しない**呼び出し**set_unexpected**の引数として渡された最後の関数。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[例外処理ルーチン](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
