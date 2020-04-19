---
title: __uncaught_exception
ms.date: 11/04/2016
api_name:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 0130776ec2511aefd42d1700f950d97738e9fb14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945950"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

1つ以上の例外がスローされた[が、try-catch ステートメントの](../../cpp/try-throw-and-catch-statements-cpp.md)対応する**catch**ブロックによってまだ処理されていないかどうかを示します。

## <a name="syntax"></a>構文

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>戻り値

**try** で例外がスローされてから、一致する **catch** ブロックが初期化されるまでは **true** です。 それ以外の場合は **false** です。

## <a name="remarks"></a>Remarks

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>関連項目

[try、throw、catch ステートメント (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
