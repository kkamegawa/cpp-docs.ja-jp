---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 2d577bfcf0584ef982ab43ff98674d0cfadd14ba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939697"
---
# <a name="_amsg_exit"></a>_amsg_exit

指定したランタイム エラー メッセージを出力した後に、エラー コード 255 でアプリケーションを終了します。

## <a name="syntax"></a>構文

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>パラメーター

*rterrnum*<br/>
システム定義のランタイム エラー メッセージの ID 番号。

## <a name="remarks"></a>Remarks

この関数は、ランタイム エラー メッセージをコンソール アプリケーションの **stderr** に出力するか、Windows アプリケーションのメッセージ ボックスにメッセージを表示します。 デバッグ モードでは、終了する前にデバッガーを起動できます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|_amsg_exit|internal.h|