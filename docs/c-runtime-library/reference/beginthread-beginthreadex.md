---
title: _beginthread、_beginthreadex
ms.date: 02/27/2018
api_name:
- _beginthread
- _beginthreadex
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
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: 8714e945464dd98483f9347c4226321a96cda61c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943639"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread、_beginthreadex

スレッドを作成します。

## <a name="syntax"></a>構文

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>パラメーター

*start_address*<br/>
新しいスレッドの実行を開始するルーチンの開始アドレス。 **_Beginthread**の場合、呼び出し規約は、 [__cdecl](../../cpp/cdecl.md) (ネイティブコードの場合) または[__clrcall](../../cpp/clrcall.md) (マネージコードの場合) のいずれかになります。 **_beginthreadex**の場合は、 [__stdcall](../../cpp/stdcall.md) (ネイティブコードの場合) または[__clrcall](../../cpp/clrcall.md) (マネージコードの場合) のいずれかになります。

*stack_size*<br/>
新しいスレッドのスタック サイズまたは 0。

*arglist*<br/>
新しいスレッドに渡される引数リストまたは**NULL**。

*Security*<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 構造体へのポインター。この構造体は、返されたハンドルを子プロセスが継承できるかどうかを決定します。 *セキュリティ*が**NULL**の場合、ハンドルを継承することはできません。 Windows 95 アプリケーションの場合は**NULL**にする必要があります。

*initflag*<br/>
新しいスレッドの初期状態を制御するフラグ。 *Initflag*を0に設定して直ちに実行するか、 **CREATE_SUSPENDED**に設定して、中断状態のスレッドを作成します。[ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread)を使用してスレッドを実行します。 *Initflag*を**STACK_SIZE_PARAM_IS_A_RESERVATION**フラグに設定して、スタックの初期予約サイズとして*STACK_SIZE*を使用します (バイト単位)。このフラグが指定されていない場合、 *stack_size*はコミットサイズを指定します。

*thrdaddr*<br/>
スレッド識別子を受け取る 32 ビット変数へのポインター。 **NULL**の場合は使用されません。

## <a name="return-value"></a>戻り値

成功した場合、これらの各関数は、新しく作成されたスレッドへのハンドルを返します。ただし、新しく作成されたスレッドが短時間で終了した場合、 **_beginthread**は有効なハンドルを返さない可能性があります。 (「解説」の説明を参照)。エラーが発生した場合、 **_beginthread**は-1l を返し、スレッドの数が多すぎる場合は**errno**が**EAGAIN**に設定され、引数が無効であるかスタックサイズが正しくない場合は**EINVAL** 、またはリソースが不足している場合は**EACCES**になります。(メモリなど)。 エラーが発生した場合、 **_beginthreadex**は0を返し、 **errno**と **_doserrno**が設定されます。

*Start_address*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、-1 を返します。

これらのリターン コードとその他のリターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

