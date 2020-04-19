---
title: 'スレッド ローカル ストレージ (TLS: Thread Local Storage)'
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 7e308f7ba23503879f8ebbcacde481cf72055229
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510395"
---
# <a name="thread-local-storage-tls"></a>スレッド ローカル ストレージ (TLS: Thread Local Storage)

スレッド ローカル ストレージ (TLS) は、指定されたマルチスレッド プロセスの各スレッドが、スレッド固有のデータを格納する場所を割り当てるための手段です。 動的にバインドされた (実行時) スレッド固有のデータは、TLS API ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)) によってサポートされます。 Win32 と Microsoft C++コンパイラは、既存の API 実装に加えて、スレッドごとの静的なデータバインド (読み込み時) をサポートするようになりました。

## <a name="_core_compiler_implementation_for_tls"></a>TLS のコンパイラ実装

**C++ 11:** `thread_local`ストレージクラス指定子は、オブジェクトおよびクラスメンバーのスレッドローカルストレージを指定するために推奨される方法です。 詳細については、「[ストレージC++クラス」 ()](../cpp/storage-classes-cpp.md)を参照してください。

MSVC は、拡張ストレージクラス修飾子として、Microsoft 固有の属性である[thread](../cpp/thread.md)も提供します。 **__Declspec**キーワードを使用して、**スレッド**変数を宣言します。 たとえば、次に示すコードは、整数型のスレッド ローカル変数を宣言して特定の値に初期化します。

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>規則と制約

静的にバインドされるスレッド ローカル オブジェクトと変数を宣言する場合は、次のガイドラインに従ってください。 これらのガイドラインは、 [thread](../cpp/thread.md)と[thread_local](../cpp/storage-classes-cpp.md)の両方に適用されます。

- **Thread**属性は、クラスおよびデータの宣言と定義にのみ適用できます。 関数の宣言または定義では使用できません。 たとえば、次のコードはコンパイラ エラーになります。

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- **Thread**修飾子は、**静的**なエクステントを持つデータ項目に対してのみ指定できます。 これには、グローバルデータオブジェクト (**静的**および**extern**の両方)、ローカルの静的オブジェクト、およびC++クラスの静的データメンバーが含まれます。 自動データオブジェクトは、 **thread**属性を使用して宣言することはできません。 次のコードはコンパイラ エラーになります。

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- スレッドローカルオブジェクトの宣言と定義では、すべて**スレッド**属性を指定する必要があります。 たとえば、次のコードはエラーになります。

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **Thread**属性を型修飾子として使用することはできません。 たとえば、次のコードはコンパイラ エラーになります。

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Thread 属性を使用C++するオブジェクトの宣言は許可されているため、次の2つの例は同じ意味になります。

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- スレッドローカルオブジェクトのアドレスは定数とは見なされず、そのようなアドレスを含む式は定数式とは見なされません。 標準 C では、オブジェクトまたはポインターの初期化子としてスレッドローカル変数のアドレスを使用できないようになります。 たとえば、次のコードは、C コンパイラによってエラーとしてフラグが設定されています。

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   この制限は、にC++は適用されません。 C++ ではすべてのオブジェクトを動的に初期化することが許可されているため、スレッド ローカル変数のアドレスを使用する式を使用してオブジェクトを初期化できます。 これは、スレッドローカルオブジェクトの構築と同様に行われます。 たとえば、前に示したコードは、 C++ソースファイルとしてコンパイルされるときにエラーを生成しません。 スレッドローカル変数のアドレスは、アドレスが取得されたスレッドが存在する場合に限り有効です。

- 標準 C では、オブジェクトまたは変数を、それ自体への参照を含む式で初期化することができますが、非静的エクステントのオブジェクトに対してのみ使用できます。 C++一般に、このようなオブジェクトの動的な初期化は、それ自体への参照を含む式で行うことができますが、この種の初期化はスレッドローカルオブジェクトでは許可されていません。 例えば:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   初期`sizeof`化されるオブジェクトを含む式は、それ自体への参照を表しておらず、C C++との両方で有効になっています。

   C++では、スレッドのローカルストレージ機能が将来拡張される可能性があるため、このようなスレッドデータの動的な初期化は許可されません。

- Windows Vista より前の windows オペレーティングシステム`__declspec( thread )`では、にいくつかの制限があります。 DLL が任意のデータまたはオブジェクトを`__declspec( thread )`として宣言すると、動的に読み込まれた場合、保護エラーが発生する可能性があります。 DLL に[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)が読み込まれると、コードがデータを`__declspec( thread )`参照するたびにシステムエラーが発生します。 スレッドのグローバル変数領域は実行時に割り当てられるため、この領域のサイズは、アプリケーションの要件および静的にリンクされているすべての DLL の要件に基づいて計算されます。 を使用`LoadLibrary`する場合、この領域を拡張して、で`__declspec( thread )`宣言されたスレッドローカル変数を許可することはできません。 Dll がによっ`LoadLibrary`て読み込まれる可能性がある場合は、 [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)などの tls api を使用して、tls を割り当てます。

## <a name="see-also"></a>関連項目

[C と Win32 を使用するマルチスレッド](multithreading-with-c-and-win32.md)
