---
title: set_terminate (CRT)
ms.date: 11/04/2016
api_name:
- set_terminate
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
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 860789a3f2fda5ef13cadffa2a00dba4fbd2090a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948368"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

**Terminate**によって呼び出される独自の終了ルーチンをインストールします。

## <a name="syntax"></a>構文

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>パラメーター

*termFunction*<br/>
作成する終了関数へのポインター。

## <a name="return-value"></a>戻り値

前の関数を後で復元できるように、 **set_terminate**によって登録された前の関数へのポインターを返します。 前の関数が設定されていない場合は、戻り値を使用して既定の動作を復元できます。この値は**NULL**でもかまいません。

## <a name="remarks"></a>Remarks

**Set_terminate**関数は、**終了**によって呼び出される関数として*termfunction*をインストールします。 **set_terminate**は例外処理C++で使用され、例外がスローされる前にプログラムの任意の時点で呼び出すことができます。 **terminate**呼び出しは、既定で[中止](abort.md)されます。 独自の終了関数を記述し、関数の名前を引数として使用して**set_terminate**を呼び出すことで、この既定値を変更できます。 **terminate** **set_terminate**の引数として指定された最後の関数を呼び出します。 必要なクリーンアップタスクを実行した後、 *Termfunction*はプログラムを終了する必要があります。 終了しない場合 (呼び出し元に戻る場合)、 [abort](abort.md)が呼び出されます。

マルチ スレッド環境では、終了関数はスレッドごとに別々に管理されます。 新しいスレッドは各々、それぞれの終了関数をインストールする必要があります。 したがって、各スレッドがそれぞれの終了処理を担当します。

**Terminate_function**型は EH で定義されています。ユーザー定義の終了関数へのポインターとしての H。 **void**を返す*termfunction*です。 カスタム関数*Termfunction*は引数を取らず、呼び出し元に戻らないようにする必要があります。 この場合、 [abort](abort.md)が呼び出されます。 *Termfunction*内から例外がスローされない可能性があります。

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate**関数は、デバッガーの外部でのみ機能します。

動的にリンクされたすべての Dll または Exe に対して1つの**set_terminate**ハンドラーがあります。**set_terminate**を呼び出す場合でも、ハンドラーは別のハンドラーに置き換えられるか、または別の DLL または EXE によって設定されたハンドラーを置き換えることができます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[terminate](terminate-crt.md) の例をご覧ください。

## <a name="see-also"></a>関連項目

[例外処理ルーチン](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
