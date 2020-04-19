---
title: __p__commode
ms.date: 11/04/2016
api_name:
- __p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 930eb45e8069bdd71b5a7986e229b229318d0be8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944115"
---
# <a name="__p__commode"></a>__p__commode

ファイルの入出力操作に対して既定の*ファイル コミット モード*を指定する `_commode` グローバル変数を指し示します。

## <a name="syntax"></a>構文

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>戻り値

`_commode` グローバル変数へのポインター。

## <a name="remarks"></a>解説

`__p__commode` 関数は内部使用専用であり、ユーザー コードから呼び出すことはできません。

ファイル コミット モードは重要なデータがディスクに書き込まれるタイミングを指定します。 詳細については、「[fflush](../c-runtime-library/reference/fflush.md)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|__p\__commode|internal.h|