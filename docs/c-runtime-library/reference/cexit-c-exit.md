---
title: _cexit、_c_exit
ms.date: 11/04/2016
api_name:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: aa25d73bef1d85adfed77ba926e2d381e02e45e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939254"
---
# <a name="_cexit-_c_exit"></a>_cexit、_c_exit

クリーンアップ操作を実行し、プロセスを終了せずに処理を戻します。

## <a name="syntax"></a>構文

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Remarks

**_Cexit**関数は、 **atexit**および **_onexit**によって登録された関数を、後入れ先出し (LIFO) の順序で呼び出します。 **_Cexit**は、すべての i/o バッファーをフラッシュし、すべての開いているストリームを閉じてから制御を戻します。 **_c_exit**は **_exit**と同じですが、 **atexit**または **_onexit**を処理したり、ストリームバッファーをフラッシュしたりすることなく、呼び出し元のプロセスに戻ります。 次の表に、 **exit**、 **_exit**、 **_cexit**、および **_c_exit**の動作を示します。

|関数|動作|
|--------------|--------------|
|**exit**|完全な C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードで終了します。|
|**_exit**|高速な C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードで終了します。|
|**_cexit**|完全な C ライブラリの終了処理を実行し、呼び出し元に戻りますが、プロセスを終了しません。|
|**_c_exit**|高速な C ライブラリの終了処理を実行し、呼び出し元に戻りますが、プロセスを終了しません。|

**_Cexit**関数または **_c_exit**関数を呼び出すと、呼び出し時に存在する一時オブジェクトまたは自動オブジェクトのデストラクターは呼び出されません。 自動オブジェクトとは、オブジェクトが静的と宣言されていない関数内で定義されるオブジェクトです。 一時オブジェクトはコンパイラによって作成されるオブジェクトです。 **_Cexit**または **_c_exit**を呼び出す前に自動オブジェクトを破棄するには、次のように、明示的にオブジェクトのデストラクターを呼び出します。

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

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
