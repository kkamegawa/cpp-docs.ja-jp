---
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 86246ed7a32dcd2f12b38aa4148570fc5fb3b7a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949667"
---
# <a name="quick_exit"></a>quick_exit

通常のプログラムが終了するようにします。

## <a name="syntax"></a>構文

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>パラメーター

*status*<br/>
ホスト環境に戻るためのステータス コード。

## <a name="return-value"></a>戻り値

**Quick_exit**関数が呼び出し元に戻ることはできません。

## <a name="remarks"></a>Remarks

**Quick_exit**関数は、通常のプログラムの終了を引き起こします。 これは、**シグナル**関数によって登録された**atexit**、 **_onexit** 、またはシグナルハンドラーによって登録された関数を呼び出しません。 **Quick_exit**が複数回呼び出される場合、または**exit**関数も呼び出される場合、動作は定義されません。

**Quick_exit**関数は、 **at_quick_exit**によって登録された関数を、後入れ先出し (LIFO) の順序で呼び出します。ただし、関数の登録時に既に呼び出されている関数は除きます。  [longjmp](longjmp.md) 呼び出しが、関数の呼び出しを終了する登録済み関数を呼び出している間に呼び出される場合、動作は定義されません。

登録された関数が呼び出された後、 **quick_exit**は、 *status*値を使用して、ホスト環境に制御を返すために、 **_exit**を呼び出します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**quick_exit**|\<process.h> または \<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
