---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 232bf7bc518907db8744fbb85e0f3a33c9296006
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625850"
---
# <a name="signal"></a>signal

割り込みシグナル処理を設定します。

> [!IMPORTANT]
> テストシナリオまたはデバッグシナリオを除き、このメソッドを使用して Microsoft Store アプリをシャットダウンしないでください。 プログラムまたは UI がストアアプリを閉じる方法は、 [Microsoft Store ポリシー](/legal/windows/agreements/store-policies)によっては許可されていません。 詳細については、「 [UWP アプリのライフサイクル](/windows/uwp/launch-resume/app-lifecycle)」を参照してください。

## <a name="syntax"></a>構文

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>パラメーター

*sig*<br/>
シグナル値。

*func*<br/>
2番目のパラメーターは、実行する関数へのポインターです。 最初のパラメーターはシグナル値で、2 番目のパラメーターは、最初のパラメーターが SIGFPE のときに使用できるサブコードです。

## <a name="return-value"></a>戻り値

**signal**は、指定されたシグナルに関連付けられている func の前の値を返します。 たとえば、 *func*の前の値が**SIG_IGN**の場合、戻り値も**SIG_IGN**になります。 **SIG_ERR**の戻り値はエラーを示します。その場合、 **errno**は**EINVAL**に設定されます。

リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**Signal**関数を使用すると、プロセスで、オペレーティングシステムからの割り込みシグナルを処理する複数の方法のいずれかを選択できます。 *Sig*引数は、**シグナル**が応答する割り込みです。SIGNAL で定義されている次のマニフェスト定数のいずれかである必要があります。始め.

|*sig*値|説明|
|-----------------|-----------------|
|**SIGABRT**|異常終了|
|**SIGFPE**|浮動小数点エラー|
|**SIGILL**|無効な命令|
|**SIGINT**|Ctrl + C シグナル|
|**SIGSEGV**|ストレージへの無効なアクセス|
|**SIGTERM**|終了要求|

*Sig*が上記の値のいずれでもない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で定義されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、 **SIG_ERR**を返します。

既定では、**シグナル**は、 *sig*の値に関係なく、終了コード3で呼び出し元のプログラムを終了します。

> [!NOTE]
> **SIGINT**は、どの Win32 アプリケーションでもサポートされていません。 Ctrl + C 割り込みが発生すると、Win32 オペレーティング システムは、その割り込みを処理する専用の新しいスレッドを生成します。 これにより、UNIX のアプリケーションなどのシングル スレッド アプリケーションがマルチスレッドになり、予期しない動作が発生する可能性があります。

*Func*引数は、記述するシグナルハンドラーのアドレス、または signal でも定義されている定義済みの定数**SIG_DFL**または**SIG_IGN**のいずれかになります。始め. *Func*が関数の場合は、指定されたシグナルのシグナルハンドラーとしてインストールされます。 シグナルハンドラーのプロトタイプには、 **int**型の1つの仮引数*sig*が必要です。割り込みが発生すると、オペレーティングシステムは*sig*を使用して実際の引数を提供します。引数は、割り込みを生成したシグナルです。 したがって、シグナル ハンドラーで (前の表の) 6 つのマニフェスト定数を使用して、発生した割り込みを特定し、適切なアクションを実行できます。 たとえば、 **signal**を2回呼び出して同じハンドラーを2つの異なるシグナルに割り当て、受信したシグナルに基づいて異なるアクションを実行するためにハンドラーの*sig*引数をテストすることができます。

浮動小数点例外 (**SIGFPE**) をテストする場合、 *FUNC*は、FLOAT で定義されているいくつかのマニフェスト定数の1つである省略可能な2番目の引数を受け取る関数を指します。H 形式の**FPE_xxx**です。 **SIGFPE**シグナルが発生した場合、2番目の引数の値をテストして、浮動小数点例外の種類を特定し、適切なアクションを実行できます。 この引数とその有効な値は Microsoft 拡張機能です。

浮動小数点例外の場合、シグナルの受信時に*func*の値はリセットされません。 浮動小数点例外から回復するには、try/except 句で浮動小数点演算を囲みます。 [setjmp](setjmp.md) と [longjmp](longjmp.md) を使用して回復することもできます。 いずれの場合も、呼び出し元プロセスは実行を再開し、プロセスの浮動小数点状態を未定義のままにします。

シグナル ハンドラーが戻った場合、呼び出し元プロセスは、割り込みシグナルを受け取った位置の直後から実行を再開します。 この動作は、どの種類のシグナルまたは動作モードにも当てはまります。

指定された関数が実行される前に、 *func*の値が**SIG_DFL**に設定されます。 **シグナル**の介在する呼び出しで特に指定されていない限り、次の割り込みシグナルは**SIG_DFL**の説明として扱われます。 この機能を使用して、呼び出された関数でシグナルをリセットできます。

シグナル ハンドラー ルーチンは、通常、割り込みの発生時に非同期的に呼び出されるので、実行時の操作が未完了で、不明な状態の場合は、シグナル ハンドラー関数が制御を取得することがあります。 次の一覧に、シグナル ハンドラー ルーチンで使用できる関数が決まる制限事項について説明します。

- 低レベルまたは STDIO を発行しないでください。H i/o ルーチン ( **printf**や**fread**など)。

- ヒープルーチンや、ヒープルーチンを使用するルーチン ( **malloc**、 **_strdup**、 **_putenv**など) を呼び出さないでください。 詳細については、「[malloc](malloc.md)」を参照してください。

- システムコールを生成する関数 ( **_getcwd**や**time**など) は使用しないでください。

- 割り込みが浮動小数点例外 (つまり、 *sig*は**SIGFPE**) に起因する場合を除き、 **longjmp**は使用しないでください。 この場合は、最初に **_fpreset**の呼び出しを使用して、浮動小数点パッケージを再初期化します。

- オーバーレイ ルーチンを使用しない。

関数を使用して**SIGFPE**例外をトラップする場合は、プログラムに浮動小数点コードを含める必要があります。 プログラムに浮動小数点コードがなく、ランタイム ライブラリのシグナル処理コードが必要な場合は、次のように volatile double を宣言して、ゼロに初期化します。

```C
volatile double d = 0.0f;
```

Windows では、 **Sigill**信号とシグナルは生成されません。 これは、ANSI との互換性を維持するために用意されています。 そのため、 **signal**を使用してこれらのシグナルのシグナルハンドラーを設定できます。また、 [raise](raise.md)を呼び出すことによって、これらのシグナルを明示的に生成することもできます。

[_Exec](../../c-runtime-library/exec-wexec-functions.md)関数または[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)関数の呼び出しによって作成されたプロセスでは、シグナル設定が保持されません。 シグナル設定は、新しいプロセスでは既定値にリセットされます。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**signal**|\<signal.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

次の例では、 **signal**を使用して、 **sigabrt**シグナルにカスタム動作を追加する方法を示します。 中止動作の詳細については、「[_set_abort_behavior](set-abort-behavior.md)」を参照してください。

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

出力は、使用されているランタイムのバージョン、アプリがコンソールまたは Windows アプリであるかどうか、および Windows レジストリ設定によって異なります。 コンソールアプリの場合、次のようなメッセージが stderr に送信される可能性があります。

```Output
Debug Error!

Program: c:\Projects\crt_signal\Debug\crt_signal.exe

R6010

- abort() has been called
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec、_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
