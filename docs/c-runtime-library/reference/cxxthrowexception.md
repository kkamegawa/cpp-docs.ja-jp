---
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: a5b614d25502ddd5a58aedcf2ec843b2b1ab9d47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942032"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

例外レコードを作成し、ランタイム環境を呼び出して例画の処理を開始します。

## <a name="syntax"></a>構文

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>パラメーター

*pExceptionObject*<br/>
例外を生成したオブジェクト。

*pThrowInfo*<br/>
例外の処理に必要な情報。

## <a name="remarks"></a>Remarks

このメソッドは、コンパイラで例外処理に使用されるコンパイラ専用ファイルに含まれています。 このメソッドはコードから直接呼び出さないでください。

## <a name="requirements"></a>必要条件

**電源**.Cpp をスローする

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
