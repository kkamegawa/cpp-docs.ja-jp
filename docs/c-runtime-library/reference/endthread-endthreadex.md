---
title: _endthread、_endthreadex
ms.date: 11/04/2016
api_name:
- _endthread
- _endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: c9dd4a49e534e8fa3e0f5ac735faccb4b0f65af5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937728"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

スレッドを終了します。 **_endthread**は、 **_beginthread**によって作成されたスレッドを終了し、 **_endthreadex**は **_beginthreadex**によって作成されたスレッドを終了します。

## <a name="syntax"></a>構文

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>パラメーター

*retval*<br/>
スレッド終了コード。

## <a name="remarks"></a>Remarks

**_Endthread**または **_endthreadex**を明示的に呼び出してスレッドを終了できます。ただし、 **_endthread**または **_endthreadex**は、 **_beginthread**または **_beginthreadex**にパラメーターとして渡されたルーチンからスレッドが戻ったときに、自動的に呼び出されます。 **Endthread**または **_endthreadex**を呼び出してスレッドを終了すると、スレッドに割り当てられたリソースを適切に回復することができます。

> [!NOTE]
> Libcmt.lib にリンクする実行可能ファイルでは、Win32 の [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API を呼び出さないでください。呼び出すと、割り当てられたリソースをランタイム システムで再利用することができなくなります。 **_endthread**と **_endthreadex**は、割り当てられたスレッドリソースを解放し、 **exitthread**を呼び出します。

**_endthread**は、スレッドハンドルを自動的に閉じます。 (この動作は、Win32 **Exitthread** API とは異なります)。したがって、 **_beginthread**と **_endthread**を使用する場合は、Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API を呼び出してスレッドハンドルを明示的に閉じないでください。

Win32 **exitthread** API と同様に、 **_endthreadex**はスレッドハンドルを閉じません。 したがって、 **_beginthreadex**と **_endthreadex**を使用する場合は、Win32 **CloseHandle** API を呼び出してスレッドハンドルを閉じる必要があります。

> [!NOTE]
> **_endthread**と **_endthreadex**はC++ 、スレッドで保留中のデストラクターが呼び出されない原因になります。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md) のマルチスレッド バージョンのみ。

## <a name="example"></a>例

[_beginthread](beginthread-beginthreadex.md)の例を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>
