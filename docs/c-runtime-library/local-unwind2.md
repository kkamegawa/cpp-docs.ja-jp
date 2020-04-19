---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: 64ed92af32caaf579e7c6951250e3bf692d1cf43
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944206"
---
# <a name="_local_unwind2"></a>_local_unwind2

内部 CRT 関数。 指定されたスコープ テーブルに示されているすべての終了ハンドラーを実行します。

## <a name="syntax"></a>構文

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>パラメーター

*xr*<br/>
[in] 1 つのスコープ テーブルに関連付けられている登録レコード。

*stop*<br/>
[in] `_local_unwind2` の停止箇所を示す構文レベル。

## <a name="remarks"></a>解説

このメソッドは、ランタイム環境によってのみ使用されます。 このメソッドをコードで呼び出さないでください。

このメソッドが終了ハンドラーを実行する場合、現在の構文レベルで開始し、`stop` で示されたレベルに到達するまで構文レベル内を上へ移動します。 `stop` で示されたレベルでは終了ハンドラーを実行しません。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
