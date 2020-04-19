---
title: マルチスレッドとロケール
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: c12a3fa1922db7a1ec0a7bcd43ddf09000d97961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213252"
---
# <a name="multithreading-and-locales"></a>マルチスレッドとロケール

C ランタイム ライブラリと C++ 標準ライブラリの両方、プログラムのロケールの変更のサポートを提供します。 このトピックでは、マルチ スレッド アプリケーションで両方のライブラリのロケール機能を使用するときに発生する問題について説明します。

## <a name="remarks"></a>Remarks

使用してマルチ スレッド アプリケーションを作成すると、C ランタイム ライブラリ、`_beginthread`と`_beginthreadex`関数。 このトピックでは、これらの関数を使用して作成されたマルチ スレッド アプリケーションのみを説明します。 詳細については、次を参照してください。 [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)します。

C ランタイム ライブラリを使用してロケールを変更するには、使用、 [setlocale](../preprocessor/setlocale.md)関数。 以前のバージョンの Visual C では、この関数は常に、アプリケーション全体のロケールを変更していました。 これは、スレッドごとに、ロケールを設定するようになりました。 これを使用して、 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)関数。 指定する[setlocale](../preprocessor/setlocale.md)のみ呼び出し、現在のスレッドのロケールを変更する必要があります`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`そのスレッドでします。 逆に、呼び出す`_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)`と、そのスレッドでは、グローバル ロケールを使用してすべての呼び出しに[setlocale](../preprocessor/setlocale.md)ことで、スレッドはスレッドごとのロケールを明示的に有効にしていないすべてのスレッドのロケールを変更します。

C++ ランタイム ライブラリを使用してロケールを変更するには、使用、 [locale クラス](../standard-library/locale-class.md)します。 呼び出すことによって、 [locale::global](../standard-library/locale-class.md#global)メソッドが明示的に有効になっていないスレッドごとのロケールのすべてのスレッドのロケールを変更します。 1 つのスレッドまたはアプリケーションの部分でロケールを変更するのインスタンスを作成、`locale`スレッドまたはコードの一部のオブジェクト。

> [!NOTE]
> 呼び出す[locale::global](../standard-library/locale-class.md#global) C++ 標準ライブラリと C ランタイム ライブラリの両方のロケールを変更します。 ただし、呼び出す[setlocale](../preprocessor/setlocale.md)のみ、C ランタイム ライブラリは、C++ 標準ライブラリが影響を受けませんのロケールを変更します。

次の例を使用する方法を示して、 [setlocale](../preprocessor/setlocale.md)関数の場合、 [locale クラス](../standard-library/locale-class.md)、および[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)関数内のアプリケーションのロケールを変更するにはさまざまなシナリオをいくつか。

## <a name="example"></a>例

この例では、メイン スレッドは、2 つの子スレッドを生成します。 最初のスレッドでは、スレッド A、により呼び出すことによって、スレッドごとのロケール`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`します。 2 番目のスレッド、スレッド B は、ほか、メイン スレッドは、スレッドごとのロケールを有効にしないでください。 スレッド a がロケールを使用して、変更に進みます、 [setlocale](../preprocessor/setlocale.md) C ランタイム ライブラリの関数。

スレッド A は、スレッドごとのロケールに有効にすると、「フランス」ロケールを使用して、スレッド A スタートでは、C ランタイム ライブラリ関数のみを持っています。 メイン スレッドでスレッド B および C ランタイム ライブラリ関数は、"C"ロケールを使用し続けます。 また、 [setlocale](../preprocessor/setlocale.md) C++ 標準ライブラリのロケール オブジェクトを"C"ロケールを使用して、引き続きすべての C++ 標準ライブラリには影響しません。

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>例

この例では、メイン スレッドは、2 つの子スレッドを生成します。 最初のスレッドでは、スレッド A、により呼び出すことによって、スレッドごとのロケール`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`します。 2 番目のスレッド、スレッド B は、ほか、メイン スレッドは、スレッドごとのロケールを有効にしないでください。 スレッド a がロケールを使用して、変更に進みます、 [locale::global](../standard-library/locale-class.md#global) C++ 標準ライブラリのメソッド。

スレッド A は、スレッドごとのロケールに有効にすると、「フランス」ロケールを使用して、スレッド A スタートでは、C ランタイム ライブラリ関数のみを持っています。 メイン スレッドでスレッド B および C ランタイム ライブラリ関数は、"C"ロケールを使用し続けます。 ただし、以降、 [locale::global](../standard-library/locale-class.md#global)メソッドが「グローバル」、ロケールを変更、すべてのスレッド内のすべての C++ 標準ライブラリ オブジェクトは、「フランス」ロケールの使用を開始します。

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example"></a>例

この例では、メイン スレッドは、2 つの子スレッドを生成します。 最初のスレッドでは、スレッド A、により呼び出すことによって、スレッドごとのロケール`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`します。 2 番目のスレッド、スレッド B は、ほか、メイン スレッドは、スレッドごとのロケールを有効にしないでください。 次を使用して、ロケールにスレッド B、 [setlocale](../preprocessor/setlocale.md) C ランタイム ライブラリの関数。

スレッド B が有効になっているスレッドごとのロケールがあるないため「フランス」ロケールを使用してメイン スレッドでスレッド B および C ランタイム ライブラリ関数を開始します。 スレッド A があるスレッドごとのロケールを有効になっているために、"C"ロケールを使用するスレッド A 続行で C ランタイム ライブラリ関数。 また、 [setlocale](../preprocessor/setlocale.md) C++ 標準ライブラリのロケール オブジェクトを"C"ロケールを使用して、引き続きすべての C++ 標準ライブラリには影響しません。

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>例

この例では、メイン スレッドは、2 つの子スレッドを生成します。 最初のスレッドでは、スレッド A、により呼び出すことによって、スレッドごとのロケール`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`します。 2 番目のスレッド、スレッド B は、ほか、メイン スレッドは、スレッドごとのロケールを有効にしないでください。 次を使用して、ロケールにスレッド B、 [locale::global](../standard-library/locale-class.md#global) C++ 標準ライブラリのメソッド。

スレッド B が有効になっているスレッドごとのロケールがあるないため「フランス」ロケールを使用してメイン スレッドでスレッド B および C ランタイム ライブラリ関数を開始します。 スレッド A があるスレッドごとのロケールを有効になっているために、"C"ロケールを使用するスレッド A 続行で C ランタイム ライブラリ関数。 ただし、以降、 [locale::global](../standard-library/locale-class.md#global)メソッドが「グローバル」、ロケールを変更、すべてのスレッド内のすべての C++ 標準ライブラリ オブジェクトは、「フランス」ロケールの使用を開始します。

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>関連項目

[旧形式のコードのためのマルチスレッド サポート (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[国際化](../c-runtime-library/internationalization.md)<br/>
[ロケール](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale クラス](../standard-library/locale-class.md)
