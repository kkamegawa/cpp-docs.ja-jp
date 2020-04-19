---
title: _initterm, _initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
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
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 7e85494bf6c8215d03602ee112e1ff2c0f1cf6f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954617"
---
# <a name="_initterm-_initterm_e"></a>_initterm, _initterm_e

関数ポインターのテーブルを調査して初期化する内部メソッドです。

1 番目のポインターにはテーブル内の開始位置を、2 番目のポインターには終了位置を指定します。

## <a name="syntax"></a>構文

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>戻り値

初期化に失敗した場合は 0 以外のエラーコードが返され、エラーがスローされます。エラーが発生しなかった場合は 0 が返されます。

## <a name="remarks"></a>Remarks

これらのメソッドは、C++ プログラムの初期化時にのみ内部的に呼び出されるものです。 プログラムでは呼び出さないでください。

これらのメソッドは、関数のエントリのテーブルをウォークするときに、 **NULL**エントリをスキップして続行します。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
