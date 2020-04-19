---
title: _seh_filter_dll、_seh_filter_exe
ms.date: 11/04/2016
api_name:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
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
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
ms.openlocfilehash: c8c76a4a1d1a39e26f5e78869d3b107578d2085a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948692"
---
# <a name="_seh_filter_dll-_seh_filter_exe"></a>_seh_filter_dll、_seh_filter_exe

例外と実行する関連アクションを指定します。

## <a name="syntax"></a>構文

```C
int __cdecl _seh_filter_dll(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
int __cdecl _seh_filter_exe(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
```

### <a name="parameters"></a>パラメーター

*Exceptionnum (_d)*<br/>
例外の識別子。

*Exceptionptr (_d)*<br/>
例外情報へのポインター。

## <a name="return-value"></a>戻り値

例外処理の結果に基づいて実行するアクションを示す整数。

## <a name="remarks"></a>Remarks

次のメソッドが [try-except Statement](../../cpp/try-except-statement.md) の例外フィルター式によって呼び出されます。 このメソッドは、次に示すように、例外を特定して適切なアクションを決定するために定数内部テーブルを調べます。 例外番号は winnt.h で定義され、シグナル番号は signal.h で定義されます。

|例外番号 (unsigned long)|シグナル番号|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE|
|STATUS_FLOAT_OVERFLOW|SIGFPE|
|STATUS_FLOAT_STACK_CHECK|SIGFPE|
|STATUS_FLOAT_UNDERFLOW|SIGFPE|

## <a name="requirements"></a>必要条件

**ヘッダー:** corecrt_startup.h

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