**Uintptr_t**の詳細については、「[標準型](../../c-runtime-library/standard-types.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Beginthread**関数は、 *start_address*でルーチンの実行を開始するスレッドを作成します。 *Start_address*のルーチンは、 **__cdecl** (ネイティブコードの場合) または **__clrcall** (マネージコードの場合) の呼び出し規約を使用する必要があり、戻り値を持つことはできません。 スレッドは、ルーチンから戻ると自動的に終了します。 スレッドの詳細については、「[旧形式のコードのためのマルチスレッド サポート (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)」を参照してください。

**_beginthreadex**は、 **_beginthread**よりもはるかに近い Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API に似ています。 **_beginthreadex**は、次の点で **_beginthread**とは異なります。

- **_beginthreadex**には、 *initflag*、 *Security*、 **threadaddr**という3つのパラメーターが追加されています。 新しいスレッドは、指定されたセキュリティを使用して中断状態で作成でき、スレッド識別子である*thrdaddr*を使用してアクセスできます。

- **_Beginthreadex**に渡される*start_address*のルーチンは、 **__stdcall** (ネイティブコードの場合) または **__clrcall** (マネージコードの場合) の呼び出し規約を使用する必要があり、スレッドの終了コードを返す必要があります。

- **_beginthreadex**は、エラーが発生した場合に-1l ではなく0を返します。

- **_Beginthreadex**を使用して作成されたスレッドは、 [_endthreadex](endthread-endthreadex.md)への呼び出しによって終了されます。

**_Beginthreadex**関数を使用すると、 **_beginthread**よりもスレッドの作成方法をより細かく制御できます。 **_Endthreadex**関数もより柔軟です。 たとえば、 **_beginthreadex**では、セキュリティ情報の使用、スレッドの初期状態 (実行中または一時停止) の設定、新しく作成されたスレッドのスレッド識別子の取得を行うことができます。 **_Beginthreadex**によって返されたスレッドハンドルを同期 api と共に使用することもできます。この場合、 **_beginthread**を使用することはできません。

**_Beginthread**より **_beginthreadex**を使用する方が安全です。 **_Beginthread**によって生成されるスレッドがすぐに終了する場合は、 **_beginthread**の呼び出し元に返されるハンドルが無効であるか、別のスレッドを指している可能性があります。 ただし、 **_beginthreadex**によって返されるハンドルは **_beginthreadex**の呼び出し元によって閉じられる必要があるため、 **_beginthreadex**がエラーを返さない場合は、有効なハンドルであることが保証されます。

[_Endthread](endthread-endthreadex.md)または **_endthreadex**を明示的に呼び出してスレッドを終了できます。ただし、 **_endthread**または **_endthreadex**は、パラメーターとして渡されるルーチンからスレッドが戻ると自動的に呼び出されます。 **_Endthread**または **_endthreadex**を呼び出してスレッドを終了すると、スレッドに割り当てられているリソースを正しく回復できます。

**_endthread**はスレッドハンドルを自動的に閉じるのに対し、 **_endthreadex**は自動的に終了しません。 したがって、 **_beginthread**と **_endthread**を使用する場合は、Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API を呼び出してスレッドハンドルを明示的に閉じないでください。 この動作は、Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API とは異なります。

> [!NOTE]
> Libcmt.lib にリンクされている実行可能ファイルの場合、Win32 **Exitthread** API を呼び出さないでください。これにより、割り当てられたリソースをランタイムシステムで再利用できなくなります。 **_endthread**と **_endthreadex**は、割り当てられたスレッドリソースを解放し、 **exitthread**を呼び出します。

**_Beginthread**または **_beginthreadex**が呼び出されると、オペレーティングシステムはスタックの割り当てを処理します。スレッドスタックのアドレスをこれらの関数のいずれかに渡す必要はありません。 また、 *stack_size*引数は0にすることができます。この場合、オペレーティングシステムはメインスレッドに指定されているスタックと同じ値を使用します。

*arglist*は、新しく作成されたスレッドに渡すパラメーターです。 通常、文字列などのデータ項目のアドレスを指定します。 *arglist*は、不要な場合は**NULL**にすることができますが、 **_beginthread**と **_beginthreadex**には、新しいスレッドに渡す値を指定する必要があります。 いずれかのスレッドが[abort](abort.md)、 **exit**、 **_exit**、または**ExitProcess**を呼び出すと、すべてのスレッドが終了します。

新しいスレッドのロケールは、プロセスごとのグローバル現在のロケール情報を使用して初期化されます。 スレッドごとのロケールが (グローバルまたは新しいスレッドに対してのみ) [configthreadlocale](configthreadlocale.md)の呼び出しによって有効にされている場合、スレッドは**setlocale**または **_wsetlocale**を呼び出すことによって、他のスレッドとは別にロケールを変更できます。 スレッドごとのロケールフラグが設定されていないスレッドは、スレッドごとのロケールフラグが設定されていない他のすべてのスレッドのロケール情報や、新しく作成されたすべてのスレッドのロケール情報に影響を与える可能性があります。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

**/Clr**コードの場合、 **_beginthread**と **_beginthreadex**にはそれぞれ2つのオーバーロードがあります。 一方はネイティブの呼び出し規約関数ポインターを受け取り、もう1つは **__clrcall**関数ポインターを受け取ります。 最初のオーバーロードは、アプリケーション ドメインセーフではなく、以降もそうなることはありません。 **/Clr**コードを記述する場合は、新しいスレッドがマネージリソースにアクセスする前に正しいアプリケーションドメインに入るようにする必要があります。 そのためには、[call_in_appdomain 関数](../../dotnet/call-in-appdomain-function.md)などを使用します。 2番目のオーバーロードは、アプリケーションドメインセーフです。新しく作成されたスレッドは、常に **_beginthread**または **_beginthreadex**の呼び出し元のアプリケーションドメインで終了します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md) のマルチスレッド バージョンのみ。

**_Beginthread**または **_beginthreadex**を使用するには、アプリケーションをマルチスレッドの C ランタイムライブラリの1つにリンクする必要があります。

## <a name="example"></a>例

次の例では、 **_beginthread**と **_endthread**を使用します。

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

任意のキーを押してサンプル アプリケーションを終了します。

## <a name="example"></a>例

次のサンプルコードは、 **_beginthreadex**から返されたスレッドハンドルを同期 API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)と共に使用する方法を示しています。 メイン スレッドは、2 番目のスレッドが終了するのを待って処理を継続します。 2番目のスレッドが **_endthreadex**を呼び出すと、そのスレッドオブジェクトがシグナル状態になります。 これにより、1 番目のスレッドの実行が継続されます。 これは **_beginthread**および **_endthread**では実行できません。 **_endthread**は**CloseHandle**を呼び出します。これにより、スレッドオブジェクトがシグナル状態に設定される前に破棄されます。

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>関連項目

- [プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)
- [_endthread、_endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit、_Exit、_exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
