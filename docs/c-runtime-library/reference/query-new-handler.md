---
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 0cbd434ee0b75f78a2492bd6239bd89f584215ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949690"
---
# <a name="_query_new_handler"></a>_query_new_handler

現在の新しいハンドラー ルーチンのアドレスを返します。

## <a name="syntax"></a>構文

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>戻り値

**_Set_new_handler**によって設定された現在の新しいハンドラールーチンのアドレスを返します。

## <a name="remarks"></a>Remarks

C++ **_Query_new_handler**関数は、 C++ [_set_new_handler](set-new-handler.md)関数によって設定された現在の例外処理関数のアドレスを返します。 **_set_new_handler**は、 **new**演算子がメモリの割り当てに失敗した場合に制御を取得する例外処理関数を指定するために使用されます。 詳細については、C++ 言語リファレンスの「[new および delete 演算子](../../cpp/new-and-delete-operators.md)」の説明をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
