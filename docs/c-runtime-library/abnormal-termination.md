---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944708"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

システムが終了ハンドラーの内部リストの実行中に、[try-finally ステートメント](../cpp/try-finally-statement.md)の `__finally` ブロックが入力されているかどうかを示します。

## <a name="syntax"></a>構文

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>戻り値

**true** システムがスタックを*アンワインド*する場合は、それ以外は **false** です。

## <a name="remarks"></a>解説

これは、アンワインドの例外を管理するために使用される内部関数で、ユーザー コードから呼び出されるものではありません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>関連項目

[try-finally ステートメント](../cpp/try-finally-statement.md)
